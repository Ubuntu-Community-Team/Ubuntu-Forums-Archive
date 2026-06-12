---
title: "Sound card not working 10.04"
date: 2010-06-06
forum: Multimedia Software
---

### Post by timme_v on 2010-06-06
Hey guys, I'd just like to say that I am a completely new to linux and that so far its quite fun!

I know there are heaps of sound problem threads around here, and I've been through them all and I still can't my sound to work.

I have the motherboards onboard audio which works perfectly when I plug in speakers.

I want to use my Creative Xfi xtreme audio. When I select it as the output for my sound, it freezes my audio players and firefox when I try.

I don't know what the following means, but this is what I gathered people need from other threads.



tim@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux


tim@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



tim@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  6 2010 for kernel 2.6.32-22-generic (SMP).




tim@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#2 <==
Codec: Realtek ALC889A

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

==> /proc/asound/card2/codec#1 <==
Codec: Creative CA0110-IBG



Sorry for being ignorant, but I've really tried to get this to work and I can't. As you can see I've upgraded ALSA but I'm not sure if I did it correctly or anything.

Thanks for any help.

---

### Post by AgentWD-40 on 2010-06-07
I'd really like to get the same X-Fi card for my car PC, but not if it's this much trouble. I heard a rumor about Sound Blaster X-Fi support for Lucid, but I guess it doesn't apply to this card...? Looking through the supported cards list for ALSA ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")) I was able to find "X-Fi Xtreme Audio" in the list, but it doesn't say whether it's supported or unsupported. Does anybody have any fixes for this problem?

---

