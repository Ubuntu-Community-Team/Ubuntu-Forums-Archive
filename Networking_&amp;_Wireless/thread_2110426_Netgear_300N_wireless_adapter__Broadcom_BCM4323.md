---
title: "Netgear 300N wireless adapter / Broadcom BCM4323"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by wingnut2626 on 2013-01-30
Good morning (or afternoon, or evening, or midnignt, or.....) fellow  ubuntu users.  I have the forsaken Netgear 300N wireless adapter, that i am using through the ndiswrapper and the windows drivers.  The chipset is Broadcom BCM4323.  I am able to connect and maintain a stable connection except:

the download speed (as reported through speedtest.net) seems to bog at 5 Mbps, and the upload speed is never faster than 6 Mbps.  This recently started happening as i upgraded to ubuntu 12.10.

When i was using the lubuntu 12.10 with the same drivers, I was getting speeds of 25/25, which is more realistic with the service that i have coming in.  It is a new(er) computer, a P4Ht vs a P4 which i had before. 

Any suggestions on what is holding me back?

---

### Post by wingnut2626 on 2013-01-31
should i go back to lubuntu?

---

### Post by wingnut2626 on 2013-01-31
Figured it out.  My CMOS battery had died.  And this motherboard, i guess, on default, disables the usb 2.0 controller.  So the wifi adapter was running on USB legacy mode.  Very weird........ but solved

---

