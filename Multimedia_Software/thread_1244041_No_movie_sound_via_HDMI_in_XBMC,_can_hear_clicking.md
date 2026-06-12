---
title: "No movie sound via HDMI in XBMC, can hear clicking sound though"
date: 2009-08-19
forum: Multimedia Software
---

### Post by skdevnath on 2009-08-19
I have Asus M3A78-EM motherboard, according to the manual it has AMD 780G/SB700 chipset.
I have installed Jauntu on that.

I can hear sound over HDMI, if I use VLC. 
I can't hear music, Video sound from XBMC. However I can hear clicking, shuffling sound on my TV via HDMI on XBMC.


I tried following trick and it seems it worked, however next day morning I turn ON my PC and I see my sound issues are back

[http://ubuntuforums.org/showpost.php?p=6690552&postcount=4](http://ubuntuforums.org/showpost.php?p=6690552&postcount=4)


Please note, I am using TV for sound, not any receiver.

Here are some details of my system:


> PCI (sysfs)
  *-multimedia
       description: Audio device
       product: RS780 Azalia controller
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list> 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Please help.

---

### Post by skdevnath on 2009-08-20
Hi Folks,

I found the solution from XBMC forum. The issue was totally with XBMC, since I can use HDMI sound via VLC, aplay, even XBMC (clicking, shuffling sound). 

Audio output:	 Digital
Default audio device: hdmi (alt2 "plug:hdmi" alt3 "plughw:1,3") 
Passthrough audio device: hdmi
Downmix to stereo:	 Yes 		

I have to choose alt3 and then things just worked. (hdmi, plug:hdmi doesn't work for my mobo).

:guitar:   :popcorn:

---

