---
title: "Sound problem in Feisty and wierd outputs. (Desperate!)"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by davidblund on 2007-05-15
I've been searching the forum like mad after a solution to my sound problem in Feisty. But I can't find anything that helps. So please forgive me if I missed out on some already existing thread.

I've done everything mentioned in this guide:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
Unfortunately it didn't solve my problem.

Yesterday I had sound from both movies and MP3-music in various multimedia software, I had to play around a lot with the mixer but eventually the sound seemed to work. Today it's dead quite. And I used the command "sudo alsactl store 1" to save mixer configuration yesterday. I've removed and reinstalled alsa-base a couple of times with no progress.

The device of choice is an M-Audio Audiophile. I'd appreciate If the internal card can be completely disabled,

Sorry for the swedish output language in the following text. Hope it's useful anyway.

_"aplay -l" outputs:_
[FONT="System"]**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Underordnade enheter: 0/1
  Underordnad enhet #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
[/FONT]

I noticed that both the NVidia CK804 and ICE1712 says "device 0". Don't know if that's strange.

_"lspci" output:_
[FONT="System"]lspci | grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
[/FONT]
[U]
"cat /proc/asound/modules" outputs:[/U]
[FONT="System"]0 snd_intel8x0
 1 snd_ice1712
[/FONT]


I'm endlessly thankful for any tiny advice that might help! I really don't want to boot XP again... ever :P

// David, Stockholm

---

### Post by davidblund on 2007-05-15
Thank god. This thread saved me:
[http://ubuntuforums.org/showthread.php?t=418360&highlight=sound+feisty](http://ubuntuforums.org/showthread.php?t=418360&highlight=sound+feisty)

Just stumbled upon it.
Sorry for posting a new thread...
Please DELETE.

// D

---

