---
title: "dual head nvidia how to specify primary display?"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by bung-foo on 2006-12-28
I am using ubuntu 6.10. I have an nvidia 7800 gt and I've installed the latest nvidia drivers from nvidias website. I have two monitors an lcd and a crt. I use the lcd as my primary display and the crt I just leave email client, IM, etc on. 

I've pretty much got everything working but there is one really annoying problem I can't figure out. No matter how I change things around the crt is always the primary display. By this I mean that the login screen is displayed on it and the default desktop is displayed on it.

I've changed the order of the devices in the xorg.conf.

I've swapped the outputs on the vid card that the monitors are plugged in to. 

I've done a lot more over the last few weeks that I don't remember. 

Is there a way to tell the xserver which monitor to use as the primary display?


I am at work right now so I can't post my xorg.conf. I can do that later tonight if anyone wants to see it.

thanks folks!

---

### Post by majoridiot on 2006-12-28
i'm pretty sure that on the nvidia cards that the vga connector will always be the primary 
display and the dvi will be secondary... i know that's how mine is, and all attempts to change
it around failed.  nvidia's driver docs make more than one reference to the difficulty in
specifying which monitor is primary and which secondary and does not provide a concrete
way of changing things around.

you might try asking at the nvidia forums... it's usually a reliable source for info, as nvidia
staff/mods will chime in should someone give you bad advice.

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by mk4umha on 2007-11-06
I know this is an old post but did you ever figure this out? i'm having the same problem except this is on my notebook with a 7400 go.

---

### Post by bung-foo on 2007-11-06
I never did figure it out. majoridiot's post is correct as far as I can tell.

---

### Post by mk4umha on 2007-11-07
> **bung-foo said:**
> I never did figure it out. majoridiot's post is correct as far as I can tell.

I think I know how it works. The internal display for the notebook is always on display 1:0, the vga port is 0:0. If the xorg.conf does not list a scree/display adaptor for display 0:0, it defaults everything to the one that's listed which is display 1:0.

I figured that out once i reran the standard X config setup.

---

