---
title: "problems installing acx 100 driver"
date: 2005-02-26
forum: Networking &amp; Wireless
---

### Post by ubuntutje on 2005-02-26
Hello,

I'm realy new to linux, ubuntu.
i'm trying to get my wireless card with acx100 chipset working using craig's guide. My problem starts at the chapter " bringing your device up"  at  ./start_net. After typing this the message below appears

" Firmware not found or not readable. Have you placed it in the firmware directory or run make extract_firmware once? This script expects it to be either at ../firmware/WLANGEN.BIN (or ../firmware/TIACX111.BIN for the ACX111 chip), relative to the script's location, OR have you placed it in the default directory:/usr/share/acx?. Bailing..." 

What am i doing wrong? What should be the right directory?
The tarfile is uzipped to home/username/usr/share/acx
I'm sorry if  i'm asking stupid questions but did I miss something?
Does anybody know what to do?

---

### Post by lao_V on 2005-02-28
The firmware needs to be in your /usr/share/acx directory not on your /home

I have found a better solution to get the acx 100/111 chip working by using the DriverLoader from [Linuxant]("http://www.linuxant.com")

---

### Post by erk on 2005-08-06
[QUOTE=lao_V]The firmware needs to be in your /usr/share/acx directory not on your /home[/QUOTE]


Better to put it in /lib/hotplug/firmware/TIACX111.BIN-2.6.10-5-386

---

