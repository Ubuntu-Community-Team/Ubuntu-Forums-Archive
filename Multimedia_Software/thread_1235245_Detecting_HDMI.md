---
title: "Detecting HDMI"
date: 2009-08-08
forum: Multimedia Software
---

### Post by nsen on 2009-08-08
These forums have been very helpful in getting my Ubuntu up and running. I am right now stuck and don't know where the problem is - tv, motherboard or Ubuntu. Tending towards something in Ubuntu. The problem is the HDMI output is not detected in consistent way. Here are my scenarios:

Note, VGA, DVI and HDMI are all connected. VGA is connected to a separate monitor. DVI (using DVI-HDMI adapter) and HDMI both connected to the TV. (With VGA connected to the TV, nothing worked!)

1. When booting, neither DVI or HDMI gets detected. Ubuntu output is only on VGA.

2. When I log out and log back in and the TV display is set on DVI (that is the  active display on the TV), everything works - even HDMI with sound out! The ATI Catalyst detects the TV as HDMI.

3. When I log out and log back in and the TV display is set on HDMI, Ubuntu output is only on VGA. 

4. When I log out and log back in and the TV display is on on DVI and the HDMI is disconnected, output is there on VGA and DVI. Now, if I connect the HDMI back in, there is video but no audio. In ATI Catalyst, the TV is detected as DVI.

So, for me to use Ubuntu on my tv, I need to keep all outputs connected. I need to do also follow the process of logout and log back in from the VGA monitor. I would like to not have to use VGA and boot my machine and be able to use HDMI. I have tried using different HDMI ports on the TV but did not help. Any hints/suggestions on what I can try out?

I have built my PC:
Foxconn A7GM-S 2.0 motherboard with ATI Radeon 3200 
I am using the latest drivers directly from ATI
Ubuntu Jaunty

---

### Post by nsen on 2009-08-25
I thought I provide an update...after trying various combinations and re-installing Ubuntu and trying it out on another TV (where it worked perfectly), it came down to a setting on my Toshiba TV. There was a menu item called "HDMI control" that was off. When I turned it on, everything is working like a charm now!!!

---

