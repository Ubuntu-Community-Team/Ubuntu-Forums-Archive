---
title: "No Sound - Intel AD198X Chipset"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by technick on 2007-02-23
I've been fighting and fighting trying to get the sound to work on my Toshiba U205-S5002 laptop 	:evil: .  I'm running the latest Edgy Eft distro and i've installed the latest Alsa drivers from their website. Some where in the process, I think I might of damaged KDE, the Kmixer no longer loads automatically. 

Here's the list of what i've tried so far.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (I used the rc2 release of drivers)
[http://ubuntuforums.org/archive/index.php/t-208658.html](http://ubuntuforums.org/archive/index.php/t-208658.html)
[http://ubuntuforums.org/showthread.php?t=305712](http://ubuntuforums.org/showthread.php?t=305712)

No luck with any of them :( 

nick@cuba:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nick@cuba:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.14rc2.
Compiled on Feb 22 2007 for kernel 2.6.17-11-generic (SMP).
nick@cuba:~$ lsmod | grep intel
snd_hda_intel          22936  1 
snd_hda_codec         209664  1 snd_hda_intel
snd_pcm                85764  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    62984  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp


Any help would be GREATLY appreciated.

---

### Post by deadgobby on 2007-02-23
check Ubies Wiki and see if you can find your answer. If the live CD ran fine and heard sound. It should of worked.
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=Toshiba+&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=Toshiba+&titlesearch=Titles)
Gobby

---

### Post by mushuweb on 2008-04-27
Hi, 

It worked for me with Ubuntu Hardy Heron (x64) !! (digital/PCM output)

> 
lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P5B
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fbbfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

1) sudo modprobe snd-hda-intel
2) sudo nano /etc/modules -> add "snd-hda-intel"
3) sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
4) sudo apt-get install linux-sound-base alsa-base alsa-utils
5) sudo apt-get install gdm ubuntu-desktop (ubuntu gnome only)

More informations : 
[LIST]
[http://ubuntu-forum.com/showthread.php?t=205449]("http://ubuntu-forum.com/showthread.php?t=205449")[/LIST][LIST][http://doc.ubuntu-fr.org/audio_intel_hda]("http://doc.ubuntu-fr.org/audio_intel_hda")
[/LIST]

In Alsa Mixer (Gnome)->Settings, check IEC958 - Playback Source, then in Options->ADC1->PCM

Hope that helps,

---

