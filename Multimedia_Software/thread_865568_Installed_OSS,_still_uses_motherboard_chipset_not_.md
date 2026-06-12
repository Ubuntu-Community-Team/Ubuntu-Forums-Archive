---
title: "Installed OSS, still uses motherboard chipset not sound card"
date: 2008-07-20
forum: Multimedia Software
---

### Post by dhondu on 2008-07-20
Hi,
I am a new Ubuntu 8.04 user with very little linux experience 
I installed OSS to get my creative Xtremegamer sound card working. My motherboard has an nvidia chipset for audio which was working fine with ALSA. 
 
I set the sound preferences under the system menu to use OSS for playback,movies, system sounds etc. But when i play an mp3 or test the system sounds I hear nothing on my speakers (they are connected to the creative sound card). If i connect them to the motherboard nvidia socket, everything works fine.

Does this mean OSS is using the motherboard chipset just like ALSA was,is there a way to get OSS to use my creative sound card instead.

thanks,

The ossinfo command gives the following output.

Version info: OSS 4.0 (b1016/200806162356) (0x00040003) 
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Chunnu)

Number of audio devices:	4
Number of audio engines:	9
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: ich0 Nvidia nForce2 interrupts=28024 (28024)
 2: sbxfi0 Sound Blaster X-Fi (SB073x) interrupts=66168 (66168)
    PCI device 1102:0005, subdevice 1102:0031
 3: ossusb0 USB audio core services


Mixer devices
 0: ICH AC97 Mixer (ALC650) (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB073x) (Mixer 0 of device object 2)

Audio devices
Nvidia nForce2                    /dev/oss/ich0/pcm0  (device index 0)
Nvidia nForce2 S/PDIF out         /dev/oss/ich0/spdout  (device index 1)
Sound Blaster X-Fi (SB073x) output  /dev/oss/sbxfi0/pcm0  (device index 2)
Sound Blaster X-Fi (SB073x) input  /dev/oss/sbxfi0/pcmin0  (device index 3)

---

### Post by fenian on 2008-07-20
Disable the onboard sound from the BIOS.

---

### Post by dhondu on 2008-07-20
My bios has no option to turn off the onboard sound

---

### Post by dhondu on 2008-07-21
Anyone, Please ?
I have already given up on trying to get my ATI Radeon X1600 AGP card to get to work, if I cant get my sound card to work either, then Ubuntu pretty much renders itself useless

---

