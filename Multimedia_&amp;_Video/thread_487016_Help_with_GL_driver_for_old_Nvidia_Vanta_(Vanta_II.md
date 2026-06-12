---
title: "Help with GL driver for old Nvidia Vanta (Vanta II) 16MB video card."
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Juicespeare1 on 2007-06-28
Hi all, 

Just joined the forum. Been using Ubuntu for several months on a couple of PC's (laptop and desktop).

Have Unix experience with HP-UX and Solaris, but my 2nd venture into Linux.

So far I have to say Ubuntu has been great. No problem with laptop, but a couple I haven't been able to solve on the desktop.

The desktop is an older IBM Netvista 6790-21U, more info here: 

[http://www-307.ibm.com/pc/support/site.wss/MIGR-39334.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-39334.html)

The problem is I want to be able to play Openarena and it requires GL in order to work. I installed the nvidia-glx-config (legacy) drivers and it works, but the screen resolution is limited to 800x600 in size.

Openarena works fine at this resolution, but I'd like to have is at least at 1024x768.

The problem is I can't upgrade the video card as the IBM case is a low profile one and requires low profile AGP and PCI cards. Also the power supply in the IBM case is 160watt and not of the standard size like a normal ATX case.

So ... what are my options?

Is what I'm trying to do even possible?

I forgot to mention I'm using Feisty 7.04 desktop version of Ubuntu.

BR
Juicespeare1

---

### Post by tseliot on 2007-06-28
did you install Nvidia's legacy driver? If yes, how did you do it?

---

### Post by Juicespeare1 on 2007-06-28
yes, I installed the legacy driver from the list of applications in the video repositories. Sorry I'm not on that system right now and can't remember what the application is called to install packages and apps.

I then ran a command something like:

sudo nvidia-glx-config enable or something like this.

I then went to restricted drivers applet and enabled/installed the nvidia legacy driver from there..

Once this was completed a reboot was needed and the system comes up in 800x600 resolution and the GL dll's appear to work.

---

