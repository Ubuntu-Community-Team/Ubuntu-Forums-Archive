---
title: "NIC detection works once then dies"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by polluxmr2 on 2009-10-06
I have a very weird problem. its kubuntu 9.04 with all the latest updates. the machine was made from an image of a ( nearly ) identical machine. the hardware differences are a video chipset ( which corrected the problems for ) and it has 2 NICs, rather than one.

So here is the basic progress of the problem.
1). boot from live kubuntu machine
2). image machine and reboot
3). boot off of local hdd
4). work away configuring it for production
5). reboot
6). no longer detects any NICs. ifconfig only outputs the lo interface. /etc/udev/rules.d/70-persistent-net ( or whatever ) reports it has two NICs (expected)
----------- begin fix --------------
7). reboot
8). in bios disable all nics
9). boot and delete the /etc/udev/rules.d/70-persistent-net ( or whatever ) file and lspci and make sure no NICs are present
10). reboot (confirm there is no new 70-persistent-net file )
11). reboot and enable all NICs in the BIOS
----------- fixed ----------------
12). now both nics are detected
13). reboot ( on boot proceed to step 6, do not pass go, do not collect 200 dollars )

i booted on a live cd 10 times, and the NICs detected 10 times. 

so, any ideas? it looks like the first boot after a successfully NIC detection in the last boot breaks it. im all out of ideas. ( and i know it isn't a hardware problem, i have two acting exactly the same )

---

### Post by polluxmr2 on 2009-10-08
so i stumped everyone?

---

