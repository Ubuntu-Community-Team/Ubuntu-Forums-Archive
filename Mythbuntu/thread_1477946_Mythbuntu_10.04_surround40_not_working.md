---
title: "Mythbuntu 10.04: surround40 not working"
date: 2010-05-09
forum: Mythbuntu
---

### Post by agkbill on 2010-05-09
Hi,

I have great problems getting 4.0 surround to work, the problem is that when I looking at DVD with 5.1 surround (works ok) I can not hear speech and I guess that all sound going to LFE is also not there.

If I set back to "stereo" I can hear speech but of cause not surround.

I was hoping to solve this by using the surround40 setting that is now available but I can not get it to work.

Using Auto build repo 0.24.


Settings in MythTV that works fine are:

"ALSA:default:CARD=EMU1010" and mixer "ALSA:default"
works both "sterio" and "5.1"


aplay -L give:

#####################################################################
christer@christer-mythtv:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=EMU1010
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=EMU1010,DEV=0
    E-mu 1010 [MAEM8810], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
christer@christer-mythtv:~$ 

####################################################################


If I test my speeker setup with:

speaker-test -c 4 -Dplug:surround40 -t wav

It works perfect.

So I tried to put the setting in MythTV, but no luck.

I tried:

"ALSA:-Dplug:surround40:CARD=EMU1010" same in Mixer.

"ALSA:surround40:CARD=EMU1010" same in Mixer.

Non of the two did work.

I also noticed that in MythTV the volume is set to 0, but Vol control on my remote that normally works fine do not work.


Any ideas on how to solve this would be most appreciated.


Best regards,
/Christer Eriksson

---

