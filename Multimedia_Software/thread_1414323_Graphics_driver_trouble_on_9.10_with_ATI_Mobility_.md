---
title: "Graphics driver trouble on 9.10 with ATI Mobility Radeon"
date: 2010-02-23
forum: Multimedia Software
---

### Post by jabalsad on 2010-02-23
Hi all,

I'm having some graphics driver trouble on my Lenovo Thinkpad T500. I tried getting the ATI Proprietary driver to work (fglrx) but everytime I boot my X just crashes. Now I'm trying to use the open source driver, but i dont think its working becaues a) It doesn't detect that an external monitor is plugged in (for dual-view) and b) when i run glxinfo i get a "Error of failed request: BadRequest" message.

Can anyone tell me how to fix this? I have already followed the steps outlined at: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

My setup is as follows:
Ubuntu 9.10 amd64
ATI Mobility Radeon HD 3650

Thanks.

---

### Post by linux4life88 on 2010-02-23
> **jabalsad said:**
> Hi all,

I'm having some graphics driver trouble on my Lenovo Thinkpad T500. I tried getting the ATI Proprietary driver to work (fglrx) but everytime I boot my X just crashes. Now I'm trying to use the open source driver, but i dont think its working becaues a) It doesn't detect that an external monitor is plugged in (for dual-view) and b) when i run glxinfo i get a "Error of failed request: BadRequest" message.

Can anyone tell me how to fix this? I have already followed the steps outlined at: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

My setup is as follows:
Ubuntu 9.10 amd64
ATI Mobility Radeon HD 3650

Thanks.

You have an R600 graphics card, this is good. Right now the R600/R700 ATI open source graphics card drivers are being heavily programed and developed. Each kerenel and xorg release has new and improved support. My own experience is that the ATI proprietary drivers are junk. Right now people like you and I are in a little bit of a waiting game (I have a R700 card) because the proprietary drivers are horrible and the open source drivers are just not quite there yet. Be patient and checkout these pages for updates on the open source drive progress:

[http://www.x.org/wiki/RadeonFeature]("http://www.x.org/wiki/RadeonFeature")
[http://www.x.org/wiki/RadeonProgram]("http://www.x.org/wiki/RadeonProgram")

---

### Post by jabalsad on 2010-02-24
Well, to be honest right now I'm not really concerned with graphics performance. All I need to do is to get the DVI output on my docking station working in order to carry on with my work. So really I'm prepared to take any solution at this stage...

---

### Post by edmicman on 2010-03-21
I've got a similar problem if anyone could help.  I just got a Thinkpad T500 and have been setting it up this weekend with 9.10 64bit version.  Everything was working great, and of course I saw that there were proprietary AMD drivers available so I thought I'd try them out.  Bad idea.

I've got the laptop set up with switchable graphics and for the OS to choose; I read that Ubuntu doesn't actually support graphics switching , but it would just default to the Intel drivers and I was fine with that.  Anyway....

I enabled the proprietary drivers and of course after restarting nothing came up.  I ended up loading with a live cd and deleting /etc/X11/xorg.conf, and after it restarted everything came back up. 

After that I read that it was something with the flgrx drivers or something, and ran this:

sudo apt-get remove --purge xorg-driver-fglrx 

Buuuut...now I can't enable any desktop effects; it says it can't find any drivers.  Before (and on the LiveCD mind you) I had the "Extra" (wobbly windows, etc.) effects enabled and everything worked great.

How can I get back to where I started, with whatever default drivers get installed in the first place?  Help?

Oh, and I followed some of the instructions from those other links, here's some output:

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]


LIke I said, I'm OK wiht the Intel driver if it'll use that, or whatever gets installed/used by default if I haven't selected something specific in the BIOS.  So I wasn't sure if I need to do something else with ATI drivers?

---

