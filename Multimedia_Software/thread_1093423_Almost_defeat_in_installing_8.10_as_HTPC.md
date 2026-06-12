---
title: "Almost defeat in installing 8.10 as HTPC"
date: 2009-03-11
forum: Multimedia Software
---

### Post by jamh on 2009-03-11
Hi everyone,

I am and will always be a devoted fan of ubuntu, and so was quite excited when I put together a machine from leftover parts to act as an HTPC to drive an optoma HD77 projector.

Unfortunately, after a week of wrestling with it, I had to abandon it and install windows XP instead.  I would like to try again, with your help.  What follows is what went wrong.

The hardware: Motherboard with built in X200 Radeon, AMD 64bit cpu, 1Gb memory, 2x250Mb drives striped into one, 20 ft VGA to DVI cable to projector that runs 1280x720 native.

I tried with ubuntu 8.10 amd 64.  I have used the CD before and was confident on it being good.  Well the install didn't seem to be able to launch startx. If I used a shorter cable and a monitor, it installed ok, but as soon as I connected it to the projector with the longish cable, X11 hung.  I made a jig with chairs and tables to keep the box close to the ceiling mounted projector (to my wife's horror), and this way I could get further, but this was no solution really, since it worked fine with Windows, so the problem is most likely screen detection in the Radeon driver, or something similar.

I tried different drivers, all with the same result.  Also, even close up, I could never build an xorg.conf that supported my 1280x720, it always fell back to 1024x768, no matter what I put in the conf file.

On the positive side, I had no issues with the Linksys wireless PCI card, and had tons with windows (I ended up finding a driver that worked on a Korean site).

I am willing to give it another try, say have a dual boot system, but before anything else I need advice.  What's the deal with the cable?

Thanks much,
Jam

---

