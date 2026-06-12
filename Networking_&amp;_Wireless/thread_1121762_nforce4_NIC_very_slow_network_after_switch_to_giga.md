---
title: "nforce4 NIC: very slow network after switch to gigabit"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by yesyes on 2009-04-10
Hi all!

I'm running Ubuntu 8.10 AMD64 on a MSI K8N Neo4 mainboard (MSI N1996) with an AMD Athlon 64 X2 4600+ and 2GB RAM.

I have recently bought an 8port Gigabit switch and connected it to the on-board Gigabit nforce4 NIC. Now I'm experiencing extremely slow local LAN, for instance when accessing my external LAN attached hard drive. It is in fact so slow that most of the time the file browser goes grey (as in program not responding) when it loads the directory listing of the external drive. When copying files across it does it at modem speeds, i.e. 5-10 kBytes/s !!! Rather annoying...

When I was still running 100Mbit LAN through the switch in my ADSL router it was much faster.
Internet access is also slower than it was before.

The speed of the external drive is fine when accessed from my girlfriend's WinXP PC. So I doubt it's the NAS drive. 

Are there any known issues with nforce4 Gigabit NIC's?
Is there a way to configure it down to 100Mbit for a test? I could find no such option in Network Manager. (I know this option exists in Win XP for example).
Any other ideas?

The driver used for the NIC is "forcedeth".
If you need more info, such as versions, please let me know including how to get them. I'm relatively new to Linux.

---

### Post by wkulecz on 2009-04-10
If you are reusing your original cables, are you sure they are up to gigabit speeds?

I recently upgraded to a gigabit wireless draft-N router and the Ubuntu 6.06 to Windows 2000 Samba sharing speeds increased dramatically.  The draft N speedup over wireless G was noticible, but not so dramatic.

I'm using an Nforce MB (don't recall its numeral) and similar processor, but am using 32-bit Ubuntu 6.06 on the wired gigabit and Ubuntu 8.04 on the wireless.

My cat 5 cables seem to work fine, but I've heard not all do, so I'd try some cat 6 cables first before I'd go looking for driver bugs.

--wally.

---

### Post by yesyes on 2009-04-27
Thanks for that and sorry about the delay. (I've recently moved house and I'm busy with home improvement)

In the meantime I have installed another PCIe Gigabit card (Marvel 88E8053 chip). That one works just fine and I get the expected speeds. I'm using the same cable (just plugged it from one NIC to the other). So it can't really be the cable. (Although I'm sure it could have been the cable...).

So I still think that there's something wrong with the nvidia gigabit chip or its driver...

But anyway, problem solved for me. :)

---

