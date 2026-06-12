---
title: "Logitech keyboard multimedia keys"
date: 2008-10-25
forum: Multimedia Software
---

### Post by superjavi on 2008-10-25
Hello everybody,

I was a Debian user until last week, when I installed Ubuntu 8.10. Almost everything is very nice, I don't miss Debian very much.
Anyway, even if I consider myself an advanced user of Linux in general, I can't find why this is happenning. I hope you can help:

In Debian, my multimedia keys, on a Logitech Cordless S530 Mac worked very well. I just had to configure them graficaly using the preferences application of Gnome.
But, in Ubuntu, these keys just seem to be totally ignored by the X server or even by the kernel. They did not even appear when running xev.
For example, I press the "play" button, and xev doesn't even shows up that an event had happened (but it works with normal keys, of course).
As this happens, any attempt to configure any program is futile. These keys are simply ignored at a lower level.

Anyone please can tell me what might happen? Do I need to touch xorg.conf? I don't think so, that file is empty!!

Thank you in advance.

---

### Post by Paysan on 2009-01-25
Hello.

I've got the same probleme. The mouse of this pack is a Logitech MX600 and it works well with hidpoint [http://www.hidpoint.com/home.html](http://www.hidpoint.com/home.html) but I can't use multimedia keys of the keyboard S530.
Have you find a solution ?

I posted here details about what I've did: [http://forum.ubuntu-fr.org/viewtopic.php?id=289025](http://forum.ubuntu-fr.org/viewtopic.php?id=289025)

Thanks for help :)

---

### Post by Paysan on 2009-01-30
Problem solved after uninstalling mouseemu package.

If you use synpatic to do this, you have to switch to another console (ctrl + alt + F2) and type sudo reboot to have xorg automaticaly configure keyboard and mouse.

---

### Post by russelld on 2009-04-07
> Problem solved after uninstalling mouseemu package. 

this restored the multimedia keys on a Logitech S510 remote keyboard (lsusb lists it as: Logitech, Inc. LX710 Cordless Desktop Laser) and in turn the multimedia buttons on a Keyspan presentation remote PR-US2.  what a bonus!

multimedia keys! sweet! :guitar:

thanks so much!

---

