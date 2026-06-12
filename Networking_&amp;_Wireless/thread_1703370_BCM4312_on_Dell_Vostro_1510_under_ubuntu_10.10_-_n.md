---
title: "BCM4312 on Dell Vostro 1510 under ubuntu 10.10 - no SECURE Wireless (unsecure ok)"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by montango on 2011-03-09
I have tried a lot of solutions proposed on forums, but I'm still unable to connect to a secure wireless network (the correct password is not recongnized, after a while it prompts again for it). Connection through unsecure wireless networs is fine, as is wired LAN

Here are my wireless card details:

06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
        Subsystem: Dell Wireless 1395 WLAN Mini-Card
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, ssb

I have installed the driver from broadcom, but I think it also works with the b43 driver. I've tried many things:

first I removed the b43 and installed the broadcom driver; no change, but after a certain number of reboots I didn't connect at all, so I reinstalled the b43 driver and I could connect to an unsecure wl network.

Could it be a problem with the "security module" rather than with the driver itself?  

I already had this problem in ubuntu 9.10 after upgrade, I followed the instructions on some forum, then I noticed that the recommended module ieee80211(I'm not sure of the name anymore) didn't work, I installed instead another one (lib80211) and it worked.

Now I have the lib80211, obviously the same hardware, but I installed ubuntu10.10 brutally (after upgrading from 9.10 to 10.04 the graphics card was not recognized anymore, see [here]("http://ubuntuforums.org/showthread.php?t=1701174"), so I had no choice but to install ubuntu 10.10 from scratch). Now I have this wireless problem.

I repeat that the passord I gave for that secure wl network is correct (it is a huge sequence of letters and digits, that I copied from a file, so there is no typing error), but it is nonetheless not accepted.

What can I do?

Thanks in advance

---

### Post by steaksauce on 2011-03-09
I have an Inspiron 1525 that comes with a broadcom 4312 card and Ubuntu recognizes my card, and allows me to connect to secured and un-secured networks using a fresh start without me doing anything. What all have you done for your card in terms of drivers and support?

---

### Post by montango on 2011-03-09
In the original, freshly installed ubuntu, I had wired internet and unsecure wireless from the beginning. As it didn't want to connect to a secure wl network, I started to apply various recipes, from which the only "benefit" was that, at some point, I lost the unsecure wireless access too. 

Now, I have the same internet capabilities as at the beginning, but I cannot guarantee that the internal configuration is the initial one. 

The procedures I followed were complicated, and I don't remember the details. I suppose some commands can shed some light upon my settings, modules, etc., but my linux knowledge is very thin...

---

