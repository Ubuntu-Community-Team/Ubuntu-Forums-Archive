---
title: "Looking for a dual HDMI video card"
date: 2010-01-11
forum: Multimedia Software
---

### Post by new_to on 2010-01-11
Hello,

I currently use "MSI Radeon HD 3650 Graphics Card - ATi Radeon HD 3650 750MHz - 512MB GDDR3 SDRAM - PCI Express" that have no HDMI and some problems with Ubuntu. Due to the Ubuntu compatibility problems I decided to ask you guys for recommendations before upgrading to a new video card. 

The only "demand" is that the card must have dual HDMI outputs, one for the monitor and one for the TV. 

Thanks is advance.

---

### Post by new_to on 2010-01-12
bump

---

### Post by new_to on 2010-01-12
bump

---

### Post by new_to on 2010-01-14
no bump on edit ...

---

### Post by new_to on 2010-01-15
Does anyone knows if the "ATI Introduces Radeon HD 5670" play nice with Ubuntu 9.10? Is setting up two monitors going to be a headache? How can I found if there's a driver for this card?

[http://www.pcworld.com/article/186908/ati_introduces_radeon_hd_5670.html](http://www.pcworld.com/article/186908/ati_introduces_radeon_hd_5670.html)

---

### Post by new_to on 2010-01-15
Bump :popcorn:

---

### Post by Nathan.Flow on 2010-01-15
> Hello,

I currently use "MSI Radeon HD 3650 Graphics Card - ATi Radeon HD 3650 750MHz - 512MB GDDR3 SDRAM - PCI Express" that have no HDMI and some problems with Ubuntu. Due to the Ubuntu compatibility problems I decided to ask you guys for recommendations before upgrading to a new video card. 

The only "demand" is that the card must have dual HDMI outputs, one for the monitor and one for the TV. 

Thanks is advance. 

What are you asking? Are you looking for a card that has 2 HDMI ports on it or are you looking for HDMI out-put through some sort of converter, like DVI to HDMI?

> Does anyone knows if the "ATI Introduces Radeon HD 5670" play nice with Ubuntu 9.10? Is setting up two monitors going to be a headache? How can I found if there's a driver for this card?

[http://www.pcworld.com/article/18690...n_hd_5670.html](http://www.pcworld.com/article/18690...n_hd_5670.html)

ATI now has first day linux support for all their cards, this means you can download the driver from their site. 

[HTML]http://support.amd.com/us/gpudownload/Pages/index.aspx[/HTML]

Just make sure you chose the right architecture(32 bit vr 64bit. ```
uname -m
``` should tell you what architecture your running, then chose the brand, then chose the series. You will have to run it from command line, this not difficult, just run ```
sudo driver.run
```where "driver" is the name of that driver package. As for getting Eyefinity to work, don't know. 

Also I don't recommend bumping your own threads.

---

