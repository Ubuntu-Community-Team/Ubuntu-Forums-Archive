---
title: "Using Focusrite 6i6 on Ubuntu 14.04"
date: 2015-03-22
forum: Multimedia Software
---

### Post by xigen on 2015-03-22
My Focusrite 2i2 works out of the box.   I simply go to settings -> sound 
and choose Analog Output  Scarlett 2i2 USB
[ATTACH=CONFIG]260829[/ATTACH]


When I try to use my Focusrite 6i6  the only output is  HDMI/DisplayPort3  GK 107 HDMI Audio Controller


From a lot of reading it looks like:
1) Under 3.13.x Pulse audio does not correctly recognize the 6i6

2) Under 3.16.x, 3.18.x, and 3.19.x  - 6i6 is correctly recognized.  Unfortunately, if you are using any propriatary (nvidia) drivers - they might break.
[http://linuxg.net/how-to-install-kernel-3-18-6-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/]("http://linuxg.net/how-to-install-kernel-3-18-6-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/")

3) Under KXstudio -- 6i6 just works.   [http://unix.stackexchange.com/questions/89098/ideas-how-to-get-my-usb-audio-interface-to-work-with-linux]("http://unix.stackexchange.com/questions/89098/ideas-how-to-get-my-usb-audio-interface-to-work-with-linux")


Soooooo

**1:question)**  Is there a way you see to get pulse to correctly identify my 6i6 in ubuntu 14.04 64?

**2:question) **I have built a 3.18 kernel and attempted to use it with my system.    Unfotunately, my graphics do not work correctly.  [http://ubuntuforums.org/showthread.php?t=2270302]("http://ubuntuforums.org/showthread.php?t=2270302")       Is there a clear way to get graphics to work under 13.18.x?  And ... will 13.18.x  break a bunch of other stuff on Ubuntu 14.04?

**3:question)**    What exactly is KXstudio?  Is it an iso?  is it a set of packages I can install on 14.04?    I am a bit lost.    Could you please advise on best practices here?

---

### Post by Yellow Pasque on 2015-03-22
> I have built a 3.18 kernel and attempted to use it with my system. Unfotunately, my graphics do not work correctly.

Well, if you're not using a new enough version of the nvidia driver, it's not going to work with such a new kernel.
Get rid of the nvidia driver that you currently have installed and use the nvidia-346 driver from: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by Yellow Pasque on 2015-03-23
BTW, it might be preferable to use latest 3.19 kernel. (You can install it pre-built from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19.2-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19.2-vivid/) )
The code for the 6i6 was cleaned up a lot in 3.19: [https://github.com/torvalds/linux/commit/76b188c4b370876018e3a778ec11a94a5316dbe4](https://github.com/torvalds/linux/commit/76b188c4b370876018e3a778ec11a94a5316dbe4)

---

### Post by xigen on 2015-03-25
I agree completely.

It looks like 15.04 ships with the 3.19.x kernel as the default.
link: [http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.04-Linux-3.19]("http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.04-Linux-3.19")

Release Date:  4/23/15

Perhaps it is time to back up my system, experiment with the 3.19 kernel and wait for the official release of 15.04.

---

### Post by anotherforwork on 2015-04-06
Hi!
I try ubuntu 15.04 with 3.19.x kernel
And i see that system [COLOR=#000000]recognize focusrite 6i6
I see sound card in  alsamixer and can change master value
BUT i can't select it in GUI sound settings, and can't get some sound in that case

How we can select our focusrite 6i6 for default sound card in system work?
Is that because alsa see it, but pulseaudio don't ?

Who try this card on 15.04 system ?[/COLOR]

---

