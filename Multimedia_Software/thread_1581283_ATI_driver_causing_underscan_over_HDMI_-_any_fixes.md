---
title: "ATI driver causing underscan over HDMI - any fixes?"
date: 2010-09-24
forum: Multimedia Software
---

### Post by Hallsy on 2010-09-24
From searching around I gather this is a common problem, but I have not really found a solution :(

This is my first Linux install and so far it's been a steep learning curve!!

Basics are Ubuntu 10.4, Gigabyte mobo with integrated ATI HD3200 (iirc) graphics.  Screen is Panasonic 50G10 plasma connected over HDMI, running at 1920x1080.

Installed ATI propietry drivers within hardware drivers program, and I had underscan.  Had this before with Win7, but had an under/overscan slider for that - none in Linux ATI CCC.

So I removed and reinstalled ATI drivers from AMD site, still the same.

I found a fix by googling around, that mentioned moving the positon of the screen (X,Y) within aticonfig, but I couldn't find out what device it had selected.

Looked in Xorg.conf and it has my device down as DFP1, which in CCC translates as a projector.  Could this be part of the problem?  How can I edit my xorg.conf to get aticonfig to see my display as a plasma?  

Anyone any ideas?  I can't deal with the underscan, it is too annoying!!!!

---

### Post by SeePU on 2010-09-24
Did you look in CCC (Catalyst Control Center) settings?

I seem to recall reading someplace that there's a setting for overscan/underscan and you set it to '0.'

---

### Post by booah on 2010-09-24
Hallsy,

Have a look at your TV settings first. This happened my yesterday and I spent so long messing with drivers and display when allI needed to do was set my tv input to hdmi.

---

### Post by tedrogers on 2010-10-12
I have this very same problem, and have been searching for a solution for ages now. I've given up many times, only to come back to it again.

I had hoped that Ubuntu 10.10 would fix it, seeing as it now has abolished xorg.conf and does everything "automagically" - or not as is my case.

I can't even get the ATI Driver from the ATI website to install because I think it is not compatible with 10.10. I will crack on with this avenue of solution for now, until something better comes along.

My TV has no option to under/overscan and the input is already configured properly, else I would not see any image at all on my particular television (Toshiba Regza 42" inch).

I tried mucking about with xrandr, which didn't really help a great deal. I even tried adding a custom modeline, but couldn't get this to work. I will probably have another go at this at some point.

Does anyone have a cleaner more efficient solution?

Thanks.

===========

UPDATE: Maverick Meerkat 10.10 uses X.Org 7.5 which is incompatible with the ATI Driver 9.3 for Linux x86 (ati-driver-installer-9-3-x86.x86_64.run) from AMD's website. This is why the driver will not install.

My search for a solution, that doesn't tell me its my TV that is at fault, continues.

---

### Post by Hallsy on 2010-10-16
> **SeePU said:**
> Did you look in CCC (Catalyst Control Center) settings?

I seem to recall reading someplace that there's a setting for overscan/underscan and you set it to '0.'

There was an underscan/overscan slider in the windows version of CCC, but not in the the Linux version :(

> **booah said:**
> Hallsy,

Have a look at your TV settings first. This happened my yesterday and I spent so long messing with drivers and display when allI needed to do was set my tv input to hdmi.

There are no settings that I can find to make it any better, all I can do is overscan (which overscans the image but still keeps the borders if you get me), zoom, etc but they all leave the borders.  This TV displayed fine with Win7.

> **tedrogers said:**
> I have this very same problem, and have been searching for a solution for ages now. I've given up many times, only to come back to it again.

I had hoped that Ubuntu 10.10 would fix it, seeing as it now has abolished xorg.conf and does everything "automagically" - or not as is my case.

I can't even get the ATI Driver from the ATI website to install because I think it is not compatible with 10.10. I will crack on with this avenue of solution for now, until something better comes along.

My TV has no option to under/overscan and the input is already configured properly, else I would not see any image at all on my particular television (Toshiba Regza 42" inch).

I tried mucking about with xrandr, which didn't really help a great deal. I even tried adding a custom modeline, but couldn't get this to work. I will probably have another go at this at some point.

Does anyone have a cleaner more efficient solution?

Thanks.

===========

UPDATE: Maverick Meerkat 10.10 uses X.Org 7.5 which is incompatible with the ATI Driver 9.3 for Linux x86 (ati-driver-installer-9-3-x86.x86_64.run) from AMD's website. This is why the driver will not install.

My search for a solution, that doesn't tell me its my TV that is at fault, continues.

With a problem across two different make TV's (if not more), I would say it is definitely ATI at fault.  Such a shame they won't address the issue.  Just a simple slider as the Windows version has would do it.

It's annoying for me, as I decided to try Ubuntu as I didn't want to shell out for another copy of Win7, but if I have to buy an Nvidia card just to get my display right in Ubuntu, it kind of defies the point!!

---

### Post by tedrogers on 2010-10-16
Well I feel a bit daft, but I finally found out what to do.

There is a hidden option for EXACT SCAN on the HDMI input of my TV, that *only* appears when a signal is detected and is different to other inputs default options (which is why I never noticed until now when I really was looking hard for it).
I put this on, borders removed and I can see the whole desktop.

I know I said my TV had no option for this, but I really have only just stumbled across this after trying to find a solution to this for a very long time.

Moral: Look harder for things, and don't assume that menu systems on TV's will be logically arranged.

---

### Post by Hallsy on 2010-10-26
Interesting Ted.  Does it stay this way now, or do you have to change the settings every time you select this input?

I'm pretty sure my Panasonic doesn't have any input specific options, but I'm going to double check anyway!

---

### Post by tedrogers on 2010-10-27
> **Hallsy said:**
> Interesting Ted.  Does it stay this way now, or do you have to change the settings every time you select this input?

I'm pretty sure my Panasonic doesn't have any input specific options, but I'm going to double check anyway!

Yes it does stay like that. I even have reset my underscan to 0% in Windows 7 as a result. This has been an epiphany for me.

---

### Post by the_pod on 2010-12-04
I'm in the same boat. Have a 47" Visio and no discernable options for addressing over/underscan via TV menus. Very sad. :(

Worst, it seems I had a solution a year ago, but did a fresh install 2 weeks ago and can't figure out how to fix things.

---

