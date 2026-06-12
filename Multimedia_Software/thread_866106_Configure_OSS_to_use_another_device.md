---
title: "Configure OSS to use another device"
date: 2008-07-21
forum: Multimedia Software
---

### Post by dhondu on 2008-07-21
Hi,
IO am reposting because the last thread died.

I installed OSS to get my creative Xtremegamer sound card working. My motherboard has an nvidia chipset for audio which was working fine with ALSA.

I set the sound preferences under the system menu to use OSS for playback,movies, system sounds etc. But when i play an mp3 or test the system sounds I hear nothing on my speakers (they are connected to the creative sound card). If i connect them to the motherboard nvidia socket, everything works fine.

Does this mean OSS is using the motherboard chipset just like ALSA was,is there a way to get OSS to use my creative sound card instead. My BIOS has no option for turning off onboard sound.

thanks,

The ossinfo command gives the following output.

Version info: OSS 4.0 (b1016/200806162356) (0x00040003)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Chunnu)

Number of audio devices: 4
Number of audio engines: 9
Number of mixer devices: 2


Device objects
0: osscore0 OSS core services
1: ich0 Nvidia nForce2 interrupts=28024 (28024)
2: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=66168 (6616
PCI device 1102:0005, subdevice 1102:0031
3: ossusb0 USB audio core services


Mixer devices
0: ICH AC97 Mixer (ALC650) (Mixer 0 of device object 1)
1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)

Audio devices
Nvidia nForce2 /dev/oss/ich0/pcm0 (device index 0)
Nvidia nForce2 S/PDIF out /dev/oss/ich0/spdout (device index 1)
Sound Blaster X-Fi (SB073x) output /dev/oss/sbxfi0/pcm0 (device index 2)
Sound Blaster X-Fi (SB073x) input /dev/oss/sbxfi0/pcmin0 (device index 3)
dhondu is online now Report Post   	Edit/Delete Message

---

### Post by sunkenpirate on 2008-11-16
I know. The same thing happens to me too.

I have a xtrememusic card. The output for my command ossinfo is as follows:

Version info: OSS 4.1 (b rc2/200811161219) (0x00040090) 
Hg revision: changeset: 516:1e608bc45947, tag: tip, date: Thu Nov 13 09:05:03 2008 +0200, summary: Some ich/ac97 changes
Platform: Linux/i686 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 (gaurav-desktop)

Number of audio devices:	9
Number of audio engines:	17
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 Intel HD Audio interrupts=157157 (157157)
    HD Audio controller Intel HD Audio
    Vendor ID    0x808627d8
    Subvendor ID 0x80860420
     Codec  2: STAC9227X (0x83847618/0x80860420)
 2: oss_sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=883573 (883573)
    PCI device 1102:0005, subdevice 1102:0021
 3: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio STAC9227X (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB046x/067x (Mixer 0 of device object 2)

Audio devices
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 2)
HD Audio rec input1-mux           /dev/oss/oss_hdaudio0/pcmin0  (device index 3)
HD Audio rec input2-mux           /dev/oss/oss_hdaudio0/pcmin1  (device index 4)
HD Audio rec input3-mux           /dev/oss/oss_hdaudio0/pcmin2  (device index 5)
HD Audio rec spdifin              /dev/oss/oss_hdaudio0/spdin0  (device index 6)
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/oss_sbxfi0/pcm0  (device index 7)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/oss_sbxfi0/pcmin0  (device index 8)

---

### Post by sunkenpirate on 2008-11-16
I do know, however how you can enable audio in vlc media player and mplayer.


In vlc media player, go to Tools=>Preferences=>Audio
Under output, go to the device option and paste the following there: /dev/oss/oss_sbxfi0/pcm0

Do the same for mplayer and you can get sound in both the multimedia players for watching movies and listening to music. You can't however, get the sounds like system sounds, or maybe from a video playing in youtube on your browser, or for anything else for that matter.

---

