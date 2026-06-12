---
title: "visual effects problem"
date: 2008-11-14
forum: Multimedia Software
---

### Post by carlo bolzonello on 2008-11-14
hey all,

my graphics card worked fine under 8.04, when i upgraded it it, and go to appearance under system - visual effects its set to none.

How do i go about troubleshooting this issue, i would like to log it as a bug if its a major problem.

any help please :)

---

### Post by Sam Lars on 2008-11-14
Are the other settings disabled?

---

### Post by carlo bolzonello on 2008-11-15
hey, which other settings are you refering too?,

---

### Post by Sam Lars on 2008-11-15
You're saying it's set to none, are the other settings (Normal, Extra) disabled or do they just not work when you choose them?

---

### Post by carlo bolzonello on 2008-11-16
hi, they are available, the other settings, however when i click on normal, i get the following " desktop effects could not be enabled" and than it reverts back to none. 

It did work prior to upgrade, it was set to normal. Thank you for your help so far

---

### Post by xc3RnbFO8P on 2008-11-16
Try **compiz** in Terminal.

---

### Post by carlo bolzonello on 2008-11-16
i get this when i run  compiz

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by xc3RnbFO8P on 2008-11-16
Check /etc/modprobe.d/**blacklist**
see if you find **8086:2562**

---

### Post by eternalnewbee on 2008-11-16
>  visual effects problem
hey all,

my graphics card worked fine under 8.04, when i upgraded it it, and go to appearance under system - visual effects its set to none.

How do i go about troubleshooting this issue, i would like to log it as a bug if its a major problem.

any help please
Have you checked whether your **Hardware Driver** is enabled?
> Checking for Xgl: not present.
Blacklisted PCIID '8086:2562' found
aborting and using fallback: /usr/bin/metacity
You might need a workaround for this.
The best thread for your problem is: **Desktop Effects & Customization**
Sorry I can't be of more help.

---

### Post by Sam Lars on 2008-11-16
You can see this thread for a script to help you with diagnosing Compiz problems like this.
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by carlo bolzonello on 2008-11-17
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by pluckypigeon on 2008-11-18
> **carlo bolzonello said:**
> Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

I have exactly the same problem as you!! and almost the same output on compiz-check (the only difference is the rev03 bit)

```

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by pluckypigeon on 2008-11-18
Here are two threads that have the same problem

Neither of them are solved as of yet. 

I'll try and keep everyone posted though and if I get a fix I will post it as soon as pos!!!

[http://ubuntuforums.org/showthread.php?t=962520](http://ubuntuforums.org/showthread.php?t=962520) 
- this one was started by me a few weeks ago

[http://ubuntuforums.org/showthread.php?t=981644](http://ubuntuforums.org/showthread.php?t=981644)
- this one was started by someone else a few days ago

---

### Post by carlo bolzonello on 2008-11-19
thank you very much for the assistnce, i am thinking that maybe its a good thing to post it to the guys as a bug so that they can solve it.

---

### Post by pluckypigeon on 2008-11-19
> **carlo bolzonello said:**
> thank you very much for the assistnce, i am thinking that maybe its a good thing to post it to the guys as a bug so that they can solve it.

I think there already is one
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/283056](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/283056)

---

