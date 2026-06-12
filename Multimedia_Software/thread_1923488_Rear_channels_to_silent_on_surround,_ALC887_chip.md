---
title: "Rear channels to silent on surround, ALC887 chip"
date: 2012-02-10
forum: Multimedia Software
---

### Post by carchaias on 2012-02-10
Hello, could you help me. I could not get surroundsound running. It is  an Asus A5ION board with ALC887 chip onboard. It has 3 jacks on back  that should offer 5.1 sound according to the manual of the board and 2  jacks on front panel.  Speaker-test -D surround51 -c 6 gives me sound on  LF,Center,RF and very low volume sound on RR,RL with some mumbel from  the sub, sub test mubles sub. In alsamixer the surround mixer affect backspeakers and sub while the chanels are on RR and RL. Here comes my alsatest  result:

[http://www.alsa-project.org/db/?f=21...4ab43f6e583ca5]("http://www.alsa-project.org/db/?f=21a09c6037cc84a08c1650f5684ab43f6e583ca5")

There is an entry in alsa-base.conf

options snd-hda-intel model=auto

  I tried with all different models here - with no effekt to volume of the back channel.


I even tryed with hda-jack-retask and it works but always the back channels , no matter wich speaker they are switched to are much to silent.  I swaped them to test and with hda-jack-retask i swiched to the front jacks also. Its from the channel, not from the speakers or the jacks.

Any ideas are welcome..

---

### Post by Yellow Pasque on 2012-02-10
Have you tried playing with hdaanalyzer? Maybe some amp is muted..
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

---

### Post by carchaias on 2012-02-12
Hm, I dont know what to do with all the stuff  hda-analyzer shows.:confused: That is quite far inside the chip or not.
mixer, pins, vendors - i understand nothing.

---

