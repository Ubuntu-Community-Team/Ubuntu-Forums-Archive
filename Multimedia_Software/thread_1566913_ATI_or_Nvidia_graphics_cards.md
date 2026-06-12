---
title: "ATI or Nvidia graphics cards?"
date: 2010-09-03
forum: Multimedia Software
---

### Post by Cityscape on 2010-09-03
What is a better brand to use for Ubuntu Linux, ATI or Nvidia graphics cards? Which has the better proprietary driver? Which has the better ubuntu open source driver?

Lots of opinions please. ;)


Adam ):P

---

### Post by Plasma_NZ on 2010-09-03
My 2 cents are as follows..

i used to be a avid ATI fan untill i switched to linux... found the entire process to install a ati card overly complex and fiddly..

NVIDIA on the other hand, weather its drivers directly from nvidia or that come with ubuntu - easy as pie, basically like a windows installer except done via terminal with GDM stopped...

anything after that is personal preference using NVIDIA-SETTINGS..

---

### Post by Cityscape on 2010-09-03
So generally Nvidia is better? Do most people agree with this?

---

### Post by Tracy177 on 2010-09-03
> **Cityscape said:**
> So generally Nvidia is better? Do most people agree with this?


ati hd 4850 work perfect in 10.04 

aticonfig --adapter=0 --od-getclocks

Adapter 0 - ATI Mobility Radeon HD 4850
                            Core (MHz)    Memory (MHz)
           Current Clocks :    500           850
             Current Peak :    500           850
  Configurable Peak Range : [500-550]     [850-900]
                 GPU load :    2%


ticonfig --adapter=0 --od-gettemperature

Adapter 0 - ATI Mobility Radeon HD 4850
            Sensor 0: Temperature - 53.00 C

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4850
OpenGL version string: 3.3.10151 Compatibility Profile Context


nvidia wont show gpu load 

my card work perfect unless u have got old ati card every new card is supported by catalyst.

ahh one thing when i play movie open vbox and use compiz and internet at the same moment the gpu load is never more than from 5 to 10% max

dont know about nvidia

---

### Post by cchhrriiss121212 on 2010-09-03
Nvidia has the better proprietary driver - easy video acceleration, regular driver updates, overall solid performance. Nouveau is not ready yet IMO. 
ATI has the better open driver - recently installed 10.04 on a new desktop and the open driver was installed automatically. No problems with it and all vidoe/graphics were running smooth even with compiz going.

---

### Post by ratcheer on 2010-09-03
Without comment on the two hardware platforms (nVidia and ATI graphics cards), I think **nVidia** has much better support for Ubuntu. At this point in time, anyway.

Tim

---

### Post by Cityscape on 2010-09-04
Okay, well I'm looking to build a computer. I have those choice of motherboards with any of the following integrated graphics cards:
ATI Radeon 2100
ATI Radeon 3000
ATI Radeon HD 4200
ATI Radeon HD 3200
NVIDIA GeForce 6150SE
NVIDIA GeForce 6150
NVIDIA GeForce 7025
NVIDIA GeForce 6100
NVIDIA GeForce 8200

Which card do you guys think will be best with Ubuntu? I normally prefer to use the open source driver if I can but if needed I would use the proprietary driver. My favorite motherboard has the Radeon 2100, what do you think of that card?

---

### Post by Cityscape on 2010-09-04
This is the motherboard that I like best, it has the Radeon 2100.
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128342](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813128342)

---

### Post by JBAlaska on 2010-09-04
In my experience NVIDIA is better supported on Linux.

That being said, If you get a MB with integrated graphics, the chip-set tends to get hot. In my case with a GeForce 8200 VERY hot(175F to shutdown) 

The simple fix for me was a Thermaltake Extreme Spirit II CL-C0034 Chipset cooler. This cooler is worth every penny of the $20.00us it cost me, and my Northbridge never gets over 104deg F no matter what I'm doing.

---

### Post by xircon on 2010-09-04
Mobile Radion 5000 series here, should have gone with Nvidia with hindsight, but it is still a step up from Intel GMA.

---

### Post by jeight on 2010-09-04
[SIZE=4]Nvidia[/SIZE] by far.

---

### Post by Cityscape on 2010-09-04
I'm not really concerned too much about how good the IGP is, but more about how well it works with Linux. As stated before I like the Radeon 2100 motherboard, does anyone know how well it works with Linux (by either the open source or closed source drivers)?

I've searched the web to see if the 2100 is good with Linux but some news was positive and some bad. But everything I read was at least 1.5 years old! So how could I tell if the Radeon 2100 works with Linux?! ATI has an outdated driver on their website but I've never been able to install any of their drivers.

---

### Post by imnotrich on 2010-09-04
Actually...ati, nvdia or intel doesn't seem to matter with Ubuntu 10.04 based distros. I had installation difficulties on several different machines. No video is a bit of a deal breaker. I don't see the bug fixes for video card incompatibility listed elsewhere on the Ubuntu pages but at least for my computer with the nvidia card 10.04.1 is working within virtual box. So maybe there's hope.

Anybody know when the bug fixes in 10.04.1 will be added to Ubuntu Studio? I'm hoping to install Ubuntu studio, or at least Ubuntu regular with sound recording packages for my home studio.

---

### Post by Cityscape on 2010-09-05
> **imnotrich said:**
> Actually...ati, nvdia or intel doesn't seem to matter with Ubuntu 10.04 based distros. I had installation difficulties on several different machines. No video is a bit of a deal breaker. I don't see the bug fixes for video card incompatibility listed elsewhere on the Ubuntu pages but at least for my computer with the nvidia card 10.04.1 is working within virtual box. So maybe there's hope.

Anybody know when the bug fixes in 10.04.1 will be added to Ubuntu Studio? I'm hoping to install Ubuntu studio, or at least Ubuntu regular with sound recording packages for my home studio.

Yeah, Ubuntu 10.04 is the worst I've seen so far for graphics card support. My other computer has an ATI Radeon X200 and it worked parfect on 9.04 Jaunty with the default driver. But when I installed Lucid all the graphics intense applications like Google don't render correctly anymore. :(

---

### Post by tkmn on 2010-09-05
It looks like Radeon 2100 is **not** supported by the Catalyst driver.

```
AMD Chipset Product Support
ATI RadeonTM HD 4290 ATI RadeonTM 3200 Series
ATI RadeonTM HD 4250 ATI RadeonTM 3100 Series
ATI RadeonTM HD 4200 Series ATI RadeonTM 3000 Series
ATI RadeonTM HD 3300 Series

```

I have a motherboard with Radeon 3200 graphics. It works well using Ubuntu 10.04 64 and Catalyst 10.7. Well everything except new games with wine (SC2).

The open source driver was also pretty good last time I tried it. (Compiz & basic 3d worked)

---

### Post by Cityscape on 2010-09-05
Hmm, thanks a lot for th info. If i choose Radeon 2100 on the ATI website I get this driver: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English)
But it hasn't been updated since early 2009. Would it work is what I'm now wondering?

---

### Post by alphacrucis2 on 2010-09-05
> **Cityscape said:**
> Hmm, thanks a lot for th info. If i choose Radeon 2100 on the ATI website I get this driver: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English)
But it hasn't been updated since early 2009. Would it work is what I'm now wondering?

No. The legacy Catalyst driver does not work with Lucid (or Karmic for that matter). Are you sure you entered the right specs for the card. If it is a HD2100 then it should be telling you Catalyst 10.8 which is fine with Lucid.

---

### Post by sxmaxchine on 2010-09-05
ati cards are definitely better but the drivers are terrible so you would be better with an nvidia for linux machines.

---

### Post by sxmaxchine on 2010-09-05
the radeon 4200 works perfectly with ubuntu however the radeon 5xxx series cards will give u a bit of trouble

---

### Post by Cityscape on 2010-09-05
> **alphacrucis2 said:**
> No. The legacy Catalyst driver does not work with Lucid (or Karmic for that matter). Are you sure you entered the right specs for the card. If it is a HD2100 then it should be telling you Catalyst 10.8 which is fine with Lucid.
No, It is a Radeon 2100 (sometimes called X2100), not HD 2100. It is considered a legacy card, and the latest catalyst version is 9.3. Thanks some much for letting me know that the catalyst driver does not work with Lucid! How would I tell if it works with the open source driver (other than buying)?

Would it be safe to say that any card that has an updated driver available (10.6 or 10.8 catalyst for example) will work in Linux via that driver?

What about other brands like XFX or Gigabyte ([http://www.newegg.ca/Product/Product.aspx?Item=N82E16814125251](http://www.newegg.ca/Product/Product.aspx?Item=N82E16814125251)), are their graphics good for linux? I couldn't find any drivers on their websites.

---

### Post by alphacrucis2 on 2010-09-05
> **Cityscape said:**
> No, It is a Radeon 2100 (sometimes called X2100), not HD 2100. It is considered a legacy card, and the latest catalyst version is 9.3. Thanks some much for letting me know that the catalyst driver does not work with Lucid! How would I tell if it works with the open source driver (other than buying)?

Would it be safe to say that any card that has an updated driver available (10.6 or 10.8 catalyst for example) will work in Linux via that driver?

What about other brands like XFX or Gigabyte ([http://www.newegg.ca/Product/Product.aspx?Item=N82E16814125251](http://www.newegg.ca/Product/Product.aspx?Item=N82E16814125251)), are their graphics good for linux? I couldn't find any drivers on their websites.

You may want to check out the Phoronix forums. They have a section dedicated to Linux graphics drivers. Both Open Source and proprietary.

---

