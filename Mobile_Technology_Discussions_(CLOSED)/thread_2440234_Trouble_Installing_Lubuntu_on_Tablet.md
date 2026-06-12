---
title: "Trouble Installing Lubuntu on Tablet"
date: 2020-04-07
forum: Mobile Technology Discussions (CLOSED)
---

### Post by jsinclair92 on 2020-04-07
Tablet Specs:
[Lenovo Thinkpad 2]("https://www.lenovo.com/us/en/tablets/thinkpad/thinkpad-tablet-2/") - I've added a link which has the full specs
Processor:  Intel Atom CPU Z2760 1.80GHz
RAM: 2GB
System type:  32-bit, x86 processor

I am attempting to install Lubuntu (32 bit version) on my tablet and am running into some issues.  I cant get the tablet to boot to the USB drive that I have Lubuntu on.  

Things I've tried (that I can recall):

[LIST]
[*]Changed the boot order, USB at the top
[*]Create bootable USB drive (w/ Lubuntu) using Gnome Disk
[*]Create bootable USB drive (w/ Lubutnu) using Rufus
[*]Create bootable USB drive (w/ Lubuntu) using Lubuntu Startup Disk Creator
[*]None of that worked... so I switched gears and tried to use DBAN to wipe the drive first, thinking this would help, somehow...? :mad: Of course, that wouldn't boot from USB either
[*]I tried to boot the USB on other laptops, which worked perfectly
[*]I tried an "Advanced startup" on windows 10, which allows you to select the boot drive, which also didn't work
[*]I turned google upside down and found that you can change the secure boot and uefi settings in the BIOS menu, which didn't work
[/LIST]

What are my options here?  Why wont this tablet boot from a USB drive?  Am I missing something?

---

### Post by CelticWarrior on 2020-04-08
Installing Ubuntu or any desktop Linux distro in such hardware is only for experts and even experts will have an hard time making everything work.

For starters, you need a modified 64-bit OS - never 32-bit, albeit the factory installed Windows is 32-bit - with an additional boot file. With that it will boot the live session and install but most hardware will need lots of tweaks to make it work.

IMO, it doesn't justify the time and effort.

> found that you can change the secure boot and uefi settings in the BIOS menu, which didn't work

Of course not... First of all, what you found is misinformed (and misinforming) people suggesting a Legacy/CSM install in UEFI hardware. There's no point in doing so in any modern hardware but specially in this case. Bay Trail's 32-bit UEFI doesn't have CSM!! So, not an option (and wouldn't change anything even if available).

---

### Post by jsinclair92 on 2020-04-08
Thanks for the response CelticWarrior.  So to confirm I am understanding correctly, I am out of luck since I have a 32-bit processor?  This is disappointing but I do understand the limitations.  And yes, it does run a 32bit Windows OS, which I'd love to give the boot because its slower than Christmas.

---

### Post by slickymaster on 2020-04-08
Thread moved to **Mobile Technology Discussions** for a better fit

---

### Post by CelticWarrior on 2020-04-08
> **jsinclair92 said:**
> Thanks for the response CelticWarrior.  So to confirm I am understanding correctly, I am out of luck since I have a 32-bit processor?  This is disappointing but I do understand the limitations.  And yes, it does run a 32bit Windows OS, which I'd love to give the boot because its slower than Christmas.

No, you're out of luck because you have a purposefully made **cost-saving "Frankenstein monster" with a 32-bit firmware (UEFI) and a 64-bit CPU/GPU**, tailored for Windows 8 32-bit or newer and Windows only.
For desktop Linux, since the beginning back in 2013/14 when those machines cropped out, it was a huge PITA, things improved slightly over the years, namely with better support for the weird SDIO bus WiFi and a few other tweaks but it remains a PITA up to this day. Just ask Google about "BayTrail Ubuntu" (CherryTrail also a problem). The issues are mostly related to Zxxxx or Xxxxx series; other series of the same families don't have that many problems.

---

### Post by mikewhatever on 2020-04-08
You may want to try Linuxium's work at [http://linuxiumcomau.blogspot.com/2020/02/canonical-have-announced-new-point.html](http://linuxiumcomau.blogspot.com/2020/02/canonical-have-announced-new-point.html). 
He's been doing those ISO respins for a few years now.

---

### Post by jsinclair92 on 2020-04-08
> **CelticWarrior said:**
> No, you're out of luck because you have a purposefully made **cost-saving "Frankenstein monster" with a 32-bit firmware (UEFI) and a 64-bit CPU/GPU**, tailored for Windows 8 32-bit or newer and Windows only.

I cant imagine a corporation cutting corners to save money! :lol:

mikewhatever - Thanks for the tip, I have reached out to Linuxium.  Hopefully he can help me outfit my Frankenstein of a tablet!  Windows has to go.

---

