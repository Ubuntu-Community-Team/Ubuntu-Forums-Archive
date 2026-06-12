---
title: "How do you change webcam drivers?"
date: 2008-12-27
forum: Multimedia Software
---

### Post by complete n00b on 2008-12-27
Hi, I just got Ubuntu on my ASUS notebook the other day, and I don't know the first thing about Linux. Nevertheless almost everything has been going alright so far. There are just a couple of problems, one of them is my upside-down webcam.

I've googled and been through the forums and spent hours doing everything I could find without really understanding what it was that I was doing, but to no avail.:confused:

According to lsusb, my webcam is a: 

Bus 003 Device 002: ID 174f:5a35 Syntek 1.3MPixel Web Cam - Asus G1s

manufactured by SONIX, which is stupidly installed upside-down in the ASUS laptop (they really should have make a quick fix by now but as far as I can tell they haven't).

When I do: udevinfo --query=all --name=/dev/video0 --attribute-walk

it tells me that the driver I am using is uvcvideo. 

Apparently the stk11xx driver has a vflip option to put the camera the right way up, but uvcvideo does not have this option (I have attempted to use all four patches made by arjos85 but they haven't worked).

I want to switch my drivers and see if I can get the vflip option, but I don't know how to do that and I'm worried that I'll accidentally make my webcam unusable.

If anybody knows what to do please give me some instructions bearing in mind that I am a TOTAL novice.

---

