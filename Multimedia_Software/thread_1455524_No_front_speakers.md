---
title: "No front speakers"
date: 2010-04-16
forum: Multimedia Software
---

### Post by genux05 on 2010-04-16
I have no sound coming out of my front speakers, and I also am using a ALC883 .. it is coming out of my rear speaker on my laptop.

The laptop is a ACER 9815, it has 3 speakers ( one bass at the rear and two at the front)

Here is the output of the util_alsa-info.sh for me

[http://www.alsa-project.org/db/?f=8b...53da35d6aad057]("http://www.alsa-project.org/db/?f=8b6a09c7a40a083810c5561eb453da35d6aad057")

any advice ? I have tired different things but nothing appears to help.

---

### Post by Yellow Pasque on 2010-04-16
A couple things:
- Here is someone reporting success on an acer 9815 using the 'acer' model keyword: [http://ubuntuforums.org/showpost.php?p=4869649](http://ubuntuforums.org/showpost.php?p=4869649)
```
kdesudo kate /etc/modprobe.d/alsa-base.conf
```
Copy/paste this line onto the end of the file:
```
options snd-hda-intel model=acer
```
Save. Quit. Reboot.

-Your ALSA driver version is mismatched to the library version, but maybe that's how Lucid is (I'll check the next time I'm in Ubuntu).

---

### Post by genux05 on 2010-04-16
cannot f****ing believe it, could have sworn that I tried that before.. just tried that again and it is WORKING!!.. 

thanks thanks thanks thanks thanks very very very much..

could I just ask one more question, the sound appears to be slightly lower not sure if it is because it is now powering 3 speakers instead of 1.. but it *sounds* (:lolflag:) not as loud.. but if that is not answered I am not that bothered to be honest.. really could not believe it when it started up.. 

soo ooo happy.. thanks again. thanks

---

