# <center> UniAudio: Towards Universal Audio Generation with Large Language Models </center>

<center> Dongchao Yang*<sup>1</sup>, Jinchuan Tian*<sup>2</sup>, Xu Tan <sup>3</sup>, Rongjie Huang <sup>4</sup>, Songxiang Liu, HaoHan Guo<sup>1</sup>,  Xuankai Chang<sup>2</sup>, Jiatong Shi <sup>2</sup>, Sheng Zhao <sup>3</sup>, Jiang Bian <sup>3</sup>, Zhou Zhao <sup>4</sup>, Xixin Wu <sup>1</sup>, Helen Meng<sup>1</sup> </center> 
 
<center> * Equal Contribution </center>
<center> 1 Chinese University of Hong Kong </center>
<center> 2 Carnegie Mellon University</center>
<center> 3 Microsoft Research Asia</center>
<center> 4 Zhejiang University</center>


## Introduction
Audio generation is a major branch of generative AI research. Compared with prior works in this area that are commonly task-specific with heavy domain knowledge, this paper advocates building universal audio generation models that can handle various tasks in a unified manner.
As recent research on large language models (LLMs) has demonstrated their strong ability to handle multiple tasks, this work presents UniAudio, an LLM-based audio generation model that supports a wide range of audio generation tasks.
Based on various input conditions, such as phoneme, text description, or audio itself, UniAudio can generate speech, sound, music, and singing voice. 
The proposed UniAudio is built with 100k hours of multi-source open-available audio data and is scaled to 1B parameters. The audio tokenization method and language model architecture are also specifically designed for both performance and efficiency. Experimentally, UniAuido supports 11 audio generation tasks and achieves competitive results on all tasks consistently. We also show that UniAudio can support new tasks seamlessly via simple fine-tuning.

## Overview
The overview of UniAudio as following picture shows.
![The overview of UniAudio](fig/over.png)
In the following, we will show some generated samples by our proposed method. 

<style>
.audio-player {
  width: 200px;
}
.audio-player2 {
  width: 150px;
}
</style>

## Zero-shot TTS.
In the following, we first show some case in LibriTTS test clean set. 

| <center>  Content (The transcirption of the target audio) </center> | <center> Prompt </center> | <center> Generated Speech </center>| <center> GT Speech </center>|
| -----------------------     |  -----------   | ------ | ----- |-------|
| IT IS SIXTEEN YEARS SINCE JOHN BERGSON DIED    | <audio class="audio-player2" src="zero_shot_tts/ref/tts_237-126133-0024.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gen/tts_237-134493-0000.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gt/tts_237-134493-0000.wav" controls preload></audio> |
| IF A LAYMAN IN GIVING BAPTISM POUR THE WATER BEFORE SAYING THE WORDS IS THE CHILD BAPTIZED | <audio class="audio-player2" src="zero_shot_tts/ref/tts_1188-133604-0004.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gen/tts_1089-134686-0021.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gt/tts_1089-134686-0021.wav" controls preload></audio> |
| THAT IS ONE REASON YOU ARE OJO THE UNLUCKY SAID THE WOMAN IN A SYMPATHETIC TONE | <audio class="audio-player2" src="zero_shot_tts/ref/tts_1284-1180-0001.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gen/tts_1284-1180-0024.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gt/tts_1284-1180-0024.wav" controls preload></audio> |
| THE DEWS WERE SUFFERED TO EXHALE AND THE SUN HAD DISPERSED THE MISTS AND WAS SHEDDING A STRONG AND CLEAR LIGHT IN THE FOREST WHEN THE TRAVELERS RESUMED THEIR JOURNEY | <audio class="audio-player2" src="zero_shot_tts/ref/1320_122612_000001_000000.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gen/tts_1320-122612-0001.wav" controls preload></audio> | <audio  class="audio-player2" src="zero_shot_tts/gt/tts_1320-122612-0001.wav" controls preload></audio> |
| BY THIS TIME LORD CHELFORD AND WYLDER RETURNED AND DISGUSTED RATHER WITH MYSELF I RUMINATED ON MY WANT OF GENERAL SHIP | <audio class="audio-player2" src="zero_shot_tts/ref/5683_32865_000001_000000.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gen/tts_5683-32866-0004.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/gt/tts_5683-32866-0004.wav" controls preload></audio> |


### Cloning famous person's voice 
In the following, we try to using 3 seconds prompt from three famous person: Theresa May, Barack Obama and Taylor Swift, and using their voice to read some text content (randomly choose from LibriTTS).

| <center> Name </center> | <center> Content (The transcirption of the target audio) </center> | <center> Prompt </center>| <center> Generated Speech </center>|
| -----------     |  -----------     |
| Barack Obama | YOUNG HAD BEEN COMMANDED TO HIS MOTHER'S CHAMBER SO SOON AS HE HAD COME OUT FROM HIS CONVERSE WITH THE SQUIRE | <audio class="audio-player" src="zero_shot_tts/famous/obama/obama.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/obama/tts_61-70970-0000_sampling_sample0.wav" controls preload></audio> |
| Barack Obama | I CANNOT ALLOW THE EXAMINATION TO BE HELD IF ONE OF THE PAPERS HAS BEEN TAMPERED WITH THE SITUATION MUST BE FACED | <audio class="audio-player" src="zero_shot_tts/famous/obama/obama.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/obama/tts_1580-141084-0008_sampling_sample0.wav" controls preload></audio> |
| Barack Obama | MUCH LATER WHEN A FRIEND OF HIS WAS PREPARING AN EDITION OF ALL HIS LATIN WORKS HE REMARKED TO HIS HOME CIRCLE IF I HAD MY WAY ABOUT IT THEY WOULD REPUBLISH ONLY THOSE OF MY BOOKS WHICH HAVE DOCTRINE MY GALATIANS FOR INSTANCE | <audio class="audio-player" src="zero_shot_tts/famous/obama/obama.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/obama/tts_2830-3979-0007_sampling_sample0.wav" controls preload></audio> |
| Barack Obama | GRAM ROUGHLY ONE TWENTY EIGHTH OF AN OUNCE | <audio class="audio-player" src="zero_shot_tts/famous/obama/obama.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/obama/tts_8463-294825-0015_sampling_sample0.wav" controls preload></audio> |
| Theresa May | HE GAVE WAY TO THE OTHERS VERY READILY AND RETREATED UNPERCEIVED BY THE SQUIRE AND MISTRESS FITZOOTH TO THE REAR OF THE TENT | <audio class="audio-player" src="zero_shot_tts/famous/May/tts_61-70968-0011_input1.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/May/tts_61-70968-0011_sampling_sample0.wav" controls preload></audio> |
| Taylor Swift | YOUNG HAD BEEN COMMANDED TO HIS MOTHER'S CHAMBER SO SOON AS HE HAD COME OUT FROM HIS CONVERSE WITH THE SQUIRE | <audio class="audio-player" src="zero_shot_tts/famous/ts/tts_8555-284449-0020_input1.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/ts/tts_61-70970-0000_sampling_sample0.wav" controls preload></audio> |
| Taylor Swift | REST AND BE STILL UNTIL I WARN YOU | <audio class="audio-player" src="zero_shot_tts/famous/ts/tts_8555-284449-0020_input1.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/ts/tts_61-70970-0017_sampling_sample0.wav" controls preload></audio> |
| Taylor Swift | THE COMBINED BANDS OF BOTH THE COUNTRIES PLAYED THE MUSIC AND A FINE SUPPER WAS SERVED | <audio class="audio-player" src="zero_shot_tts/famous/ts/tts_8555-284449-0020_input1.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/ts/tts_8555-284449-0020_sampling_sample0.wav" controls preload></audio> |

### Cloning the person's voice from your daily life
In this part, we show some case that clone our friends's voice. We directly use our smart phone to record 3 seconds prompts( One use the iphone, the other use VIVO). We directly speak chinese, we expect the model can transfer our voice into English.

| <center> Name </center> | <center>  Content  </center> | <center> Prompt </center>| <center> Generated Speech </center>|
| -----------     |  -----------     |
| Girl | AND EMIL MOWED HIS WAY SLOWLY DOWN TOWARD THE CHERRY TREES | <audio class="audio-player" src="zero_shot_tts/famous/yy/prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/yy/tts_237-134500-0014_sampling_sample0.wav" controls preload></audio> |
| Girl | THE DEPARTURE WAS NOT AT ALL AGREEABLE | <audio class="audio-player" src="zero_shot_tts/famous/yy/prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/yy/tts_672-122797-0024_sampling_sample0.wav" controls preload></audio> |
| Girl | IT'S NOT PARTICULARLY RARE SHE SAID BUT SOME OF IT WAS MY MOTHER'S |<audio class="audio-player" src="zero_shot_tts/famous/yy/prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/yy/tts_4446-2273-0009_sampling_sample0.wav" controls preload></audio> |
| Girl | WHAT I MEAN IS THAT I WANT YOU TO PROMISE NEVER TO SEE ME AGAIN NO MATTER HOW OFTEN I COME NO MATTER HOW HARD I BEG |<audio class="audio-player" src="zero_shot_tts/famous/yy/prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/yy/tts_4446-2275-0033_sampling_sample0.wav" controls preload></audio> |
| Girl |DO YOU KNOW LAKE OH I REALLY CAN'T TELL BUT HE'LL SOON TIRE OF COUNTRY LIFE | <audio class="audio-player" src="zero_shot_tts/famous/yy/prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/yy/tts_5683-32865-0013_sampling_sample0.wav" controls preload></audio> |
| Boy | THE EARTH IS NOT DEVOID OF RESEMBLANCE TO A JAIL |<audio class="audio-player" src="zero_shot_tts/famous/dc/dongchao_prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/dc/tts_4507-16021-0043_sampling_sample0.wav" controls preload></audio> |
| Boy | INDEED THERE WERE ONLY ONE OR TWO STRANGERS WHO COULD BE ADMITTED AMONG THE SISTERS WITHOUT PRODUCING THE SAME RESULT |<audio class="audio-player" src="zero_shot_tts/famous/dc/dongchao_prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/dc/tts_3575-170457-0040_sampling_sample0.wav" controls preload></audio> |
| Boy | ALSO THERE WAS A STRIPLING PAGE WHO TURNED INTO A MAID |<audio class="audio-player" src="zero_shot_tts/famous/dc/dongchao_prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/dc/tts_61-70968-0004_sampling_sample1.wav" controls preload></audio> |
| Boy | I HAD A NAME I BELIEVE IN MY YOUNG DAYS BUT I HAVE FORGOTTEN IT SINCE I HAVE BEEN IN SERVICE | <audio class="audio-player" src="zero_shot_tts/famous/dc/dongchao_prompt.wav" controls preload></audio> | <audio class="audio-player" src="zero_shot_tts/famous/dc/tts_3729-6852-0011_sampling_sample1.wav" controls preload></audio> |

### Long sentence by TTS

| <center>  Content </center> | <center> Generated Speech </center>| <center> GT Speech </center>|
| -----------------------     |  -----------   | ----- |-------|
| THE DYNAMO ELECTRIC MACHINE THOUGH SMALL WAS ROBUST FOR UNDER ALL THE VARYING SPEEDS OF WATER POWER AND THE VICISSITUDES OF THE PLANT TO WHICH IT BELONGED IT CONTINUED IN ACTIVE USE UNTIL EIGHTEEN NINETY NINE SEVENTEEN YEARS | <audio class="audio-player2" src="zero_shot_tts/long/gen/tts_2300-131720-0003.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/long/gt/tts_2300-131720-0003.wav" controls preload></audio> |
| EVERY ONE COULD OBSERVE HIS AGITATION AND PROSTRATION A PROSTRATION WHICH WAS INDEED THE MORE REMARKABLE SINCE PEOPLE WERE NOT ACCUSTOMED TO SEE HIM WITH HIS ARMS HANGING LISTLESSLY BY HIS SIDE HIS HEAD BEWILDERED AND HIS EYES WITH ALL THEIR BRIGHT INTELLIGENCE BEDIMMED | <audio class="audio-player2" src="zero_shot_tts/long/gen/tts_7127-75947-0000.wav" controls preload></audio> | <audio class="audio-player2" src="zero_shot_tts/long/gt/tts_7127-75947-0000.wav" controls preload></audio> |

## Zero-shot VC.
In the following, we show some case using VCTK. Similar with previous section, we can easy to use our own voice prompt to realize voice conversion. 

| <center> Source </center> | <center> Prompt </center>| <center> Generated Speech </center>| <center> Ground Truth Speech </center> |
| -----------     |  -----------     |
| <audio src="zero_shot_vc/source/VC_vctk_0_1.wav" controls preload></audio> | <audio src="zero_shot_vc/prompt/VC_vctk_0_1.wav" controls preload></audio> | <audio src="zero_shot_vc/gen/VC_vctk_0_1.wav" controls preload></audio> | <audio src="zero_shot_vc/gt/VC_vctk_0_1.wav" controls preload></audio> |
| <audio src="zero_shot_vc/source/VC_vctk_0_2.wav" controls preload></audio> | <audio src="zero_shot_vc/prompt/VC_vctk_0_2.wav" controls preload></audio> | <audio src="zero_shot_vc/gen/VC_vctk_0_2.wav" controls preload></audio> | <audio src="zero_shot_vc/gt/VC_vctk_0_2.wav" controls preload></audio> |
| <audio src="zero_shot_vc/source/VC_vctk_0_3.wav" controls preload></audio> | <audio src="zero_shot_vc/prompt/VC_vctk_0_3.wav" controls preload></audio> | <audio src="zero_shot_vc/gen/VC_vctk_0_3.wav" controls preload></audio> | <audio src="zero_shot_vc/gt/VC_vctk_0_3.wav" controls preload></audio> |
| <audio src="zero_shot_vc/source/VC_vctk_33_3.wav" controls preload></audio> | <audio src="zero_shot_vc/prompt/VC_vctk_33_3.wav" controls preload></audio> | <audio src="zero_shot_vc/gen/VC_vctk_33_3.wav" controls preload></audio> | <audio src="zero_shot_vc/gt/VC_vctk_33_3.wav" controls preload></audio> |
| <audio src="zero_shot_vc/source/VC_vctk_27_1.wav" controls preload></audio> | <audio src="zero_shot_vc/prompt/VC_vctk_27_1.wav" controls preload></audio> | <audio src="zero_shot_vc/gen/VC_vctk_27_1.wav" controls preload></audio> | <audio src="zero_shot_vc/gt/VC_vctk_27_1.wav" controls preload></audio> |
| <audio src="zero_shot_vc/source/VC_vctk_25_4.wav" controls preload></audio> | <audio src="zero_shot_vc/prompt/VC_vctk_25_4.wav" controls preload></audio> | <audio src="zero_shot_vc/gen/VC_vctk_25_4.wav" controls preload></audio> | <audio src="zero_shot_vc/gt/VC_vctk_25_4.wav" controls preload></audio> |

## Zero-shot Sing Voice Synthesis

| <center> Content (words of song) </center> | <center> Speaker Prompt </center> | <center> Generated Sing </center>|
| -----------     |  -----------     |
| 十年之前@我不认识你@你不属于我@我们还是一样@陪在一个陌生人左右 | <audio src="sing/ref/sing_187_0003_48k.wav" controls preload></audio> | <audio src="sing/gen/sing_187_0003_48k.wav" controls preload></audio> |
| 好吧天亮之后总是潦草离场@清醒的人最荒唐 | <audio src="sing/ref/sing_770_0008_48k.wav" controls preload></audio> | <audio src="sing/gen/sing_770_0008_48k.wav" controls preload></audio> |
| 我们这些努力不简单@快乐炼成泪水@是一种勇敢 | <audio src="sing/ref/sing_887_0011_48k.wav" controls preload></audio> | <audio src="sing/gen/sing_887_0011_48k.wav" controls preload></audio> |
| 空空留遗憾多难堪又为难 | <audio src="sing/ref/sing_Alto-6ban0005.wav" controls preload></audio> | <audio src="sing/gen/sing_Alto-6ban0005.wav" controls preload></audio> |
| 嗯纵容着任性的随意的放肆的轻易的 | <audio src="sing/ref/sing_Alto-6ban0010.wav" controls preload></audio> | <audio src="sing/gen/sing_Alto-6ban0010.wav" controls preload></audio> |
| 你说你好想带我回去你的家 | <audio src="sing/ref/sing_Alto-6manman0009.wav" controls preload></audio> | <audio src="sing/gen/sing_Alto-6manman0009.wav" controls preload></audio> |
| 狼狈比失去难受我怀念的是无话不说 | <audio src="sing/ref/sing_Alto-6wo0011.wav" controls preload></audio> | <audio src="sing/gen/sing_Alto-6wo0011.wav" controls preload></audio> |
| 我怀念的@是争吵以后还会想要爱你的冲动 | <audio src="sing/ref/sing_Alto-6wo0013.wav" controls preload></audio> | <audio src="sing/gen/sing_Alto-6wo0013.wav" controls preload></audio> |
| 我和我最后的倔强握紧双手绝对不放下一站 | <audio src="sing/ref/sing_Alto-60008.wav" controls preload></audio> | <audio src="sing/gen/sing_Alto-60008.wav" controls preload></audio> |

## Zero-shot Speech Enhancement

| <center> Noisy Speech </center> | <center> De-noised Speech </center> | <center> Ground Truth </center>|
| -----------     |  -----------     |
| <audio src="se/noisy/se_out_0.wav" controls preload></audio> | <audio src="se/gen/se_out_0.wav" controls preload></audio> | <audio src="se/gt/se_out_0.wav" controls preload></audio> |
| <audio src="se/noisy/se_out_1.wav" controls preload></audio> | <audio src="se/gen/se_out_1.wav" controls preload></audio> | <audio src="se/gt/se_out_1.wav" controls preload></audio> |
| <audio src="se/noisy/se_out_4.wav" controls preload></audio> | <audio src="se/gen/se_out_4.wav" controls preload></audio> | <audio src="se/gt/se_out_4.wav" controls preload></audio> |
| <audio src="se/noisy/se_out_13.wav" controls preload></audio> | <audio src="se/gen/se_out_13.wav" controls preload></audio> | <audio src="se/gt/se_out_13.wav" controls preload></audio> |
| <audio src="se/noisy/se_out_33.wav" controls preload></audio> | <audio src="se/gen/se_out_33.wav" controls preload></audio> | <audio src="se/gt/se_out_33.wav" controls preload></audio> |
| <audio src="se/noisy/se_out_18.wav" controls preload></audio> | <audio src="se/gen/se_out_18.wav" controls preload></audio> | <audio src="se/gt/se_out_18.wav" controls preload></audio> |

### Using UniAudio to denoise the speech from film.
In the following, we find a moive clips from bilibili (https://www.bilibili.com/video/BV1UA411J7H2/?vd_source=e4a11ee6c459009bfa05833e70cd49c3). Due to the actor's lines are easy to be misunderstanding if you never see the moive "功夫", which directed and starring by Stephen Chow in 2004 (strongly recommendation!). We only show part of the content. 

| <center> Noisy Speech </center> | <center> De-noised Speech </center> |
| -----------     |  -----------     |
| <audio src="se/kongfu/SE_kongfu2_noisy.wav" controls preload></audio> | <audio src="se/kongfu/SE_kongfu2_denoise1.wav" controls preload></audio> |


## Zero-shot Target Speaker Extraction

| <center> Mixed Speech </center> | <center> Prompt </center> | <center> Extracted Speech </center> | <center> Ground Truth </center>|
| -----------     |  -----------     |
| <audio src="TSE/mix/61-70968-0000_8455-210777-0012.wav" controls preload></audio> | <audio src="TSE/prompt/61-70968-0000_8455-210777-0012.wav" controls preload></audio> | <audio src="TSE/gen/61-70968-0000_8455-210777-0012.wav" controls preload></audio> | <audio src="TSE/gt/61-70968-0000_8455-210777-0012.wav" controls preload></audio> |
| <audio src="TSE/mix/121-123852-0002_1188-133604-0003.wav" controls preload></audio> | <audio src="TSE/prompt/121-123852-0002_1188-133604-0003.wav" controls preload></audio> | <audio src="TSE/gen/121-123852-0002_1188-133604-0003.wav" controls preload></audio> | <audio src="TSE/gt/121-123852-0002_1188-133604-0003.wav" controls preload></audio> |
| <audio src="TSE/mix/1188-133604-0001_1995-1826-0012.wav" controls preload></audio> | <audio src="TSE/prompt/1188-133604-0001_1995-1826-0012.wav" controls preload></audio> | <audio src="TSE/gen/1188-133604-0001_1995-1826-0012.wav" controls preload></audio> | <audio src="TSE/gt/1188-133604-0001_1995-1826-0012.wav" controls preload></audio> |
| <audio src="TSE/mix/260-123440-0003_2961-960-0009.wav" controls preload></audio> | <audio src="TSE/prompt/260-123440-0003_2961-960-0009.wav" controls preload></audio> | <audio src="TSE/gen/260-123440-0003_2961-960-0009.wav" controls preload></audio> | <audio src="TSE/gt/260-123440-0003_2961-960-0009.wav" controls preload></audio> |

## Zero-shot Text-to-Sound

| <center> Instruction (The text description) </center> | <center> Generated Sound </center>|
| -----------     |  -----------     |
| Someone is running alone on a hardwood floor. | <audio src="sound/gen/3.wav" controls preload></audio> |
| Repeated bursts of fireworks are accompanied by intermittent cheers and whistles of a crowd | <audio src="sound/gen/6.wav" controls preload></audio> |
| A bird frequently vocalizing with a high pitched chirp. | <audio src="sound/gen/26.wav" controls preload></audio> |
| Several musicians warm up on their instruments as people in the audience talk. | <audio src="sound/gen/230.wav" controls preload></audio> |
| Birds chirp and people talk as cars go by. | <audio src="sound/gen/232.wav" controls preload></audio> |
| After a train horn blows, the chugging of the engine Increases. | <audio src="sound/gen/234.wav" controls preload></audio> |
| After a train horn blows, the chugging of the engine Increases. | <audio src="sound/gen/234.wav" controls preload></audio> |

#### 20s audio genenration

| <center> Instruction (The text description) </center> | <center> Generated Sound </center>|
| -----------     |  -----------     |
| An ambulance siren wails continue for more than twenty seconds. | <audio src="sound/long/TSS_139_sampling_sample1.wav" controls preload></audio> |
| A cricket is chirping as the wind is blowing. | <audio src="sound/long/TSS_761_sampling_sample0.wav" controls preload></audio> |


## Zero-shot Text-to-Music

| <center> Instruction (The text description)  </center> | <center> Generated Music </center>|
| -----------     |  -----------     |
| The Pop song features harmonizing vocals singing over energetic crash cymbals, groovy bass guitar, wide electric guitar melody, punchy snare and soft kick hits. There is a short drum break at the very beginning of the loop. It sounds happy, nostalgic and euphoric, as it gives off vibes of a Christmas song. | <audio src="music/gen/3OlK_1yQOk.wav" controls preload></audio> |
| This is a rap music piece played behind a rollerskating video. The sound of the skaters can be heard faintly throughout the recording. There is a male voice rapping at the forefront while other voices can be heard singing melodically in the background and ad-libbing occasionally. There is a mild keyboard playing the tune while a loud electronic drum beat is playing the rhythm. The atmosphere of this piece is groovy and urban. | <audio src="music/gen/43OOP6UEw0.wav" controls preload></audio> |
| The low quality recording features a live performance of fruity male vocal singing over funky piano melody and beat played on playback that consists of punchy snare and kick hits, shimmering hi hats and smooth bass. The crowd is also singing along, harmonizing with the lead vocal. It sounds emotional and groovy, even though the recording is noisy. | <audio src="music/gen/78P-0zWJtg.wav" controls preload></audio> |
| This is the recording of a gear showcase jam. There is an overdriven electric guitar playing a groovy solo with the amplified reverb effect. There is a crunchy sound. The piece can be used as the jingle of an advertisement. It could also be used for lifting electric guitar samples to be used in a beat. | <audio src="music/gen/KGUrOb1qgU.wav" controls preload></audio> |
| The R&B song features a passionate male vocalist singing over a wide funky electric guitar melody, smooth bass guitar, punchy kick and snare hits, shimmering hi hats, snappy rimshots and soft crash cymbals. The rimshots are present in the first half of the loop, while a more energetic second part of the loop consists of punchy snare hits. It sounds emotional and heartfelt, as the vocal is slightly distorted. | <audio src="music/gen/m-N4i-ge28.wav" controls preload></audio> |
| The low quality recording features a traditional song that consists of wide, harmonizing female vocals singing over acoustic rhythm guitar. It sounds mellow, soft and emotional. | <audio src="music/gen/yRFCl-z-EE.wav" controls preload></audio> |
| someone is playing a high pitched melody on a steel drum. The file is of poor audio-quality. | <audio src="music/gen/-3Kv4fdm7Uk.wav" controls preload></audio> |
| The pop rock music features a male voice singing. An electric guitar with a distortion effect on plays plays two chords every two measures. The drums play a strong rhythm and together with a synth bass drive the pulse of the music. | <audio src="music/gen/-hSMzrWZCAE.wav" controls preload></audio> |
| The low quality recording features a live performance of loud steel pans melody over playback instrumental that consists of shimmering hi hats, open hats and "4 on the floor" kick pattern. There are some crowd talking noises in the background. It sounds exotic and energetic. | <audio src="music/gen/0bvPjMQ_WbE.wav" controls preload></audio> |
| This is a pop music piece. The words are being sung by two vocals: one male and one female which lead to a duet for the chorus. There is a banjo and an electric guitar playing the melody while a simple electronic drum beat provides the rhythmic background for the song. It is a slightly melodic and emotional song. This piece could be used in the soundtrack of a romantic drama during a flashback scene. | <audio src="music/gen/2U8Dvh7nwFI.wav" controls preload></audio> |

### 20s music generation

| <center> Instruction (The text description)  </center> | <center> Generated Music </center>|
| -----------     |  -----------     |
| The music is purely instrumental and so it features no human voice. More gamelans are played but by using different techniques. Other metallic percussion instruments can be heard. | <audio src="TTM/long/TTM_7XMqcbZKNNw_sampling_sample0.wav" controls preload></audio> |
| This song is a sweet duet. The tempo is medium with a melodious, intense piano accompaniment , electric guitar rhythm, steady drumming and synthesiser arrangements. This song is melodic, story telling, spirited, emotional, passionate and sweet. The lyrics are simple and so this song could be a Children’s Song. | <audio src="TTM/long/TTM_DP2vmsftZHY_sampling_sample0.wav" controls preload></audio> |


## Instructed TTS

| <center> Instruction (Control the generated samples) </center> | <center> Content </center> | <center> Generated Speech </center>|
| -----------     |  -----------     |
| A man speaks loudly and slowly with a bass tone | Degenerated into deadness and formality | <audio src="ITTS/gen/1382_130549_000089_000000_Jenny_p-35.00_v+26.15_s-25.79_Cheerful.wav" controls preload></audio> |
| The mournful madame says: loud, slow and high pitched | He flushed crimson | <audio src="ITTS/gen/1383_130489_000023_000000_Aria_p+29.84_v+34.20_s-27.24_Sad.wav" controls preload></audio> |
| A man who speaks very slowly, his tone is very low, shehehe yowled loudly | Her blank gaze chilled you | <audio src="ITTS/gen/1383_130489_000081_000000_Aria_p-30.19_v+25.97_s-25.87_Shouting.wav" controls preload></audio> |
| A man said with a relatively low tone and saying a fast speed and breathe loudly | He sacrificed the vulgar prizes of life | <audio src="ITTS/gen/1383_130489_000048_000000_Sara_p-33.05_v+28.69_s+29.89_Whispering.wav" controls preload></audio> |

## Audio Edit

| <center> Instruction </center> | <center> Source Audio </center> | <center> Generated Audio </center>| 
| -----------     |  -----------     |
| Add: loud roar of traffic in the background | <audio class="audio-player" src="A_edit/Audit_audio_edit_add_132_input1.wav" controls preload></audio> | <audio class="audio-player" src="A_edit/Audit_audio_edit_add_132_sampling_sample0.wav" controls preload></audio> | 
| Add: a helicopters' engine is running in the background | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_add_142_input1.wav" controls preload></audio> | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_add_142_sampling_sample3.wav" controls preload></audio> | 
| drop: birds chirping, wings flap | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_drop_151_input1.wav" controls preload></audio> | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_drop_151_sampling_sample0.wav" controls preload></audio> | 
| Drop:a motorcycle idles nearby at moderate speed | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_drop_273_input1.wav" controls preload></audio> | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_drop_273_sampling_sample0.wav" controls preload></audio> | 
| super resolution: A clock is ringing a bell | <audio class="audio-player" src="A_edit/Audit_audio_edit_super_290_input1.wav" controls preload></audio> | <audio class="audio-player" src="A_edit/Audit_audio_edit_super_290_sampling_sample0.wav" controls preload></audio> | 
| super resolution: A clock is chiming | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_super_14_input1.wav" controls preload></audio> | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_super_14_sampling_sample0.wav" controls preload></audio> | 
| Super resolution: Man speaking with water sounds | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_super_253_input1.wav" controls preload></audio> | <audio class="audio-player" src="A_edit/gen/Audit_audio_edit_super_253_sampling_sample0.wav" controls preload></audio> | 


## Speech dereverberation

| <center> Reverberation Speech </center> | <center> De-reverberated Speech </center> | <center> Ground Truth </center>|
| -----------     |  -----------     |
| <audio src="RIR/Speech_RIR_simulate_ris_test5_input0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test5_sampling_sample0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test5_input1.wav" controls preload></audio> |
| <audio src="RIR/Speech_RIR_simulate_ris_test22_input0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test22_sampling_sample0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test22_input1.wav" controls preload></audio> |
| <audio src="RIR/Speech_RIR_simulate_ris_test23_input0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test23_sampling_sample0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test23_input1.wav" controls preload></audio> |
| <audio src="RIR/Speech_RIR_simulate_ris_test48_input0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test48_sampling_sample0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test48_input1.wav" controls preload></audio> |
| <audio src="RIR/Speech_RIR_simulate_ris_test81_input0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test81_sampling_sample0.wav" controls preload></audio> | <audio src="RIR/Speech_RIR_simulate_ris_test81_input1.wav" controls preload></audio> |



## Speech Edit

| <center> Content <img width=500/> </center> | <center> Instruction </center> | <center> Generated Speech </center> | <center> Original Audio </center>| 
| -----------     |  -----------     |
| Please wait for me, Marie," Emil coaxed. | delete the word 'for' | <audio class="audio-player" src="speech_edit_sample/gen/237_134493_000009_000001.wav" controls preload></audio> | <audio class="audio-player" src="speech_edit_sample/org/237_134493_000009_000001.wav" controls preload></audio> | 
| He is called, as you know, the apostle of the Indies. | replace the word "called" as "named" | <audio class="audio-player"  src="speech_edit_sample/gen/1089_134686_000032_000004.wav" controls preload></audio> | <audio class="audio-player" src="speech_edit_sample/org/1089_134686_000032_000004.wav" controls preload></audio> | 
| It is thou that must tell me! | delete the word 'tell' | <audio class="audio-player" src="speech_edit_sample/gen/1221_135766_000027_000002.wav" controls preload></audio> | <audio class="audio-player" src="speech_edit_sample/org/1221_135766_000027_000002.wav" controls preload></audio> | 
| Bartley leaned over her shoulder, without touching her, and whispered in her | replace the word "shoulder" as  "feet" | <audio class="audio-player" src="speech_edit_sample/gen/4446_2273_000051_000000.wav" controls preload></audio> | <audio class="audio-player" src="speech_edit_sample/org/4446_2273_000051_000000.wav" controls preload></audio> | 
| He had three flies on his cast, and, because in these waters there was always | insert a word "large" after "waters" | <audio class="audio-player" src="speech_edit_sample/gen/7176_88083_000020_000001.wav" controls preload></audio> | <audio class="audio-player" src="speech_edit_sample/org/7176_88083_000020_000001.wav" controls preload></audio> | 
| They could see that a conflict meant serious results | insert a word "many" after "meant" | <audio class="audio-player" src="speech_edit_sample/gen/7729_102255_000012_000006.wav" controls preload></audio> | <audio class="audio-player" src="speech_edit_sample/org/7729_102255_000012_000006.wav" controls preload></audio> | 

## Chinese TTS 

| <center> Content </center> | <center> Generated Speech </center>|
| -----------     |  -----------     |
| 你投了票的 | <audio src="zero_shot_tts/chinese/sing_SSB0009_SSB00090400_sampling_sample1.wav" controls preload></audio> |
| 未来在吸引球迷和赞助商以及推广乒乓球运动方面 | <audio src="zero_shot_tts/chinese/sing_SSB0851_SSB08510142_sampling_sample0.wav" controls preload></audio> |
| 壤塘县的乡镇有什么 | <audio src="zero_shot_tts/chinese/sing_SSB0851_SSB08510143_sampling_sample3.wav" controls preload></audio> |
| 但并不是每家公司的所有产品都会被影响 | <audio src="zero_shot_tts/chinese/sing_SSB0851_SSB08510144_sampling_sample0.wav" controls preload></audio> |
| 恐怖片的电影有什么 | <audio src="zero_shot_tts/chinese/sing_SSB0851_SSB08510164_sampling_sample0.wav" controls preload></audio> |

