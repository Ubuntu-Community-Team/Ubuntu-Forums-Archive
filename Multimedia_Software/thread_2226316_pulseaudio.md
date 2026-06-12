---
title: "pulseaudio"
date: 2014-05-26
forum: Multimedia Software
---

### Post by 0536g007ve on 2014-05-26
pulaseaudio seems to be working, but no sound.  after totally deleting audio and spending a week trying to fix it, i have concluded that i am lost. 
[COLOR=#000000] version 12.04  [/COLOR][COLOR=#545454][FONT=arial]**Ubuntu 12.04**[/FONT][/COLOR][COLOR=#545454][FONT=arial].4 LTS Precise Pangolin[/FONT][/COLOR][COLOR=#000000]

[/COLOR] aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

the last part of ([COLOR=#000000][FONT=Ubuntu Mono]pkill pulseaudio; sleep 2; pulseaudio -vv) seems to have the word suspended in it a lot?[/FONT][/COLOR]
I: [alsa-sink] alsa-sink.c: Device suspended...
I: [pulseaudio] core.c: All sinks and sources are suspended, vacuuming memory
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes

thanks in advance for help

---

### Post by ronb19495 on 2014-05-26
try this fix by odur
1. Uninstalling pulseaudio and purged it (sudo apt-get autoremove --purge pulseaudio).
2. Rebooted and removed ~/.config/pulse/ (rm -r ~/.config/pulse/)
3. Rebooted again and installed pulseaudio again (sudo apt-get install pulseaudio paprefs pulseaudio-esound-compat).

---

### Post by 0536g007ve on 2014-05-26
Before I try purge again is there a way to check speaker connection to pulseaudio?  Volume control indicates it is working but no sound.
Thanks

---

### Post by ronb19495 on 2014-05-27
try installing pavucontrol if you dont have it installed.sudo apt-get install pavucontrol. when installed click on configuration tab and also check to see if sound is not muted in pavucontrol also check alsamixer

---

### Post by ronb19495 on 2014-05-27
heres some screenshots of alsamixer and pavucontrol alsamixer screenshot 1,screenshot 2 pavucontrol with the 3 drop down configuration tabs for my setup,screenshot 2 pavucontrol with soun unmuted click on playback button to check that,good luck
by the way pavucontrol when installed is named pulseaudio volume control 
I started typing and named it puss audio not nice hey

---

### Post by 0536g007ve on 2014-06-01
Opened music in youtube, opened pulseaudio control, clicked output devices, the bars at the bottom are moving right to left indicating music is playing, but no sound out of speakers
```
robin@robin-HP-G62-Notebook-PC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
robin@robin-HP-G62-Notebook-PC:~$ 


I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
D: [pulseaudio] alsa-util.c: Trying dca:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-dts-surround-51+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
D: [pulseaudio] alsa-util.c: Trying dca:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-dts-surround-51+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
D: [pulseaudio] alsa-util.c: Trying dca:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-dts-surround-51+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
D: [pulseaudio] alsa-util.c: Trying dca:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra1+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra1+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra1+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,1
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra2
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra2+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra2+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra2+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,2
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra3+input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra3+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra3+input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0,3
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hw:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hw:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:0
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo supported.
D: [pulseaudio] alsa-mixer.c: Looking at profile input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: [pulseaudio] flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
D: [pulseaudio] flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
D: [pulseaudio] alsa-mixer.c: Profile set 0x8c2f568, auto_profiles=yes, probed=yes, n_mappings=1, n_profiles=3, n_decibel_fixes=0
D: [pulseaudio] alsa-mixer.c: Mapping analog-stereo (Analog Stereo), priority=60, channel_map=front-left,front-right, supported=yes, direction=0
D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo (Analog Stereo Output), priority=6000, supported=yes n_input_mappings=0, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Output analog-stereo
D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo (Analog Stereo Duplex), priority=6060, supported=yes n_input_mappings=1, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Input analog-stereo
D: [pulseaudio] alsa-mixer.c: Output analog-stereo
D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo (Analog Stereo Input), priority=60, supported=yes n_input_mappings=1, n_output_mappings=0
D: [pulseaudio] alsa-mixer.c: Input analog-stereo
I: [pulseaudio] module-card-restore.c: Restoring profile for card alsa_card.pci-0000_00_1b.0.
I: [pulseaudio] card.c: Created 0 "alsa_card.pci-0000_00_1b.0"
D: [pulseaudio] reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM remap-surround71
I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:0
I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
I: [pulseaudio] alsa-sink.c: Successfully opened device hw:0.
I: [pulseaudio] alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] alsa-mixer.c: Added 1 ports
I: [pulseaudio] module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_1b.0.analog-stereo.
I: [pulseaudio] module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_00_1b.0.analog-stereo.
I: [pulseaudio] module-device-restore.c: Restoring mute state for sink alsa_output.pci-0000_00_1b.0.analog-stereo.
I: [pulseaudio] sink.c: Created sink 0 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
I: [pulseaudio] sink.c:     device.api = "alsa"
I: [pulseaudio] sink.c:     device.class = "sound"
I: [pulseaudio] sink.c:     alsa.class = "generic"
I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] sink.c:     alsa.name = "HDA Generic"
I: [pulseaudio] sink.c:     alsa.id = "HDA Generic"
I: [pulseaudio] sink.c:     alsa.subdevice = "0"
I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] sink.c:     alsa.device = "0"
I: [pulseaudio] sink.c:     alsa.card = "0"
I: [pulseaudio] sink.c:     alsa.card_name = "HDA Intel MID"
I: [pulseaudio] sink.c:     alsa.long_card_name = "HDA Intel MID at 0xd4400000 irq 44"
I: [pulseaudio] sink.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: [pulseaudio] sink.c:     device.bus = "pci"
I: [pulseaudio] sink.c:     device.vendor.id = "8086"
I: [pulseaudio] sink.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] sink.c:     device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
I: [pulseaudio] sink.c:     device.form_factor = "internal"
I: [pulseaudio] sink.c:     device.string = "hw:0"
I: [pulseaudio] sink.c:     device.buffering.buffer_size = "65536"
I: [pulseaudio] sink.c:     device.buffering.fragment_size = "32768"
I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer"
I: [pulseaudio] sink.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] sink.c:     device.profile.description = "Analog Stereo"
I: [pulseaudio] sink.c:     device.description = "Built-in Audio Analog Stereo"
I: [pulseaudio] sink.c:     alsa.mixer_name = "Intel ID 2804"
I: [pulseaudio] sink.c:     alsa.components = "HDA:10ec0270,103c1425,00100100 HDA:80862804,80860101,00100000"
I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] source.c: Created source 0 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of Built-in Audio Analog Stereo"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     alsa.card = "0"
I: [pulseaudio] source.c:     alsa.card_name = "HDA Intel MID"
I: [pulseaudio] source.c:     alsa.long_card_name = "HDA Intel MID at 0xd4400000 irq 44"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "8086"
I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] source.c:     device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
I: [pulseaudio] source.c:     device.form_factor = "internal"
I: [pulseaudio] source.c:     device.string = "0"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-sink.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20.00ms
D: [pulseaudio] alsa-sink.c: hwbuf_unused=0
D: [pulseaudio] alsa-sink.c: setting avail_min=15502
D: [pulseaudio] alsa-mixer.c: Activating path analog-output
D: [pulseaudio] alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=no, has_volume=yes, has_dB=yes, min_volume=0, max_volume=87, min_dB=-65.25, max_dB=0
D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
I: [pulseaudio] alsa-sink.c: Successfully enabled deferred volume.
I: [pulseaudio] alsa-sink.c: Hardware volume ranges from -65.25 dB to 0.00 dB.
I: [pulseaudio] alsa-sink.c: Fixing base volume to 0.00 dB
I: [pulseaudio] alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-sink.c: Driver does not support hardware mute control, falling back to software mute control.
D: [pulseaudio] alsa-util.c: snd_pcm_dump():
D: [pulseaudio] alsa-util.c: Hardware PCM card 0 'HDA Intel MID' device 0 subdevice 0
D: [pulseaudio] alsa-util.c: Its setup is:
D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
D: [pulseaudio] alsa-util.c:   format       : S16_LE
D: [pulseaudio] alsa-util.c:   subformat    : STD
D: [pulseaudio] alsa-util.c:   channels     : 2
D: [pulseaudio] alsa-util.c:   rate         : 44100
D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
D: [pulseaudio] alsa-util.c:   msbits       : 16
D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
D: [pulseaudio] alsa-util.c:   period_size  : 8192
D: [pulseaudio] alsa-util.c:   period_time  : 185759
D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
D: [pulseaudio] alsa-util.c:   period_step  : 1
D: [pulseaudio] alsa-util.c:   avail_min    : 15502
D: [pulseaudio] alsa-util.c:   period_event : 0
D: [pulseaudio] alsa-util.c:   start_threshold  : -1
D: [pulseaudio] alsa-util.c:   stop_threshold   : 1073741824
D: [pulseaudio] alsa-util.c:   silence_threshold: 0
D: [pulseaudio] alsa-util.c:   silence_size : 0
D: [pulseaudio] alsa-util.c:   boundary     : 1073741824
D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
D: [alsa-sink] alsa-sink.c: Thread starting up
D: [pulseaudio] alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: [pulseaudio] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
D: [pulseaudio] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: [pulseaudio] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
D: [pulseaudio] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [pulseaudio] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] core-util.c: RealtimeKit worked.
I: [alsa-sink] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-sink] alsa-sink.c: Starting playback.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] module-device-restore.c: Could not set format on sink alsa_output.pci-0000_00_1b.0.analog-stereo
D: [pulseaudio] module-alsa-card.c: Found 0 jacks.
I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"").
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: [pulseaudio] module-udev-detect.c: Found 1 cards.
I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #5; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.0/modules/module-jackdbus-detect.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.0/modules/module-bluetooth-discover.so': success
D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus system bus c2ab24a88b902a72e43e0f030000000f as :1.65
D: [pulseaudio] bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/HFPAG on adapter /org/bluez/1154/hci0.
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/HFPHS on adapter /org/bluez/1154/hci0.
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/A2DPSource on adapter /org/bluez/1154/hci0.
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/A2DPSink on adapter /org/bluez/1154/hci0.
I: [pulseaudio] module.c: Loaded "module-bluetooth-discover" (index: #6; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.0/modules/module-esound-protocol-unix.so': failure
I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.0/modules/module-gconf.so': success
D: [pulseaudio] module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
W: [pulseaudio] module.c: module-combine is deprecated: Please use module-combine-sink instead of module-combine!
W: [pulseaudio] module-combine.c: We will now load module-combine-sink. Please make sure to remove module-combine from your configuration.
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module-device-restore.c: Restoring volume for sink combined.
I: [pulseaudio] module-device-restore.c: Restoring mute state for sink combined.
I: [pulseaudio] sink.c: Created sink 1 "combined" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     device.class = "filter"
I: [pulseaudio] sink.c:     device.description = "Simultaneous Output"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card"
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] source.c: Created source 1 "combined.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of Simultaneous Output"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     device.icon_name = "audio-input-microphone"
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=16777216, tlength=16777216, base=4, prebuf=1, minreq=0 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=16777216, tlength=16777216, base=4, prebuf=4, minreq=4 maxrewind=0
D: [combine] module-combine-sink.c: Thread starting up
D: [combine] core-util.c: RealtimeKit worked.
I: [combine] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 6.
D: [pulseaudio] module-device-restore.c: Could not set format on sink combined
I: [pulseaudio] module-stream-restore.c: Restoring volume for sink input sink-input-by-media-role:filter.
I: [pulseaudio] resampler.c: Using resampler 'trivial'
I: [pulseaudio] resampler.c: Using s16le as working format.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: [pulseaudio] sink-input.c: Created input 0 "Simultaneous output on Built-in Audio Analog Stereo" on alsa_output.pci-0000_00_1b.0.analog-stereo with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink-input.c:     media.name = "Simultaneous output on Built-in Audio Analog Stereo"
I: [pulseaudio] sink-input.c:     media.role = "filter"
I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-media-role:filter"
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink] alsa-sink.c: Latency set to 200.00ms
D: [alsa-sink] alsa-sink.c: hwbuf_unused=30256
D: [alsa-sink] alsa-sink.c: setting avail_min=15503
D: [alsa-sink] alsa-sink.c: Requesting rewind due to latency change.
D: [alsa-sink] alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: [alsa-sink] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: [alsa-sink] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 59904 bytes.
D: [alsa-sink] alsa-sink.c: before: 14976
D: [alsa-sink] alsa-sink.c: after: 14976
D: [alsa-sink] alsa-sink.c: Rewound 59904 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [alsa-sink] sink.c: latency = 2363
D: [alsa-sink] source.c: Processing rewind...
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module.c: Loaded "module-combine-sink" (index: #8; argument: "").
I: [pulseaudio] module.c: Loaded "module-combine" (index: #9; argument: "").
I: [pulseaudio] module.c: Loaded "module-gconf" (index: #10; argument: "").
I: [pulseaudio] module-default-device-restore.c: Saved default sink 'ladspa_output.mbeq_1197.mbeq' not existent, not restoring default sink setting.
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module-default-device-restore.c: Restored default source 'alsa_output.pci-0000_00_1b.0.analog-stereo.monitor'.
I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #14; argument: "").
D: [pulseaudio] module-suspend-on-idle.c: Sink combined becomes idle, timeout in 5 seconds.
I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.0/modules/module-console-kit.so': success
I: [pulseaudio] client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: [pulseaudio] module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: [pulseaudio] module.c: Loaded "module-console-kit" (index: #16; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.0/modules/module-systemd-login.so': failure
I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #17; argument: "").
I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #18; argument: "").
I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #19; argument: "").
I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #20; argument: "").
D: [pulseaudio] module-ladspa-sink.c: Using default input ladspa port mapping
D: [pulseaudio] module-ladspa-sink.c: Using default output ladspa port mapping
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=16777216, tlength=0, base=8, prebuf=1, minreq=1 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=16777216, tlength=16777216, base=8, prebuf=8, minreq=8 maxrewind=0
D: [pulseaudio] module-ladspa-sink.c: Module: mbeq_1197
D: [pulseaudio] module-ladspa-sink.c: Label: mbeq
D: [pulseaudio] module-ladspa-sink.c: Unique ID: 1197
D: [pulseaudio] module-ladspa-sink.c: Name: Multiband EQ
D: [pulseaudio] module-ladspa-sink.c: Maker: Steve Harris <steve@plugin.org.uk>
D: [pulseaudio] module-ladspa-sink.c: Copyright: GPL
D: [pulseaudio] module-ladspa-sink.c: Port 0 is control: 50Hz gain (low shelving)
D: [pulseaudio] module-ladspa-sink.c: Port 1 is control: 100Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 2 is control: 156Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 3 is control: 220Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 4 is control: 311Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 5 is control: 440Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 6 is control: 622Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 7 is control: 880Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 8 is control: 1250Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 9 is control: 1750Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 10 is control: 2500Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 11 is control: 3500Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 12 is control: 5000Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 13 is control: 10000Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 14 is control: 20000Hz gain
D: [pulseaudio] module-ladspa-sink.c: Port 15 is input: Input
D: [pulseaudio] module-ladspa-sink.c: Port 16 is output: Output
D: [pulseaudio] module-ladspa-sink.c: Ignored port latency
D: [pulseaudio] module-ladspa-sink.c: Will run 2 plugin instances
D: [pulseaudio] module-ladspa-sink.c: Binding 5.300000 to port 50Hz gain (low shelving)
D: [pulseaudio] module-ladspa-sink.c: Binding 2.600000 to port 100Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding 2.600000 to port 156Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -8.500000 to port 220Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -10.500000 to port 311Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -11.200000 to port 440Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -16.000000 to port 622Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -14.700000 to port 880Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -6.600000 to port 1250Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -5.700000 to port 1750Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding -3.000000 to port 2500Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding 3.000000 to port 3500Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding 6.700000 to port 5000Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding 7.300000 to port 10000Hz gain
D: [pulseaudio] module-ladspa-sink.c: Binding 7.300000 to port 20000Hz gain
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module-device-restore.c: Restoring volume for sink ladspa_output.mbeq_1197.mbeq.
I: [pulseaudio] module-device-restore.c: Restoring mute state for sink ladspa_output.mbeq_1197.mbeq.
I: [pulseaudio] sink.c: Created sink 2 "ladspa_output.mbeq_1197.mbeq" with sample spec float32le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     device.master_device = "combined"
I: [pulseaudio] sink.c:     device.class = "filter"
I: [pulseaudio] sink.c:     device.ladspa.module = "mbeq_1197"
I: [pulseaudio] sink.c:     device.ladspa.label = "mbeq"
I: [pulseaudio] sink.c:     device.ladspa.name = "Multiband EQ"
I: [pulseaudio] sink.c:     device.ladspa.maker = "Steve Harris <steve@plugin.org.uk>"
I: [pulseaudio] sink.c:     device.ladspa.copyright = "GPL"
I: [pulseaudio] sink.c:     device.ladspa.unique_id = "1197"
I: [pulseaudio] sink.c:     device.description = "LADSPA Plugin Multiband EQ on Simultaneous output to Built-in Audio Analog Stereo"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card"
I: [pulseaudio] source.c: Created source 2 "ladspa_output.mbeq_1197.mbeq.monitor" with sample spec float32le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of LADSPA Plugin Multiband EQ on Simultaneous output to Built-in Audio Analog Stereo"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     device.icon_name = "audio-input-microphone"
D: [pulseaudio] module-intended-roles.c: Not setting device for stream LADSPA Stream, because already set.
I: [pulseaudio] sink-input.c: Trying to change sample rate
I: [pulseaudio] sink-input.c: Resampling enabled to 44100 Hz
I: [pulseaudio] module-stream-restore.c: Restoring volume for sink input sink-input-by-media-role:filter.
D: [pulseaudio] module-suspend-on-idle.c: Sink combined becomes busy.
I: [pulseaudio] resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: [pulseaudio] resampler.c: Using resampler 'copy'
I: [pulseaudio] resampler.c: Using float32le as working format.
D: [pulseaudio] memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
D: [pulseaudio] memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
I: [pulseaudio] sink-input.c: Created input 1 "LADSPA Stream" on combined with sample spec float32le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink-input.c:     media.name = "LADSPA Stream"
I: [pulseaudio] sink-input.c:     media.role = "filter"
I: [pulseaudio] sink-input.c:     module-stream-restore.id = "sink-input-by-media-role:filter"
D: [pulseaudio] module-device-restore.c: Could not set format on sink ladspa_output.mbeq_1197.mbeq
D: [pulseaudio] module-suspend-on-idle.c: Sink ladspa_output.mbeq_1197.mbeq becomes idle, timeout in 5 seconds.
D: [combine] module-ladspa-sink.c: Requesting rewind due to state change.
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module.c: Loaded "module-ladspa-sink" (index: #21; argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=combined plugin=mbeq_1197 label=mbeq control=5.3,2.6,2.6,-8.5,-10.5,-11.2,-16.0,-14.7,-6.6,-5.7,-3.0,3.0,6.7,7.3,7.3").
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] main.c: Got org.PulseAudio1!
D: [pulseaudio] main.c: Got org.pulseaudio.Server!
I: [pulseaudio] main.c: Daemon startup complete.
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
D: [pulseaudio] protocol-native.c: Protocol version: remote 26, local 26
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for python2.7
D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/python2.7.desktop.
I: [pulseaudio] module.c: Unloading "module-bluetooth-discover" (index: #6).
I: [pulseaudio] module.c: Unloaded "module-bluetooth-discover" (index: #6).
D: [pulseaudio] module-console-kit.c: dbus: interface=(null), path=(null), member=(null)
I: [pulseaudio] module-suspend-on-idle.c: Sink ladspa_output.mbeq_1197.mbeq idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink ladspa_output.mbeq_1197.mbeq is 0x0004, suspending
D: [combine] sink-input.c: Requesting rewind due to corking
D: [pulseaudio] module-suspend-on-idle.c: Sink combined becomes idle, timeout in 5 seconds.
D: [pulseaudio] module-combine-sink.c: [alsa_output.pci-0000_00_1b.0.analog-stereo] total=199.91ms sink=199.91ms 
I: [pulseaudio] module-combine-sink.c: [combined] avg total latency is 199.91 msec.
I: [pulseaudio] module-combine-sink.c: [combined] target latency is 199.91 msec.
I: [pulseaudio] module-combine-sink.c: [alsa_output.pci-0000_00_1b.0.analog-stereo] new rate is 44100 Hz; ratio is 1.000; latency is 199.91 msec.
I: [pulseaudio] module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink combined is 0x0004, suspending
D: [alsa-sink] alsa-sink.c: hwbuf_unused=0
D: [alsa-sink] alsa-sink.c: setting avail_min=15502
D: [alsa-sink] alsa-sink.c: Requested volume: 0: 100% 1: 100%
D: [alsa-sink] alsa-sink.c:            in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] alsa-sink.c: Got hardware volume: 0: 100% 1: 100%
D: [alsa-sink] alsa-sink.c:               in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] alsa-sink.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: [alsa-sink] alsa-sink.c:                      in dB: 0: 0.00 dB 1: 0.00 dB
D: [alsa-sink] sink.c: Volume not changing
D: [alsa-sink] alsa-sink.c: Requested to rewind 65536 bytes.
D: [alsa-sink] alsa-sink.c: Limited to 34960 bytes.
D: [alsa-sink] alsa-sink.c: before: 8740
D: [alsa-sink] alsa-sink.c: after: 8740
D: [alsa-sink] alsa-sink.c: Rewound 34960 bytes.
D: [alsa-sink] sink.c: Processing rewind...
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [alsa-sink] sink.c: latency = 1386
D: [alsa-sink] source.c: Processing rewind...
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
I: [pulseaudio] sink-input.c: Freeing input 0 "Simultaneous output on Built-in Audio Analog Stereo"
I: [pulseaudio] module-combine-sink.c: Device suspended...
I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1b.0.analog-stereo is 0x0004, suspending
I: [alsa-sink] alsa-sink.c: Device suspended...
I: [pulseaudio] core.c: All sinks and sources are suspended, vacuuming memory
D: [pulseaudio] reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
```

---

