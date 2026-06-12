---
title: "aspire one speakers/headphones"
date: 2009-02-14
forum: Multimedia Software
---

### Post by notatoad on 2009-02-14
is there a way to make the aspire one turn off the speakers when headphones are plugged in?  I've got the sickboy kernel installed on ubuntu 8.10.

even if i have to change the output manually, that would be fine.  i've got a long bus ride tomorrow and need to be able to watch movies without pissing everybody off :p

---

### Post by seagolfer on 2009-02-24
add this line:
options snd-hda-intel model=acer_wmi
to the end of /etc/modprobe.d/alsa-base
This solves the problem on my Aspire One, but I'm running a different Debian distro (Sidux) so this solution may not be directly transferrable. If you have the alsa-base file and edit it as root it should work.  If not no harm done, just delete the line.

This has now changed.  Put the above line in /etc/modprobe.d/sound

---

