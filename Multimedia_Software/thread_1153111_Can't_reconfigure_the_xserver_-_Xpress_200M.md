---
title: "Can't reconfigure the xserver - Xpress 200M"
date: 2009-05-08
forum: Multimedia Software
---

### Post by white_eagle-mk on 2009-05-08
Yesterday, I **finally** decided to move on to the OSS drivers for my integrated graphics card so I removed the fgrlx prop. (from AMD) drivers I was using till now because they don't offer support for my chip - ATi Xpress 200M - anymore, they moved it to the legacy section. Well I decided to move ATi's drivers to the legacy section of my PC because of their poor politics because I found out that the makers of the libre drivers finally released 3D support for my chip. 

I used [these instructions]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") to remove fglrx and replace it with the free 'ati' driver. When I followed those instructions *in the past* - on the last step:```
sudo dpkg-reconfigure xserver-xorg
``` -- I _always_ got output and I could choose between which driver to use from the offered ones.

Now, when I do that, I don't get any output at all! The terminal bounces me back as I've hitten enter without typing anything in the command box :( :x

I've asked the same question on the [Phoronix forums](http://www.phoronix.com/forums/showthread.php?t=16894) (ignore the first post - I got that solved), but I haven't gotten a response yet - I want a faster response I thought I may get here.

The thing that's really annoying in this problem and will *certainly* get fixed if I manage to reconfigure the xserver somehow, is that I have to accept to boot into 'low-graphics' mode and click OK once more whenever GDM starts!

I tried with backuping *xorg.conf* first and then deleting it from */etc/X11* and re-trying to configure the server, but the same thing happens! Don't worry, I returned the backed-up xorg.conf file. 

What should I do? I'm very desperate about this problem! I'll be very glad if I find a working solution to this as I can't find anyone with the same problem as me on Google.

Thanks for any help!

ps. Please, **I beg you** don't tell me to revert to the propietary fglrx driver (except if that's part of the solution to get the 'ati' OSS driver working) and don't tell me to do a fresh install either because I don't have a way for how to do that (don't ask).

In the meantime, I'll keep searching for an answer and post it here if it has been successfull.

---

### Post by white_eagle-mk on 2009-05-09
Bumpity BUMP.


I haven't found a solution yet! :(

---

