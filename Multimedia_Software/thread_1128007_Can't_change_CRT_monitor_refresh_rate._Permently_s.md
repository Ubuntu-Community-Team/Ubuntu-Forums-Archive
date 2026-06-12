---
title: "Can't change CRT monitor refresh rate. Permently set to 60Hz"
date: 2009-04-17
forum: Multimedia Software
---

### Post by UserNumberUno on 2009-04-17
Hi.

I have a Panasonic PanaSync E70G.  The monitor is an analog VGA CRT 17" inch display.  Normally in Windows the monitor runs at 1024x768 and 85Hz.  I just installed Ubuntu 9.04RC and the display defaulted to 1280x1024 and 60Hz.  I changed the resolution to 1024x768 using the Display menu item in the System menu.  But when I went to change the refresh rate the refresh rate was shown as 0.0Hz.  The is no option to change it to 85Hz.  The monitor is currently running at 60Hz and this hurts my eyes.  Is there some way to change the refresh rate to 85Hz?  I also have an Nvidia 6600GT that is fully supported by the free nv driver.

---

### Post by jukingeo on 2009-06-27
> **UserNumberUno said:**
> Hi.

I have a Panasonic PanaSync E70G.  The monitor is an analog VGA CRT 17" inch display.  Normally in Windows the monitor runs at 1024x768 and 85Hz.  I just installed Ubuntu 9.04RC and the display defaulted to 1280x1024 and 60Hz.  I changed the resolution to 1024x768 using the Display menu item in the System menu.  But when I went to change the refresh rate the refresh rate was shown as 0.0Hz.  The is no option to change it to 85Hz.  The monitor is currently running at 60Hz and this hurts my eyes.  Is there some way to change the refresh rate to 85Hz?  I also have an Nvidia 6600GT that is fully supported by the free nv driver.

I think there might be a work around for those that have Nvidia cards, but for us ATI users, we are stuck.  This wasn't always the case, but I don't know why recently there has been a rash of problems with support past a 60hz refresh rate.  In the past I DID have about 75hz with my ATI card, but a recent update to Ubuntu altered that.  I tried to roll back the updates but was unsuccessful.  I have also tried to probe why there is an issue with ATI and Ubuntu, but there seems to be very little in terms of answers.

Overall I been about a year on Ubuntu and I must say I am not impressed with the way it handles hardware support.  There is just way too much hoop jumping to take care of (what I consider) small problems.  Sound problems seem to dominate here.  The sad thing is that I am using Ubuntu STUDIO and would like to use it on a professional level.  But with all the problems with hardware, I don't foresee that as being a possibility.

Anyway, hope you find a solution to your problem.

Geo

---

### Post by %zqMOA$@U97bJ£&amp; on 2009-07-29
I just want to say, that in Ubuntu 7.xx, 8.xx, and 9.04 (I'm writing from it now) native drivers for NV6150 can't set refresh rate 100Hz in 1024x768. There is a strange list of (useless) options like 87Hz etc, but even this options doesn't work to well. 85 gives 78 etc., Even more strange is that in higher resolution (AFAIK 1152x864) there is 100Hz in the list. Choosing it sets screen to 92Hz and works.

Now I'm trying to download drivers from driver update. ver. 180 failed to download - application crashed.
I know, that in LCD refresh rate it's not so important and setting 60Hz solves problem, but in CRT higher refresh rate helps to protect eyes.

Config:
Ubuntu 9.04
Asus M2N-MX SE PLUS (integrated NV6150 SE)
Eizo FlexScan F520 (old CRT)

PS. Sorry for my english. It's not my native language.

- EDIT -
Finally it works! I successfully installed NVIDIA drivers version 180 (recommended in the list) and now it's working 1024x768@100Hz. Card and monitor are detected correctly. Sorry for bothering.
[I]
**UserNumberUno[/I]:**
Try to install new drivers (180) - it might help. If not, try older version (if they support your card).

---

### Post by jukingeo on 2009-08-03
> **ULLISSES said:**
> I just want to say, that in Ubuntu 7.xx, 8.xx, and 9.04 (I'm writing from it now) native drivers for NV6150 can't set refresh rate 100Hz in 1024x768. There is a strange list of (useless) options like 87Hz etc, but even this options doesn't work to well. 85 gives 78 etc., Even more strange is that in higher resolution (AFAIK 1152x864) there is 100Hz in the list. Choosing it sets screen to 92Hz and works.

100hz?  Why would you want to go THAT high?  75 or 85 should be good enough.  At any rate, early releases of Hardy did work with my ATI card, the latest update whacked it out.  I tried to roll back, but it didn't work.  So now I am stuck with the 60hz setting.

> 

- EDIT -
Finally it works! I successfully installed NVIDIA drivers version 180 (recommended in the list) and now it's working 1024x768@100Hz. Card and monitor are detected correctly. Sorry for bothering.
[I]
**UserNumberUno[/I]:**
Try to install new drivers (180) - it might help. If not, try older version (if they support your card).

Well, Nvidia is supported way better than ATI and when I had an Nvidia GForce 5200FX on my machine, I never had resolution problems.  The trouble though was that the 5200 was becoming outdated and I was having trouble playing a couple of my games in Windows.  I was in need of a video card update.  The clincher is that my machine is older and the power supply cannot handle the newer power hungry cards.  Cost wise, buying a new machine was out of the question. After doing much research I found the ATI 9600XT.  This card is twice as powerful as the 5200, but at the same time consumed slightly less power than the 5200.  So there was no question that it would work on my machine.  So I bought it and the Windows games I was having trouble with did greatly improve.  BUT then I started running into problems with Linux. As I said, I was able to change resolutions at first, but after a long move and my machine was in a 4 month hiatus, I did updates on it and now I can't get my resolution off of 60hz.  I am running a Dell 17" flatscreen right now and the 60hz resolution looks very good.  But on my Sony 17" CRT screen, I do notice the flicker.  I am not as bothered by it as some people, but it is somewhat annoying.  So I would like to fix that problem, or rather I hope the Ubuntu devs fix that problem

Geo

---

### Post by %zqMOA$@U97bJ£&amp; on 2009-08-05
My success was temporary. Now it's everything like in older version. NVIDIA Control Panel works, drivers are loaded (v180.44) but there is no 100Hz in the list.

Why I want go so high in refresh rate? Becouse I use computer very often and I used to use 100Hz in Windows. Wiht 100Hz I can seat all day long in front of the screen without any problems. With lower refresh rate my eyes get tired.

I have 17-inch CRT and 1024x768@100Hz is optimal setting for this screen. But now I have only 87Hz and nothing more. I'm going to try some xorg.conf tricks and if it fail, I'm thinking about choosing another distro - in Gentoo refresh rate problem doesn't exist.

---

### Post by jukingeo on 2009-08-27
> **ULLISSES said:**
> My success was temporary. Now it's everything like in older version. NVIDIA Control Panel works, drivers are loaded (v180.44) but there is no 100Hz in the list.

Why I want go so high in refresh rate? Becouse I use computer very often and I used to use 100Hz in Windows. Wiht 100Hz I can seat all day long in front of the screen without any problems. With lower refresh rate my eyes get tired.

I have 17-inch CRT and 1024x768@100Hz is optimal setting for this screen. But now I have only 87Hz and nothing more. I'm going to try some xorg.conf tricks and if it fail, I'm thinking about choosing another distro - in Gentoo refresh rate problem doesn't exist.

Your eyes must be REAL sensitive to flicker then. Usually 85 is fine on my CRT and I am also good with 75.  But at 60hz, I notice the flicker considerably.  Now this is on the CRT monitor. Lately I been using a flat screen LCD monitor and it too is running at 60hz, but I don't notice the flicker at all.

I DO like my CRT better (colors are richer), but the LCD is easier on my eyes.

I am basically accepting that this is a Linux ATI issue.  I just know that on my dedicated use machines (I am planning in the future), I am going to stick with Nvidia and I shouldn't have problems with the refresh rate.

The big downfall are the big companies like ATI...I don't know when they are going to get it in their thick skulls that by assisting the needs of the developers of Linux WOULD result in more of US buying THEIR product.  But as it stands, we are not going to buy something if it doesn't work!

That is my biggest gripe about Linux in general...hardware support is disastrous.

Geo

---

