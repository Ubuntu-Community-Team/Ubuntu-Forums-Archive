---
title: "Dual Monitor problem with graphics card drivers"
date: 2013-05-23
forum: Multimedia Software
---

### Post by Tjkhan on 2013-05-23
I tried everything but nothing is working. If I install the driver from aditional driver or manually from the graphics card site and install that... all same. Its for dual monitor i guess. Because, if i unplug one monitor then the system doesnt show any problem.

Whatever I do, shows errors shown in the two attached screenshots below.

I tried on my laptop and that works fine! But my desktop doesnt. 

I m using Unubtu 12.04
It say I am using 2D when I try to start **MyUnity**, it says i m using 2D. 


**Questions:**
[LIST=1]
[*]**What should I do?** 
[*]**Using 2D will effect on anything like  web development? Java and all other animation things?** [so far didnt face any problem] 
[/LIST]

Thank you

---

### Post by dino99 on 2013-05-23
Looks like an hardware plugging issue: hdmi/vdi/cord

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Multimedia & Video**.*

I have deleted the two large screenshots in the body of your post. A reminder to all: Please think of those with slow connections and vision issues and refrain from posting large pics in the body of posts. Cheers. ;)

---

### Post by gordintoronto on 2013-05-23
What video card is in the system? What is the brand and model of each of the monitors, and what are their native resolutions? What cable is used for each monitor?

---

### Post by Tjkhan on 2013-05-24
i moved to 13.04
Now everything working fine. Thank guys for everything

---

### Post by heidricha on 2013-05-28
Lucky you!

I still can not find a way to connect two monitors. 

The system is Intel i5, so should have a i915, or similar video, and another one is inserted into the PCI-X slot. The system only sees the NVIDIA in the slot:

lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

There are HDMI and VGA on the board, HDMI, DVI and VGA on the card. 
VGA on the first monitor, VGA, and DVI on the other)

2 VGA cables.
1 HDMI to DVI cable.

If I connect HDMI only, I have no boot screen, thew monitor gets alive only after X gets alive, and use the HDMI output. 
If I connect the same monitor (No. 2 of course) to the NVIDIA card with both cables, it works fine, but no chance to use the othewr monitor at all.

The maximum I could reach, that if I connect the VGA of the board to the first of the monitors, and both VGA and HDMI on the card to the other, I have got a boot screen (ubuntu with the dots) on the first monitor... after boot it freezes, the system changes the other monitor, and it works standalone, no other card, or other monitor is detected. When I halt/reboot, the dots goes further on the first monitor, after the second one has been turned off by the system.

I have also tried several ways to connect the monitors, but seems to me, that this card with this driver just can not handle more than one monitor, and the system for some resason does not support the two cards simultaneously.

What else should I try?

---

### Post by heidricha on 2013-05-28
Quick update:
Using DVI-DVI cable, and opensource driver, both monitors work...

I guess the problem is, that the HDMI output is the alternative of the VGA... so I can not use the two monitors on DHMI and VGA, one of them should be on the DVI... the other one can be connected via HDMI or VGA...

---

### Post by heidricha on 2013-05-28
Slower update...

After playing with DVI cable and opensource driver, the whole stuff started to work somehow - in the very same config I have tried for the first time. NVIDIA driver works now as well.

The system was able to "survive" even a reboot - so the settings are the same than before, and can be correctly tuned with nvidia-tools. 

Can not learn anything from this story, I guess...

---

