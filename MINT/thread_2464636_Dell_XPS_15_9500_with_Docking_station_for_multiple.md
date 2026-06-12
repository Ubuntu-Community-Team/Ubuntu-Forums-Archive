---
title: "Dell XPS 15 9500 with Docking station for multiple displays"
date: 2021-07-07
forum: MINT
---

### Post by jfaberna on 2021-07-07
I have a Dell XPS 15 9500 (10th Gen Core i7) with a docking station Dell D3100 that connects to the XPS via USB3. The dock has GBe, USB2 and USB2 along with HDMI and DP to support up to 3 monitors. I've tested this successfully only on Windows 10.

I dual-boot the XPS with Linux Mint which uses Ubuntu 20.04.2 (5.8.0-59 kernel).

My problem is that I can't seem to see any of the monitors that connect to the docking station the same way I can in Windows 10. Linux can see the GBe Lan port in the dock, but not the DP or HDMI's. 

Any Ideas?

EDIT: Forgot to mention that the D3100 Dock connects via USB3 type A. Since the XPS 15 9500 has only Type C for Thunderbolt and USB3, I use a DA20 Adapter that came with the laptop to connect the D3100.  The DA20 has USB3 Type C for the laptop, USB3 type A for the D3100, and another HDMI on the DA20. That HDMI does work with Ubuntu as an extended desktop to the laptop.

---

### Post by coffeecat on 2021-07-07
*Thread move to **Mint** sub-forum.*

---

### Post by jfaberna on 2021-07-07
I think the problem is related to DisplayLink drivers not being installed. I'm going to play with those and see if I can get it working.

---

