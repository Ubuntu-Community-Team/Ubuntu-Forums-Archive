---
title: "Broadcom BCM4309 OR D-Link DWA-652  Help, please"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by BEND IT 7 on 2009-06-05
Hi, all.

I just installed Ubuntu 8.04 on my brother's laptop as the only OS. 

It is a Dell with a Broadcom BCM4309 built-in Wifi card AND a D-Link DWA-652 XTREME N Adapter in the tray.

I can not get EITHER card to connect to our wifi network.

Help, please?

---

### Post by Ayuthia on 2009-06-05
> **BEND IT 7 said:**
> Hi, all.

I just installed Ubuntu 8.04 on my brother's laptop as the only OS. 

It is a Dell with a Broadcom BCM4309 built-in Wifi card AND a D-Link DWA-652 XTREME N Adapter in the tray.

I can not get EITHER card to connect to our wifi network.

Help, please?
If you are able to get a wired connection in Ubuntu, you can try to install b43-fwcutter (This is for the 4309 card):
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
However, I don't recall b43legacy working that great in Hardy.

---

### Post by BEND IT 7 on 2009-06-10
> **Ayuthia said:**
> If you are able to get a wired connection in Ubuntu, you can try to install b43-fwcutter (This is for the 4309 card):
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
However, I don't recall b43legacy working that great in Hardy.

That worked flawlessly.  It worked on the first try & no extra setup was needed...it loaded surprisingly fast, too.

I just ran the terminal script you suggested and then turned on the hardware driver.  The 4309 card now works probably better overall than it did in XP.

Thank you!

---

### Post by slinkydonkey on 2009-12-22
Hi I am having the same problem with a Dell Lattitude D400 its using same wireless Broadcom BCM4309 im using Ubuntu 9.10 but it still does not work can you help?

---

