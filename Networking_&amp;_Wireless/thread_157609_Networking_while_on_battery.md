---
title: "Networking while on battery"
date: 2006-04-09
forum: Networking &amp; Wireless
---

### Post by latitudeD600 on 2006-04-09
Tags: networking does not work when laptop is on battery.
Hello - 

  I am new to ubuntu, but having been impresed by it I have installed it on my laptop from which I am writing now. 
   All is fine except for the fact that when I start up on battery power, even thow I ifconfig shows I have an Ip address, I cannot access the web . ping/ telnet/www  completety out of order. Both on wireless and wire.

Please let me know if you have any solutions. Since I work from cafes/ clients it is necesary that I have network come up on startup /wake up from sleep mode.

Thank you.

---

### Post by jml on 2006-04-09
A couple ideas come to mind.  Does your laptop have power saving settings that can be adjusted from within the BIOS set up utility?  Its possible that your computer may be configured to conserve power when running on battery by turning off certain power draining functions.  Another possibility, if your wireless has a power button, try pushing it once when on battery power and see if that helps.  It might be turned off when booting from the battery.

Another possibility, I have read about is that the ACPI power saving functionality of some laptops in some way interferes with wireless functionality.  Try booting with ACPI disabled and see if wireless works.  This will have an effect on the laptop's battery life, however.

Joe

---

