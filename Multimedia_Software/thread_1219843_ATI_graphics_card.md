---
title: "ATI graphics card"
date: 2009-07-22
forum: Multimedia Software
---

### Post by djdanamal on 2009-07-22
Hi, I'm not sure whats going on with my computer, I have an installed ATI 9250 graphics card. I use the DVI output to my monitor, it works fine.
When I look it up in the "hardware Drivers" it does not show up? sould it?
Will the card be working with out having proper drivers installed? I have never actually  installed the driver.

---

### Post by bacil on 2009-07-22
Hw drivers only show up if you using or are able to use proprietary dirver. 

So answer is your card is supported either by defualt module or its support is loaded in kernel and you dont need to worry about that

---

### Post by djdanamal on 2009-07-22
ok that make sence.
It loads in kernal so thats why I've never had to worry about it.
The reason I have my mind on graphics cards is I want to upgrade very soon...
My board has AGP8x port which I'm obviously using and 3 PCI ports.
 Do some cards run from the PCI ports?

---

### Post by khelben1979 on 2009-07-22
From what I can see [here]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.26&lang=English&rev=9.3&ostype=Linux%20x86"), version 9.3 of catalyst is the latest one which supports your hardware.

---

### Post by djdanamal on 2009-07-22
so, if i go thru my system and un install all the standard graphics drivers and setup the ATI driver, will that actually give me better performance?
Seems like a lot of wk if there is no gain.....

---

### Post by khelben1979 on 2009-07-22
The native graphics drivers are always faster than the ones which is supplied as free open source drivers.

I wouldn't suspect fast graphics performance with that graphics card, though.

---

### Post by persiantc on 2009-07-22
I really like ATI graphics cards .

[www.persiantc.com]("http://www.persiantc.com")

---

### Post by internalkernel on 2009-07-22
Save yourself a heaache and go with Nvidia... I'll save the why ATI linux development sucks rant for later... Just look through the posts regarding install and support of ATI drivers. 

I had an ATI card on my old laptop, and it caused me endless headaches - still does in fact. That laptop is 3 years old, and as of Catalyst 9.3 it's no longer supported. Open Source drivers are getting better but forget about doing any serious 3D with those. 

just my opinion though...

---

### Post by khelben1979 on 2009-07-22
> **internalkernel said:**
> Save yourself a heaache and go with Nvidia... I'll save the why ATI linux development sucks rant for later... Just look through the posts regarding install and support of ATI drivers. 

I had an ATI card on my old laptop, and it caused me endless headaches - still does in fact. That laptop is 3 years old, and as of Catalyst 9.3 it's no longer supported. Open Source drivers are getting better but forget about doing any serious 3D with those. 

just my opinion though...

From my own experience: I have never been unable to install native graphics driver for any ati graphics chip or graphics card when I have done it on a Debian system. On Ubuntu, however, I have failed (but after much struggle I managed to fix it on Ubuntu as well)

I'm not sure if you should blame ATi for making bad drivers. Some ATi chipset or graphics cards might be badly supported in comparison with other ATi models though.

---

### Post by internalkernel on 2009-07-22
> **khelben1979 said:**
> I'm not sure if you should blame ATi for making bad drivers. Some ATi chipset or graphics cards might be badly supported in comparison with other ATi models though.

Perhaps... I just think that their support is poor, and I'm certainly not the only one... :) I experienced random lock ups, freezes and sometimes X would just crash when using their drivers. Their release cycle is rather long, not as long as Debian's though ;) Nvidia pushes out new drivers every month almost, it's like clockwork... I've just had a much better experience with Nvidia - and this last slap in the face of no longer supporting certain cards... I mean seriously, wtf? My laptop is 3 years old, it has a Radeon Mobility x600 with 256 megs. I would expect at the very least another 2 years of support.

---

### Post by khelben1979 on 2009-07-22
> **internalkernel said:**
> Nvidia pushes out new drivers every month almost, it's like clockwork... I've just had a much better experience with Nvidia - and this last slap in the face of no longer supporting certain cards... I mean seriously, wtf? My laptop is 3 years old, it has a Radeon Mobility x600 with 256 megs. I would expect at the very least another 2 years of support.

I agree that it sounds bad. Especially if you're interested in running newer games on these cards with reduced graphics quality, reduced screen resolution and so on.. New drivers are sometimes able to solve graphic bugs which plagues some games and I agree that if they had another policy this would make ATi a more attractive choice, however, I'm not sure how important this really is. One can't really expect that old graphics hardware would benefit from graphics acceleration because of newer drivers for example. I guess they haveto set limits and as long as the older drivers works you should be able to use your old graphics card until it starts to malfunction. 

I also think it's about greed too. Like every company they want to earn money and I guess giving support for old hardware isn't a priority with ATI/AMD.

---

