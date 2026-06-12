---
title: "Broadcom B43 Dell D600"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by oldcelt on 2009-01-28
I've installed 8.10 (dual boot with XP Pro)and everything is fine except for wireless networking.

I have a Netgear modem/router which serves my whole LAN (ethernet & wireless).

In the Ubuntu Hardware Drivers panel I see the Broadcom B43 Wireless Driver and it says 'This driver is activated and currently in use'.  However, I can't see where to find the wireless network so I can connect to it.

Help for a complete Ubuntu tyro please?

Ken

---

### Post by Ayuthia on 2009-01-28
> **oldcelt said:**
> I've installed 8.10 (dual boot with XP Pro)and everything is fine except for wireless networking.

I have a Netgear modem/router which serves my whole LAN (ethernet & wireless).

In the Ubuntu Hardware Drivers panel I see the Broadcom B43 Wireless Driver and it says 'This driver is activated and currently in use'.  However, I can't see where to find the wireless network so I can connect to it.

Help for a complete Ubuntu tyro please?

Ken

Can you go into the Terminal and post the results of:
```
lspci -nn
lshw -C network
```
We need to know the make, model, and chipset of your wireless card along with what wired card you have.  The Broadcom card has a few different wireless modules available in Linux based on which card you have and some can cause conflicts with others.

---

### Post by oldcelt on 2009-01-28
Thanks for the input.  It is sorted in fact.  I missed seeing the tiny icon in the top taskbar (OK, I know I'm using Windows terminology) which was telling me I needed a reboot.

Re-booted and all is well.

Ken

---

