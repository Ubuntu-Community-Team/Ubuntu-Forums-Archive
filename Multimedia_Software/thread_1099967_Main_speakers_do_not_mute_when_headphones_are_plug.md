---
title: "Main speakers do not mute when headphones are plugged in"
date: 2009-03-18
forum: Multimedia Software
---

### Post by jeko82 on 2009-03-18
Hi!
I am new in Ubuntu!
I have a Fujistsu-Siemens laptop, the sound card is

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

As i wrote in the title, when I plug in the headphones, main speakers do not mute...

Is there anybody out there who can help me?!

ByE!!

---

### Post by markbuntu on 2009-03-18
You can look in here. I think that the fujitsu option will work with that laptop.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by jeko82 on 2009-03-24
I tried... but it doesn't work :-(

do i have to write 

options snd-hda-intel Fujitsu model=fujitsu 

wherever between the options in

sudo gedit /etc/modprobe.d/alsa-base

??

Thank you for the reply, anyway! :-)

---

### Post by markbuntu on 2009-03-24
no, you only need to write

options snd-hda-intel model=fujitsu

at the end of the /etc/modprobe.d/alsa-base file like it says in the directions. If that did not work you can try some of the other options. You can also go here for more extensive help with the snd-hda-intel driver

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

