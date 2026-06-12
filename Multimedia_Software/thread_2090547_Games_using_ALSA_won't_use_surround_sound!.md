---
title: "Games using ALSA won't use surround sound!"
date: 2012-12-02
forum: Multimedia Software
---

### Post by snow56767 on 2012-12-02
Hi guys,
    I have recently installed a new audio card, a Creative Labs Audigy 2 to be specific, and so I have re-installed ALSA. The only problem is that now my surround sound won't work with my games (Xonotic and Doom3). I can get it to work in VLC by selecting the Dobly Digital stream then selecting my sound card. I have looked at the console and my games keep telling me:

```

ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM surround51
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'surround51' failed: No such file or directory

```

The output of aplay -L is:

```

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=Audigy2
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    SB Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output

```So why can't ALSA connect to surround51? it is obviously there and working because it is loaded by the kernel. I think it is also important to say that I manually downloaded, compiled, and installed my ALSA drivers.

---

### Post by Another Monkey on 2012-12-03
See if my post [here]("http://ubuntuforums.org/showpost.php?p=12385729&postcount=3") offers any help.

As you are using 5.1, you will want to use the value "6" where I have used "8".

---

### Post by snow56767 on 2012-12-03
That did help and I also figured out another solution to my specific problem. I needed to open my alsa.conf file (/usr/share/alsa/alsa.conf) and change the default card to 1. This solved my issue because I have two sound cards and the one I wanted (my Audigy) is card 1, not card 0.

---

