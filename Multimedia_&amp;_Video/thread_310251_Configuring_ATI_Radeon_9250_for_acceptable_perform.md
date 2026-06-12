---
title: "Configuring ATI Radeon 9250 for acceptable performance for use with AIGLX"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by VCSkier on 2006-11-30
A friend of mine has a AMD64 desktop with a ATi Radeon 9250 PCI bus card and we are trying to configure his xorg.conf to give him acceptable performance in beryl through AIGLX.  Has anyone had success with compositing on this card, using the open source "radeon" driver?

Even with just a Firefox window open, frame rates will dip below 20 fps, maybe even below 15 fps, which is unacceptable, considering his graphics card has 256 MB DDR RAM, and he has a speedy dual-core processor, with a GB of system RAM.

We've tried many different combinations of xorg.conf options, and none of them have helped; is there a official, or recommended set of options that give optimal performance with the "radeon" driver and AIGLX?  Or, if not, what do you guys use/recommend?

I'd like to use the open source "radeon" driver, because I tried the proprietary "fglrx" binary drivers first, and couldn't even get a good XGL session.  Besides, I like using Free stuff, and I think AIGLX is a better/more long-term way of compositing.

Thanks everyone.

---

### Post by VCSkier on 2006-12-04
Bump?  If no one has gotten AIGLX to work on a system like this, what about XGL?  Has anyone found success with compositing in XGL on a system like this one; I'd be willing to try that again if someone has reported success.

---

### Post by VCSkier on 2006-12-06
FWIW, the card is based off of rv280, xorg identifies it as a Radeon 9200 Pro...  If no one here has any advice, where else could I seek help?

---

### Post by nasosp on 2006-12-07
I had an ATI Radeon 9200 Pro VGA and I tried this script with OSS drivers fpr AIGLX+Beryl

Edit your /etc/X11/xorg.conf

In the device section in the file you should create something that looks like this:

Section "Device"
Identifier "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
Driver "ati"
Option  "XAANoOffscreenPixmaps" <-- definately put this one it enables 3D
Option "AGPFastWrite" "yes"
Option "AGPMode" "4" <-- you can put up to 8 if you have agp 8
Option "EnablePageFlip" "on"
Option "ColorTiling" "on"
Option "UseFBDev" "true"
BusID "PCI:1:0:0"
EndSection

I have saved this configuration from a wiki but I don't have the link.


Oh take a look at this as well to add anything if needed:  [https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy?highlight=%28aiglx%29](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy?highlight=%28aiglx%29)
Generally this should do the trick as it did for me. But I suggest that you buy a new card as I did. I don't know but firefox with ati 9200 scrolls like s**t. Don't ask me why... Many people with 92** series face the same prob. Maybe they will fix it with a new driver but I bought a new vga, since I didn't like the performance... Try and tell me, maybe this is going to work better for you. 

Finally, buy a used one if you don't want to put a lot of money from ebay ... :D

---

### Post by VCSkier on 2006-12-07
thanks, i'll try this config next time i'm on his computer, and i'll let you know how it goes.  my only reservation is because his card is pci, not agp.  do agpmode and agpfastwrite still apply?

---

### Post by nasosp on 2006-12-07
Oh... sorry I didn't see it. You can bypass them don't use them. It's gonna be ok.

---

### Post by VCSkier on 2006-12-07
oh, and how will i know if i need to use agp 4 or 8?  will x crash if i have it set too high?

---

### Post by RSL on 2006-12-07
Will the AGP setting even do anything since the card is PCI? I was running Beryl for a while on the same card as you're talking about, VCSkier. I got decent results no rain effects though.

---

### Post by VCSkier on 2006-12-07
> **RSL said:**
> Will the AGP setting even do anything since the card is PCI?
lol, i didn't even think about that...  i'm dumb sometimes.

i'm still curious about determining the proper agp mode setting for my laptop's radeon mobility 9000, but you're right, as nasosp said, for the card in question, the PCI radeon 9250, the agp settings are irrelevant.

> **RSL said:**
> I was running Beryl for a while on the same card as you're talking about, VCSkier. I got decent results no rain effects though.which driver and version were you using?  did you apply any patches or anything?  And what did you have in your xorg?  could there be any other variables that might effect this?  could the fact that it is an AMD64 dual core processor cause issues?

Thanks!

---

### Post by RSL on 2006-12-08
It just kinda *worked* for me right out of the box. I no longer run it because I've reinstalled my system and just been too busy. I remember that I used the default ATI driver from xorg and not the proprietary or the fglrx one. I tried both but both gave worse results than the default Ubuntu ATI driver. I don't think the Rain effects work on that card, sadly.

I found this bookmark I made. I'm sure I used it to get the performance or something. [http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7)

Hope this helps.

---

### Post by eightballd on 2007-01-15
Were you ever able to get decent performance?   I'm currently in a similar boat (though my boat is 32bit).... Radeon 9250 PCI using "radeon" driver.  Accelleration is ON (though I don't know what FPS I'm getting with glxgears) but Beryl is unberylably (haha) slow.  

Haven't had a chance to tinker with it yet though, was late last night when I finally got it to stop crashing (hint:  don't have Load "GLcore" in your xorg.conf with this configuration!)

---

### Post by one_stinky_bum on 2007-01-19
Same here - radeon 9250 on a P4 2.2Ghz. A solution would be nice. :guitar:

---

### Post by sloggerkhan on 2007-01-19
I have a an x700 128mb using the ATI (radeon) driver for beryl with AIGLX and it doesn't do the water effects, either. (Though it does do snow.)

My Beryl can be a little laggy @ my native res of 1680x1050, though it works fine with about 1280x800.  I think it performed better with fglrx+xgl

---

### Post by je1117 on 2007-01-19
i'm running an AMD64 with a radeon 9200. in my quest for finding the right drivers, I installed Edgy, tried the open source drivers. I never even got to boot up into it - black screen. But I might have done something wrong, a guy running my same specs suggested AIGLX and he was using it currently. So i don't know.

I'm using closed source with Dapper now.

---

### Post by fvgm on 2007-01-19
hi guys. i´m from Brazil, I have ATI 9250SE 128MB 64bits AGP card, and when i run beryl everything goes slow.. but the cube and all effects (except water and blur) are functionally. 
Its a poor performance in firefox, even in terminal too!!


please where are the solution?
buy a new card? :)

---

