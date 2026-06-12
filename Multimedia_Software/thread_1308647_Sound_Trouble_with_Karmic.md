---
title: "Sound Trouble with Karmic"
date: 2009-10-31
forum: Multimedia Software
---

### Post by kbjr on 2009-10-31
i just upgraded to karmic and now, all of a sudden, my sound won't work. i used `bash alsa-info.sh --pastebin` ([http://pastebin.ca/1651038](http://pastebin.ca/1651038)) and found out that my alsa driver was a different version than the lib and utils. so i tried upgrading my version of alsa, went through all of the steps, and when i was done, the libs and utils were upgraded (went from 1.0.2 to 1.0.21), but the driver version still won't change. please help.

---

### Post by kbjr on 2009-10-31
i figured out what was wrong and got it to work.

the problem was because when i upgraded to karmic, i told it to keep my old /boot/grub/menu.lst file. because of this, when i booted, it wasn't booting from the right place, i had to go in and change it from '/boot/vmlinuz-2.6.28-16-generic' to '/boot/vmlinuz-2.6.31-14-generic'.

anyway, it works now. :)

---

