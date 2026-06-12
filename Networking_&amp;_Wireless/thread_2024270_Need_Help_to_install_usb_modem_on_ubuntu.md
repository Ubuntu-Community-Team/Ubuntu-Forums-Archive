---
title: "Need Help to install usb modem on ubuntu"
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by shabujRock on 2012-07-13
I cannot use my usb modem on my laptop. so if anyone can know the solution please te me or reply how could fix it.

---

### Post by Cheesehead on 2012-07-13
Unplug it. Then plug it in again.

Then post here the last 10 lines of /var/log/dmesg

Then post here the result of the command [FONT="Courier New"]lsusb -v[/FONT]

---

### Post by ub07 on 2012-07-13
> **shabujRock said:**
> I cannot use my usb modem on my laptop. so if anyone can know the solution please te me or reply how could fix it.

What kind of USB modem is it? Mobile broadband or dial-up?

---

### Post by shabujRock on 2012-07-14
> **ub07 said:**
> What kind of USB modem is it? Mobile broadband or dial-up?

Bro its dialup modem. any help? please...............:)

---

### Post by ub07 on 2012-07-14
I'm going to try to walk you through this because I've just been through it myself.

First, type:

> 

lsusb



See if you can see your usb modem listed. If not we will have some work to do.

What usb modem (make, model) do you have?

---

