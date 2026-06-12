---
title: "LIRC, Imon ffdc, lcd bug in 9.04?"
date: 2009-04-30
forum: Multimedia Software
---

### Post by tqhien on 2009-04-30
Hi,

I upgraded to Jaunty last week. I had a hard time trying to install lirc and lcdproc on 8.10 for 3 weeks since I came to Ubuntu a month ago. I managed to make some features work under 8.10 but gave up, as the release of Jaunty was planned to be released.

So, last week, I installed lirc and lcdproc through apt-get. I got the config dialog, chose Soundgraph Imon-Pad IR/VFD (as I have a Thermaltake Mozart/Medialab).

I configured lirc.conf, hardware.conf, added a lirc_imon.conf in /etc/modprobe.d/ with options lirc_imon pad2keys_active=1
But this last action doesn't seem to do anything.

IRW'ed show the right button, except for the pad, which show nothing.

That's for problem n°1.

Now Problem n°2.
I configured LCDd for imon lcd, 16x2 size. Everything worked fine. Except the server message keeps scrolling from left to right, by 4-6 characters jump. So it is kind of unreadable.
Launching lcdproc show the right screens, but the scrolling remains, which is kind of weird.
I try compiling lcdproc from source, to change the refresh rate : the scrolling is still present.
I did'nt try to compile lirc from source yet, as I wonder if some patch (and if so which patch) is of any use.

Anyone has the same pb as mine ?

Edit : I plugged off my computer then on then now, LCDProc is just fine. Maybe the usb had something weird and unplugged/plugged back clear some memory.

---

### Post by m2digital on 2009-05-20
I have the same issue #1.  I have an IMON Pad remote and receiver, but cannot get the pad (pad2key) to work.  irw does not recognize commands from the pad.  

Can anyone provide a walkthrough of how to resolve this, any patches that are needed to resolve this.  I've had no success following the procedures previously posted.

Any help would be very much appreciated.

---

### Post by lightpower on 2009-06-02
Hope you are running two instances of lircd for it to sence both the black and non-black keys.

---

### Post by barras on 2009-06-22
I have the same issue #1. I have an IMON Pad remote and receiver (I've Thermaltake dh101), but cannot get the pad (pad2key) to work. irw does not recognize commands from the pad.

Please help me,

Fabio

---

### Post by Eldis on 2009-08-05
I also have the same problem. Using jaunty have everything working from apt-get installation including VFD and remote but pad keys show nothing under IRW and pad2keys option is enabled.

I was under the impression the newest lirc had pad2keys included ?

I have the 15c2:ffdc version.

---

### Post by fax668 on 2009-08-06
This worked for me:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184/comments/19](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184/comments/19)

---

