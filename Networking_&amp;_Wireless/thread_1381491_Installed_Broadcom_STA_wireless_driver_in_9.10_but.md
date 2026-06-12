---
title: "Installed Broadcom STA wireless driver in 9.10 but still can't get online"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by atravnic on 2010-01-14
Installed 9.10 side-by-side with Vista, then installed the Broadcom STA wireless driver, rebooted to activate it -- no luck, no connection, neither wireless nor wired. Did this several times. :( Getting online in Vista works fine. Help!     ...Fred

Here's the system I'm using:
HP tx2500z laptop
Vista Home Premium SP1
AMD Turion X2 Dual-Core Mobile processor RM
ATI Radeon HD 3200 graphics card
Broadcom 4322AG 802.11a/b/g/draft-n WiFi adapter
Realtek RTL 8186C (P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)

---

### Post by bigal50 on 2010-01-14
I would start over and install 9.10 again. Then using ethernet open a terminal and enter the following
```
sudo appitude update
sudo appitude upgrade
```
When it is finished reboot and then install and activate the STA Broadcom driver again. Reboot and it should work.

This works for me on my Vostro 1520 with the Broadcom 4312

---

### Post by atravnic on 2010-01-18
Bigal50, I'd like to thank you for your help. In the course of working through this problems I learned a lot and, most significantly, overcame some of my apprehension of getting down and dirty with Ubuntu.   ...Fred

---

### Post by Kafubie on 2010-01-18
Hey bigal50, i will do what you said, because i have problems with broadcom 4312 too. Im excited to try it out.

---

### Post by smflorkey on 2010-01-20
Thanks, bigal50, but I did that (a little differently) and still don't get a wireless connection.

Lenovo U330, Windows XP (waiting for the "free" Windows 7 CD from Lenovo)

Ran wubi for a fairly painless installation.  WinXP was connected wirelessly for the initial installation.  Tried to connect Ubuntu 9.10 the same way and got nothing.  The wired connection works well -- used the Update Manager to get all 199 updates. :-)  Also got the Broadcom STA driver on the wired connection; installed it; restarted; no joy.

lspci shows

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

My Linksys WRT54GL is set for WPA2 (personal) using TKIP+AES, renewing the group key every hour (3600 seconds).  What do I need to do to get Ubuntu 9.10 connected to this?

Thanks, 
Steve

---

