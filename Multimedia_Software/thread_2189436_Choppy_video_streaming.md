---
title: "Choppy video streaming"
date: 2013-11-22
forum: Multimedia Software
---

### Post by zuren on 2013-11-22
I'm racking my brain on an issue that is proving to be a bit of an annoyance.  I'm hoping someone here in the community may have some ideas.

I have posted elsewhere on the forum regarding a used system that I purchased from a coworker for home theater PC use.  The HDD was dying and it was in a tower so this is its current configuration:

OS - Ubuntu 12.04
Case - SilverstoneTek Lascala LC13
Mobo - Gigabyte EP45-UD3P ver. 1.1
Processor - Core 2 Duo E8400 3.0GHz
SSD - Kingston HyperX 3K SH103S3/120G 2.5" 120GB SATA II
GPU - SAPPHIRE Ultimate Radeon HD 6670 1GB 128-bit GDDR
Optical drive - LG Blu-ray RW drive
PSU - Corsair HX620w
RAM - Corsair 4GB DDR2 1066
CPU cooler - ARCTIC Freezer 7 Pro
Network connection - Hardwired to router
Internet service &#8211; Verizon 15down/5up

It started life using a HIS Radeon HD 5850 video card.  Streaming video with the 5850 card was fine with a couple exceptions:

[LIST]
[*]XBMC &#8211; card would emit a very annoying, high pitched tone at a very steady, regular interval with this application open 
[*]NHL Gamecenter Live &#8211; I have a Gamecenter Live account that I stream hockey games through a browser (Firefox or Chromium).  The stream skips at regular intervals (like a scratch on a CD). 
[*]Cooling fan in general was loud 
[/LIST]

I wanted to go fanless anyway so I bought the 6670 card hoping other issues may be also be resolved.  Again, most streams are fine with but:

[LIST]
[*]XBMC &#8211; high pitched tone is gone but when I look at the hardware status, I can see the video card is mostly steady at 98.8 FPS but jumps to 630 FPS intermittently (again, like a scratch on a CD).  This doesn&#8217;t seem right.  I never checked this FPS issue with the other card but suspect it was similar. 
[*]NHL Gamecenter Live &#8211; Stream still skips.  It is watchable but not correct. 
[*]Silent operation now that it is fanless 
[/LIST]

My main focus is the issue with NHL Gamecenter Live.  For a comparison, I started up my laptop (new HP ProBook 6570b - Win7, Core i5 w/ integrated graphics, using Firefox, WiFi) and the NHL games stream perfectly.  This tells me it isn&#8217;t the stream or NHL servers but something in my hardware or software doing this.  Adobe Flash Player is the latest for both for Ubuntu and Windows7.

What else can I troubleshoot or research to smooth out this video issue?  I have included some System Monitor numbers below.  Please let me know if there is anything else you need to see or if anything is jumping out as abnormal.

Thanks!


System Monitor Readout while the stream from NHL Gamecenter Live is active:

CPU1 - ~50%
CPU2 - ~50%
 Memory utilized - 18.3%
Stream - 0-1MB/sec (jumps from 0 to 1 to 0)
XBMC (System>System Info>Video) - 1920x1080@0.00Hz Full Screen 98.8 FPS (jumps to 630ish)

---

### Post by deep_friar on 2013-12-19
I have the same problem with Gamecenter Live on my two dissimilar machines running Ubuntu.

Curiously, I did not have this problem in previous NHL seasons. I have subscribed to Gamecenter Live for at least the past three seasons, and both my Toshiba netbook and my home-built desktop played GCL video perfectly (at such data rates as they could handle, which for the netbook was strictly less than maximum) until this season (2013-14). 

I've switched the netbook and the desktop back and forth between 13.10 and 12.04 LTS during the current NHL season to check out whether it was something new specifically in Ubuntu causing the trouble, but neither version has allowed me to make GCL play smoothly on either machine.

The netbook exhibits the same choppiness no matter what wireless network I use to connect to the Internet -- home, coffee shop, university campus, T-Mobile 3.5G via tethering to my phone, whatever.

I am worried that something did indeed change on the National Hockey League's end between last season and this one that disadvantages Linux users.

---

### Post by vinni_f on 2014-11-05
found any fix or anything interesting?

---

### Post by sammiev on 2014-11-05
> **vinni_f said:**
> found any fix or anything interesting?

This thread is about a year old, I would suggest starting a new one where you will likely get more help.

---

