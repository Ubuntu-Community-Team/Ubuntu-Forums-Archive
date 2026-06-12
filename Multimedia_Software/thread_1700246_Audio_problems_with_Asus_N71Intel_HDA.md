---
title: "Audio problems with Asus N71/Intel HDA"
date: 2011-03-04
forum: Multimedia Software
---

### Post by CYcolone on 2011-03-04
Howdy Ubuntu community. I recently decided to switch my laptop (Asus N71Jq) from Windows 7 to Ubuntu only, committed to finally familiarizing myself with GNU/Linux. I installed Ubuntu 10.10 64-bit, but have been struggling for the past couple of days to get the Intel HDA sound controller working fully.

After a fresh install of Ubuntu 10.10, the speakers, headphones jacks, and microphone jack all work great. The only problem is that I can't record from the internal microphone. I can listen to it by unmuting the mic using a mixer, but all recording applications like arecord only pick up the microphone jack.

I can get both microphones working properly if I add "options snd-hda-intel model=auto" to the /etc/modprobe.d/alsa-base.conf file. This however breaks one of the two headphones jacks, and makes it so the tiny subwoofer on the bottom of the laptop to not mute when headphones are plugged in. I've tinkered with all the other model settings, but auto works the best.

Essentially, it would be nice if I could combine the output channels of the default setting, with the input channels of the model=auto setting. The laptop uses an Intel 5 series chipset, with Intel HDA audio, using the Realtek ALC663 codec. If anyone has any advice for me, I would really appreciate it.

Here's the alsa-info.sh outputs using each of the two settings:
alsa-info.sh: [http://pastebin.com/1NJXbpLQ](http://pastebin.com/1NJXbpLQ)
alsa-info.sh (using model=auto): [http://pastebin.com/AJyQb0cn](http://pastebin.com/AJyQb0cn)

---

### Post by CYcolone on 2011-03-04
Here's a screenshot of the mixer using the default settings, without the model=auto line. The only recordable line is the Capture line. It however only picks up the Mic line, not the IntMic line. I can only listen to the IntMic line.

[IMG]http://dl.dropbox.com/u/114089/alsamixer.png[/IMG]

---

### Post by CYcolone on 2011-03-17
I still have not gotten anywhere with this issue. If anyone has any ideas, I'd appreciate it.

---

### Post by *michi* on 2011-07-20
Hi CYcolone,

I have the same problem. Have you found a solution? Either I can't use the microphones or it sounds like a tin...

Found this model options ([http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)) , but hadn't time to test them all:


```
ALC662/663/272
==============
  3stack-dig    3-stack (2-channel) with SPDIF
  3stack-6ch     3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig     6-stack with SPDIF
  lenovo-101e     Lenovo laptop
  eeepc-p701    ASUS Eeepc P701
  eeepc-ep20    ASUS Eeepc EP20
  ecs        ECS/Foxconn mobo
  m51va        ASUS M51VA
  g71v        ASUS G71V
  h13        ASUS H13
  g50v        ASUS G50V
  asus-mode1    ASUS
  asus-mode2    ASUS
  asus-mode3    ASUS
  asus-mode4    ASUS
  asus-mode5    ASUS
  asus-mode6    ASUS
  asus-mode7    ASUS
  asus-mode8    ASUS
  dell        Dell with ALC272
  dell-zm1    Dell ZM1 with ALC272
  samsung-nc10    Samsung NC10 mini notebook
  auto        auto-config reading BIOS (default)
```

---

### Post by CYcolone on 2012-03-29
Issue has finally been resolved with ALSA 1.0.25. Thank you ALSA contributors!

---

