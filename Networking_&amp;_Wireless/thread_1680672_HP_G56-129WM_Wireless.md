---
title: "HP G56-129WM Wireless"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by mightybrick on 2011-02-02
I'm not a linux newbie, but I'm not an expert either. I need some assistance getting my wireless working on this laptop I got for Christmas. I'm running 10.10. The wireless toggle on the keyboard doesn't turn on the wireless. The LED toggles on and off, but ubuntu reports wireless as "device not ready". 
Here is the output from lswh:
```
brock@Brock-HP:~$ sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:09:6a:58
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=0 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:d3500000-d3503fff

```
Then when trying to bring the device up, I get:
```
brock@Brock-HP:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not permitted

```
"Rfkill list all" shows no blocks.
Would anyone have any suggestions that I could try?
Maybe a driver issue?

EDIT: OK, I rolled back to 10.04, and wireless works fine now. Guess I'll stick with Lucid. I don't know if I should mark this solved, since technically the problem wasn't fixed.

---

