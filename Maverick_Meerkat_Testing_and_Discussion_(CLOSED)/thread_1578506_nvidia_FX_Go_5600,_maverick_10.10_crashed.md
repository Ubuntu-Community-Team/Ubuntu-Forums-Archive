---
title: "nvidia FX Go 5600, maverick 10.10 crashed"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dominikvz on 2010-09-20
I have Sony Notebook GRT896HP, and Nvidia FX Go 5600.

On 10.04 graphics driver was working well, but after upgrading to Maverick 10.10,
ubuntu is not working on any nvidia drivers, nvidia-current ...

Please how to setup or witch driver can i install for nvidia.

Ubuntu is working only if i uninstall all nvidia drivers and files and delete xorg.xconf ...

is it nvidia FX Go 5600 supported with any driver in maverick ?

thank you

---

### Post by s.fox on 2010-09-22
Thread Moved to [Maverick Meerkat Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=385")

---

### Post by cariboo on 2010-09-22
Have a look at [this]("http://ubuntuforums.org/showpost.php?p=9875976&postcount=16") post, it should answer your question.

---

### Post by dominikvz on 2010-09-23
I have look post, but it is not working, on install
driver tells me that Fx Go5600 is not supported .
and driver is disabled nouveau driver ...

---

### Post by dominikvz on 2010-09-24
[B]Please help !!!!
[/B]
i have try eather older drivers, but all the same chrashed ...

I have try to clean install of maverick, but there was the same problem !!!

On Ubuntu 10.04 lucid, enithyng was worked perfectly !!!

On 10.10 Maverick can not find solution ...

---

### Post by dominikvz on 2010-09-24
NOTEBOOK MODEL:

[**http://www.laptopsdirect.co.uk/Sony-Vaio-GRT896HP-PCG-GRT896HP/version.asp**]("http://www.laptopsdirect.co.uk/Sony-Vaio-GRT896HP-PCG-GRT896HP/version.asp")

---

### Post by dominikvz on 2010-09-27
Any solution please ?

Why was 10.04 version automaticly find and install drivers ?

---

### Post by cariboo on 2010-09-27
Do the nouveau drivers work for you? You can get 3D support for nouveau drivers in the [xorg-edgers ppa]("http://https://launchpad.net/~xorg-edgers/+archive/ppa"). 

It looks like nvidia, has slowed develop on the drivers for older graphics chipsets.

---

### Post by dominikvz on 2010-09-27
Nouveau drivers is working, i have resolution 1280x1024 and good color depth, but 2D is slow. When i move windows on desktop, there are, how to i say, there are ghost windows (duplicated) until
window is not moving to another position on desktop.

And i can not setup Visual effects, Normal or Extra, i think compiz
detect to slow graphic card....

I do not use 3D, this is not nesesery for my work (i think)... 

In 10.04 in "Addition drivers" there was detected Nvidia drivers automaticly,
i have activated and evrything wa working perfectly. I was have complete setup "Nvidia Settngs", and without changing eny default settings, i was have 10 times faster 2D ...

---

### Post by cariboo on 2010-09-27
Have you tried purging nvidia-current:

```
sudo apt-get purge nvidia-current
```

Then re-istalling it? the installation process should blacklist the nouveau drivers.

---

### Post by mc4man on 2010-09-27
I would take a look here for supported cards with the cuurent nvidia drivers that work w/ xserver 1.9 (or follow link on page
While there appears to be support for Quadro Fx * series there is not for Geforce less than 6000 series.

In that case then, ATM,  it's nouveau or go back to xserver 1.8 or 10.04**.**
Whether legacy cards get 1.9 support is solely up to nvidia
[ftp://download.nvidia.com/XFree86/Linux-x86/260.19.04/README/supportedchips.html](ftp://download.nvidia.com/XFree86/Linux-x86/260.19.04/README/supportedchips.html)

---

### Post by dominikvz on 2010-09-28
yes i have try, and after this, i was have to do new clean install 10.10
(i did not know how to restore blacklisted nouveau driver)

Code: 	sudo apt-get purge nvidia-current 
nvidia-current is not working, disables nouveau and crashes xserver

---

### Post by dominikvz on 2010-09-28
is it any way to setup nouveau driver for Visual effects (Normal, Extra),
i thing this is compiz !?!?

---

### Post by dominikvz on 2010-09-28
Back to 10.04 version, i do not want to do that,
10.10 version is faster and more stable, there is better overal performance on my laptop.

---

### Post by dominikvz on 2010-10-08
[B]Driver is now available (after several distribution upgrading) on detected additional drivers.
After activating, it works perfect !!!

UBUNTU RULEZ !!!!!!!!!!!!!!!!!!!!!![/B]

---

