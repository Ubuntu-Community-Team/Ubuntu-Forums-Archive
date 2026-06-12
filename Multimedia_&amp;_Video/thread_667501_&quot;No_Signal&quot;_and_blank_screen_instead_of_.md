---
title: "&quot;No Signal&quot; and blank screen instead of usplash"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by Starlight on 2008-01-14
Hello!

I've had this problem ever since I installed Gutsy (I've had Feisty before and it worked well, but I decided to do a fresh install of Gutsy instead of upgrading Feisty) and I thought it's some temporary problem which would be fixed with some update, but I still have it, so I guess it's a problem with my computer. Instead of the Kubuntu loading screen I get a "No Signal" error, and then it goes blank for the whole boot process. When it finished booting, it displays the login page and everything's well after that, but there's no logo and progress bar while my Kubuntu is booting (or when it's shutting down). I've tried using startupmanager to change usplash resolution, and I've tried a few of them, but it didn't change anything. Does anyone else have the same problem? Is there some way to fix it? I have a GeForce 8400 GS video card...

---

### Post by steeleyuk on 2008-01-14
Usually 'No signal' means that its a screen resolution problem or a frequency problem (often the frequency is too high).

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/25011](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/25011)

Seems that is a similar bug report. You could try the fix in there which is suggested but make a backup of the GRUB file before you do.

---

### Post by Starlight on 2008-01-14
Thanks, but my problem seems to be different, since I'm not using DVI... maybe I'll try that fix, though. :)

The strange thing is that before I installed Gutsy, Feisty's usplash worked well... I wonder why they replaced a working one with a bugged one...

edit: I've already tried booting with vga=791, it hasn't fixed anything...

---

### Post by steeleyuk on 2008-01-14
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/145893](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/145893)
[https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930)

Looks like it might be a case of changing the usplash resolution. The configuration file is at /etc/usplash.conf. Again, make a backup copy before changing anything. Seems like theres a few problems with the 8x00 series of Nvidia cards as well.

---

### Post by Starlight on 2008-01-14
Thanks for the links, I'm checking them out. :)

I've tried using different resolutions for usplash (1026x768, 1280x1024) and none of them worked. But I found something different in one of these bug reports, and I'm going to try that...

By the way, does usplash have some log where I can see if it gives errors?

---

