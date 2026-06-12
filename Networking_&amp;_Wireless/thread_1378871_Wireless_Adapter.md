---
title: "Wireless Adapter"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by supernova42 on 2010-01-11
I am currently using an old wireless adapter and Ubuntu has a driver for it.  However I do not have the windows driver for it making my dual-boot half useless.  Is there a way I can find out what adapter i have?  Thank you in advance.

---

### Post by Cuba71 on 2010-01-11
If it's a usb adapter, start with *lsusb*

---

### Post by supernova42 on 2010-01-12
no its some other kind.  The port says "wireless LAN antenna".

---

### Post by designingpatrick on 2010-01-14
I'm looking to purchase a wireless usb adapter, are there any which can be recommended for Ubuntu? I have one currently (hawking hwu8dda), but the company doesn't seem make drivers for the operating system environment.

Any recommended wireless usb adapters for Ubuntu?

---

### Post by bkratz on 2010-01-14
> **supernova42 said:**
> no its some other kind.  The port says "wireless LAN antenna".

If it is internal just type 

lspci in the terminal

(LSPCI in lowercase)

and post the output here or simply decode it yourself

---

