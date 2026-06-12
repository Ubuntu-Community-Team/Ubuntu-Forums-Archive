---
title: "Desktop resolution"
date: 2013-03-30
forum: Multimedia Software
---

### Post by mJayk on 2013-03-30
Hi all,

Quick niggly problem,  I recently switched to xfce desktop on my ubuntu install. First off I was unable to select the correct resolution for my monitor so I installed xrandr that fixed that problem.  Since then however when I logon I get no display - just No signal.

My current quick fix is if i switch to tty1 crtl+alt+f1 then back to tty7 it works fine.  Strange huh?

Any ideas.

Cheers in advance

Matt

---

### Post by Bucky Ball on 2013-03-30
*Thread moved to **Multimedia & Video**.*

Which driver are you using for your graphics card? What make/model is the graphics card?

---

### Post by mJayk on 2013-03-30
Haya im using the standard driver that comes with the install been unable to find any decent drivers with this card / kernel combo

Card is an old x1800 GTO - ati and ubuntu 12.04 64 bit

---

### Post by Bucky Ball on 2013-03-30
Hmm. Have you checked in Additional Drivers after an update and nothing there? ATI should be using fglrx and Catalyst Control Centre (control resolution from there) but not sure if that is the case with older cards (although should be).

* Just had a quick look and there doesn't seem to be too many folk having probs with that card. Vesa driver seems to work fine. Is that what you're using at the moment?

---

### Post by mJayk on 2013-03-30
yea for older cards the driver support stops at a certain kernel.  Its legacy support.

---

### Post by mJayk on 2013-03-30
I also dont see how it can be a driver problem if I dont get the same problem with other desktop enviroments (unity - gnome etc)

---

### Post by Bucky Ball on 2013-03-30
You are using the Vesa driver?

---

### Post by mJayk on 2013-03-30
How can I find the exact driver I'm using?  I've not installed any graphics drivers as of yet.

And thanks for the help.

---

### Post by Bucky Ball on 2013-03-31
No worries. Try this:

```
sudo lshw -c video
```

That'll show you the driver down the bottom somewhere.

---

### Post by mJayk on 2013-03-31
[sudo] password for matthew: 
  *-display:0             
       description: VGA compatible controller
       product: R520 [Radeon X1800]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:e0000000-efffffff memory:f5000000-f500ffff ioport:c000(size=256) memory:f4000000-f401ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f5010000-f501ffff



is the output.  Not clear to me what the driver is.

---

### Post by Bucky Ball on 2013-03-31
```
*-display:1 UNCLAIMED
description: Display controller
product: Advanced Micro Devices [AMD] nee ATI
vendor: Hynix Semiconductor (Hyundai Electronics)
physical id: 0.1
bus info: pci@0000:01:00.1
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress bus_master cap_list
configuration: latency=0
resources: memory:f5010000-f501ffff
```

There is no driver installed for the display controller. The Radeon 1800 does seem to have an appropriate driver installed, though.

---

### Post by Yellow Pasque on 2013-04-01
> ATI should be using fglrx and Catalyst Control Centre (control resolution from there) but not sure if that is the case with older cards (although should be).
No. fglrx/Catalyst is not usable/applicable here.

> There is no driver installed for the display controller
From what I've seen, it's normal for lshw to report 'Unclaimed' on the secondary controller.

Try playing with xfconf:
```
xfconf-query -c displays -l
xfconf-query -c displays -p /Default/DVI-0/Resolution
```

---

