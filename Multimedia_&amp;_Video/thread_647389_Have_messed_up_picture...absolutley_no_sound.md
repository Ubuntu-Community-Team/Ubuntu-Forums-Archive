---
title: "Have messed up picture...absolutley no sound"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by Josh C on 2007-12-22
Please help!!! 

I have been using Ubuntu Gutsy on Compaq laptop with Integrated Altec Lansing audio for about a month now.  Everything worked fine at first, but there have been several updates since the intial install and now I have issues.  

When I try to stream video from the web (i.e. YouTube, Yahoo and MSN news links), play saved video files (i.e. avi, wmv, mpeg) or listen to audio only files (i.e. mp3, flac, wav) I get no sound.  With the video files I have picture although at some point the color settings got all out of whack and I have yet to get the picture back to "normal" again, but I have absolutely no sound. 

I am very new to Linux and I am not very versed in it.  So far, I have been trolling the forums and have tried a few things.  The following is the result of some suggestions found this morning in a sticky regarding no sound.

josh@josh-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
josh@josh-laptop:~$ sudo apt-get --purge remove linux-sound base alsa-base alsa-utils
[sudo] password for josh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-sound
josh@josh-laptop:~$ sudo apt-get install linux-sound base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-sound
josh@josh-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
josh@josh-laptop:~$ grep 'audio' /etc/group
audio:x:29:josh
josh@josh-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have no clue how to interpret this information.  I also installed the VLC player, but I get no sound with that either.  The other programs that I use are Totem and  Mplayer, but none of them are working.  They all show the video playing, but have no sound.

Any help would be greatly appreciated.  I hate to thought of having to revert back to Windows.  By the way I am using a Grub-loader and have both Vista and Gutsy installed.  The sound in Vista works just fine.

Thanks for your time.  Happy holidays!!!

---

### Post by balaknair on 2007-12-23
Yeah Linux generally has issues with Intel-HDA. I had the same issues my onboard HDA card. This is what finally worked for me.

open a terminal and enter the following steps(without the quotes)

"cat /proc/asound/card0/codec#* | grep Codec"

this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A
Next find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

(the alsa-config should also be on your system at usr/src/(your kernel version)/sound/alsa/alsa-configuration.txt)

in that page find your card model and check the details given
eg
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)


select the description that best matches your system(eg a 5.1 surround system with 6 audio-out channels/ports would be 6stack)

then go back to the terminal and type
"sudo nano /etc/modprobe.d/alsa-base"

Paste this into the last line of the file
"options snd-hda-intel model=MODEL"
replace MODEL with your model(6stack, 3stack, laptop etc.)

reboot.
if this doesn't work you might have to consider recompiling the alsa-kernel(though if you followed the ubuntuforums guide above I guess you've already tried it.
These steps are just a part of the howto guide at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I've only mentioned the steps that worked for me with the HDA-Intel card(like yours) with Gutsy 7.04, 7.10, and with Mandriva 2008- recompiling the kernel with Gutsy led to my sound card not being detected at all and I had to purge alsa and try again, that's why I mentioned just the tips that worked for me.

The video part of things I'm not that sure about(I'm a noob like you), but keep trolling the forums, you're sure to find a solution.
Lotsa luck

---

