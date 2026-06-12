---
title: "Cannot access internet after changing to BT Homehub3"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by trevorCooley on 2013-02-19
Hi, I've been using Ubuntu for a few months without any serious problems until I upgraded to BT Infinity and the Homehub 3. I've spent about a week trying to resolve the issue myself but I just can't get to the bottom of it.

Problem:

1. Internet access is broken when using a wireless connection on the BT Homehub3. 

Details:

1. Internet/wireless was working fine using previous BT Homehub1.
2. Internet works fine using a wired connection.
3. Could be some kind of DNS issue as I can ping IPs directly (e.g google 74.125.132.103) and Skype seems to work. 
4. I cannot ping my router on wireless.
5. I am using a dual-boot Win7/Ubuntu Samsung N220 Netbook.
6. Windows install on the same machine and other devices are accessing the Internet fine.
7. I'm using Ubuntu 12.04.2 LTS.
8. I can wirelessly access the Internet via other people's routers.
9. No updates to Ubuntu were performed between using the different versions of the HomeHub, but I have updated subsequently.
10. Unfortunately I do not recall the exact details, but after reading numerous other BT related posts I have tried disabling wireless security, pointing to an alternate DNS server, disabling power management, changing the wireless interface type and the wireless channel on the router, all to no avail. There is a chance I may have made some mistakes during these steps though.
11. I've read that there have been issues with dual-boot machines and BT routers (same MAC address?), but this issue occurred before I had ever booted into Windows using this router.
12. I'm sure there are more details that I've forgotten but I've been going round and round in circles for so long that I'm completely lost.

Thanks for any advice or ideas.

---

### Post by trevorCooley on 2013-02-22
I finally resolved this myself and the solution was was one of the first things that I had initially tried *sigh*.

Anyway, the solution was to change the wireless interface type in the router software from 802.11 b/g/n to 802.11 b/g and then reboot the Ubuntu machine. I thought it would be enough to just reconnect to the router after making the changes, but I could only get it to work if I rebooted afterwards.

---

