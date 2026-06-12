---
title: "OSS4 sound showing in ossxmix but no output sound please help"
date: 2008-10-11
forum: Multimedia Software
---

### Post by H4ck3rz on 2008-10-11
Hi iv have installed OSS4 & instalation went fine with no erros now my problem is i still have no sound in the ossxmix it shows ther is sound playing when tested a cd or any kind of sound test the ouput is set to my soundblaster X-Fi card i in the ossxmix nothing is muted also in sound prefrences nothing is muted i was just wondering if any one eles if having this problem or if some one no's how to solve this here is my ossinfo 
```
h4ck3rz@h4ck3rz-desktop:~$ osstest
Sound subsystem and version: OSS 4.1 (b rc2/200810091939) (0x00040090)
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/oss_sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (UAA) output
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 473407.00 Hz (886.26%)> 
/dev/oss/oss_sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (UAA) input
- Skipping input only device

*** All tests completed OK ***
h4ck3rz@h4ck3rz-desktop:~$ ossinfo
Version info: OSS 4.1 (b rc2/200810091939) (0x00040090) 
Hg revision: changeset: 473:d79ebde9987e, tag: tip, date: Tue Oct 07 17:50:26 2008 +0300, summary: Suported rate fix for envy24
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 (h4ck3rz-desktop)

Number of audio devices:	2
Number of audio engines:	6
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi (UAA) interrupts=4310 (4310)
    PCI device 1102:0005, subdevice 1102:6002
 2: oss_usb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (UAA) output   /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (UAA) input    /dev/oss/oss_sbxfi0/pcmin0  (device index 1)
h4ck3rz@h4ck3rz-desktop:~$ 

```could some one please help me with this i dont wanna go back to vista i have started to really like linux other than this sound problem 
but it is really anoying me

---

### Post by modmadmike on 2009-11-07
HAd the same problem and had to revert to PulseAudio because my Xonar D2X was PCI-E and the drivers only work with the Xonar D2 (same card just PCI).

---

