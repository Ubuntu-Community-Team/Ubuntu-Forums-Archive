---
title: "Wireless remains off on HP dv6000"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by cupabj on 2009-01-08
Hi,

I recently installed ubuntu 8.04 on a HP dv6000 series laptop with Vista dual boot. Initially, wireless worked for a few hours after installation of b43-fwcutter and driver for the inbuilt Broadcom wireless card. Soon, wireless refused to turn on after reboot. The Amber LED remained on and never turned Blue. I tried booting in Vista and same problem there too. HP support asked me to reinstall BIOS and Broadcom drivers. That, expectedly, didn't help. I checked *lspci* output and that doesn't show the Broadcom wireless device. In Vista too, the Broadcom wireless doesn't show up in Device manager. While this could well be a HP hardware problem, it happened soon after getting wireless to work in Ubuntu. I would like to know if anyone experienced it after ubuntu installation. Is there any chance that ubuntu changes some BIOS settings that leads to the wireless card to remain in 'off' state? Or, is there any possibilty that firmware/microcode is flashed by ubuntu drivers that leads to a 'permanent' problem with the wireless card? Appreciate any solutions/workarounds to get the wireless up again.

---

### Post by melojo on 2009-01-08
I have never herd of ubuntu or linux doing that.  First thing I would try is to unplug and take out the battery and hold the power button for 30 seconds.  Put battery back in and see if it makes any difference.  If it shows up in windows but does not work.  Remove it from the hardware list and reinstall.

---

### Post by cupabj on 2009-01-08
Tried to power cycle the way you suggested. Didn't help. Thanks anyway.

> **melojo said:**
> I have never herd of ubuntu or linux doing that.  First thing I would try is to unplug and take out the battery and hold the power button for 30 seconds.  Put battery back in and see if it makes any difference.  If it shows up in windows but does not work.  Remove it from the hardware list and reinstall.

---

### Post by knappen on 2009-01-08
You did not turn it off by accident? It happens to me every now and then.

---

### Post by cupabj on 2009-01-08
Nope! That's the  first thing that I checked :)
> **knappen said:**
> You did not turn it off by accident? It happens to me every now and then.

---

### Post by Ayuthia on 2009-01-08
> **cupabj said:**
> Hi,

I recently installed ubuntu 8.04 on a HP dv6000 series laptop with Vista dual boot. Initially, wireless worked for a few hours after installation of b43-fwcutter and driver for the inbuilt Broadcom wireless card. Soon, wireless refused to turn on after reboot. The Amber LED remained on and never turned Blue. I tried booting in Vista and same problem there too. HP support asked me to reinstall BIOS and Broadcom drivers. That, expectedly, didn't help. I checked *lspci* output and that doesn't show the Broadcom wireless device. In Vista too, the Broadcom wireless doesn't show up in Device manager. While this could well be a HP hardware problem, it happened soon after getting wireless to work in Ubuntu. I would like to know if anyone experienced it after ubuntu installation. Is there any chance that ubuntu changes some BIOS settings that leads to the wireless card to remain in 'off' state? Or, is there any possibilty that firmware/microcode is flashed by ubuntu drivers that leads to a 'permanent' problem with the wireless card? Appreciate any solutions/workarounds to get the wireless up again.

Have you checked with HP about any recall/limited warranty about this?  I had the same problem and HP replaced my motherboard for me.  The issue was with the BIOS not being aggressive enough with their fans.

---

### Post by cupabj on 2009-01-08
Your reply indicates that this is indeed a HW problem. I'll contact HP about this. I hope that they honor the warranty beyond 1 year and across different countries! 
Thanks for your response.
> **Ayuthia said:**
> Have you  checked with HP about any recall/limited warranty about this?  I had the same problem and HP replaced my motherboard for me.  The issue was with the BIOS not being aggressive enough with their fans.

---

### Post by Ayuthia on 2009-01-08
> **cupabj said:**
> Your reply indicates that this is indeed a HW problem. I'll contact HP about this. I hope that they honor the warranty beyond 1 year and across different countries! 
Thanks for your response.

My laptop was over a year old when it happened.  HP release a special limited warranty for this issue so hopefully they will honor it.

---

