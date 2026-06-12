---
title: "DVD not playing or coping"
date: 2009-06-16
forum: Multimedia Software
---

### Post by bgsteiner on 2009-06-16
I can not play a DVD on my computer the built in DVD player that came with ubuntu 9.04 said i need the appropriate plug-ins to play the DVD the same goes for coping DVD's that are not protected please help

---

### Post by Oats on 2009-06-24
I was having the same problem trying to play encrypted DVDs on my fresh install of 9.04.

The problem was fixed when I installed libdvdcss2.

To get libdvdcss2 without going to third party repositories, check out this Documentation:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

It tells you to first install libdvdread4.  On my system, libdvdread4 was already installed.  When I ran the second command, it told me that libdvdcss2 was being installed.  After a reboot, MPlayer worked on the previously offending dvd.

Hope this helps you.

---

### Post by magmon on 2009-06-25
Try using vlc media player. Ive found that it can play the widest range of media files, and its free.

---

### Post by zezerbing on 2009-07-02
I have this same problem.libdvdcss2 is installed. I checked it twice. The movie loads ant the title starts for a second and just shuts off.

---

