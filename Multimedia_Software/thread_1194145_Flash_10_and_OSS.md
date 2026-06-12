---
title: "Flash 10 and OSS"
date: 2009-06-22
forum: Multimedia Software
---

### Post by Magick93 on 2009-06-22
Hi all

I have no sound with Flash player 10 and OSS. I am running ubuntu 9.04.

I can play flash from youtube in Totem - and it does have sound. But not in firefox.

I have searched extensively but cannot find a solution.

Anyone have any ideas?

---

### Post by starcraft.man on 2009-06-22
Why using OSS? I assume the reason Totem is working with sound and flash is because it's piping audio through a different audio system, likely alsa or pulseaudio. I recommend you go to your sound panel under System > Prefs and change from the autodetect to one of those. Change all entries listed as sound playback, you can test if it works by the test button.

If that isn't it, a very curious problem indeed. I mean clearly flash works cuz you can play youtube clips in the totem browser...

---

### Post by Magick93 on 2009-06-22
I'm using OSS4 because that has built in support for my soundcard - Creative X-fi.

And Totem is also using OSS.

I noticed that this is a known and unfixed bug.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/291371](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/291371)

---

### Post by sanumala on 2009-06-22
If you are using ubuntu 64 bit try reinstalling flash using the following tutorial it helps a lot
[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

---

### Post by LKjell on 2009-06-22
Hi try to remove all package with flash and purge them. Then install it again. I've tested OSSv4 before and flash in firefox works great. And remember it might be the volume slider on the flash player in firefox that is muted or that you have muted firefox. If I remember correctly the OSSv4 mixer name is ossxmixer.

---

