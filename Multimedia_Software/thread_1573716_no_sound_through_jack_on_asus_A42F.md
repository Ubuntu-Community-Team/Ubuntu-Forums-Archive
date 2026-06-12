---
title: "no sound through jack on asus A42F"
date: 2010-09-13
forum: Multimedia Software
---

### Post by walkrue on 2010-09-13
okay, maybe there some thread asking this but still not work for me

i'm using asus A42F(K42F) and ubuntu 10.04 netbook edition,
sound from internal speaker work perfectly, but when headphone/ earphone plugged, nothing come out.

what I already done is upgrading alsa script written here :
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

but stopped in checking /etc/modprobe.d/alsa-base.conf
it says Look for options snd-hda-intel index=-2, but the line doesn't exist, 
I tried add the line with options snd-hda-intel index=-2 model=basic/auto/eeepc-p703/eeepc-901 
but the result is no sound (both on internal speaker and jack) when streaming from youtube/ metacafe, 
but when using rhythmbox the sound come from internal speaker, but not from jack
ALC269
so I delete the line for now

and this is the output for my alsa-info-script output
[http://www.alsa-project.org/db/?f=ba919848aa66acb32a4812649f8735be10e7631f](http://www.alsa-project.org/db/?f=ba919848aa66acb32a4812649f8735be10e7631f)

did I missed something?
thx before

---

### Post by walkrue on 2010-09-13
any help?

---

### Post by quvil on 2010-09-14
I have a similar problem - when headphones are connected, a sound continues to come from internal speakers and not from headphones (on Dell Inspiron 1525). After two days of troubleshooting I booted up Windows and found out that the problem exists there as well. Which means this is probably a hardware problem.

Therefore, before you start looking for a solution for Linux, I would advice you to check whether this is not a hardware problem - just boot up Windows and see whether things work there.

---

### Post by walkrue on 2010-09-15
> **quvil said:**
> I have a similar problem - when headphones are connected, a sound continues to come from internal speakers and not from headphones (on Dell Inspiron 1525). After two days of troubleshooting I booted up Windows and found out that the problem exists there as well. Which means this is probably a hardware problem.

Therefore, before you start looking for a solution for Linux, I would advice you to check whether this is not a hardware problem - just boot up Windows and see whether things work there.

well, I already think its a hardware failure, but its work fine in windows 7

thank for telling :D

---

