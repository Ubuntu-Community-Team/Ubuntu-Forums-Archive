---
title: "Gateway NV53 - Wireless Issue"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by slooksterpsv on 2010-03-21
I've attached all the required information to a txt file attached to this thread.

here's the issue: I can login, connect wirelessly and it works great for about 10 min. next thing I know I'm disconnected from the wireless network and it won't connect. I have to use a USB Wifi card to get it to work. Also, it won't even attempt the connection after its disconnected.

It has a Wireless b/g/n card integrated into the Gateway.

Let me know what to try, what other information you  need, or if you have a fix, that would be great too. The OS is 32-bit that I'm running but it came with Windows 7 64-bit - think 64-bit would make a difference? - It's a WUBI installation too.

EDIT: Now it's here, it wouldn't take the txt file cause it was too large so I had to zip it.

---

### Post by chili555 on 2010-03-21
> I've attached all the required information to a txt file attached to this thread.I don't see an attachment.

---

### Post by slooksterpsv on 2010-03-21
It's been fixed, here's how:
=D I changed the blacklist and added ath_hal and updated the kernel from 14 to 20. It's working perfectly now!

---

### Post by CashCollector on 2010-05-06
Hey man, I have the exact model laptop and I have the exact problem. I need to know exactly how you do this fix please?

> **slooksterpsv said:**
> It's been fixed, here's how:
=D I changed the blacklist and added ath_hal and updated the kernel from 14 to 20. It's working perfectly now!

---

### Post by CashCollector on 2010-05-06
i hope somebody can help me quick plz

---

### Post by CashCollector on 2010-05-13
This is defiantly a hardware/driver issue, as I'm having the same exact problem on Windows 7. Still no fix if anybody knows anything?

---

### Post by chili555 on 2010-05-13
He says he blacklisted ath_hal. In reviewing his *lsmod*, I can't see that it was loaded in the first place. Do you have an Atheros card? Learn with:```
lspci -nn | grep Network
```Which Atheros drivers are loaded?```
lsmod | grep ath
```

---

### Post by CashCollector on 2010-05-18
> **chili555 said:**
> He says he blacklisted ath_hal. In reviewing his *lsmod*, I can't see that it was loaded in the first place. Do you have an Atheros card? Learn with:```
lspci -nn | grep Network
```Which Atheros drivers are loaded?```
lsmod | grep ath
```
I wonder if you seen that said that I am NOT using Ubuntu?

---

### Post by snypa on 2010-07-31
> **CashCollector said:**
> This is defiantly a hardware/driver issue, as I'm having the same exact problem on Windows 7. Still no fix if anybody knows anything?
 
Did you ever find a fix for your Gateway NV53 laptop wireless connection issue.? I picked one up other day and it keeps dropping my wireless. Let me know. Thanx

---

### Post by drklunk on 2010-08-15
Found this on Best Buy's website, it was part of one of the reviews: 

> I have bought this 4 times now. Two for work, one for a friend, and one for myself. Almost all of them have Ubuntu Linux on them and it works great.

Notes for Ubuntu 9.10: This laptop works great with Ubuntu but needs a few minor adjustments:

1) Use the 32-bit version, and once installed, add the 'pae' kernel, headers, and modules from Synaptic (just search for "pae"). This allows full access to all 4GB of RAM.

2) Install the ATI driver, which Ubuntu will tell you to do via "Hardware Drivers" - this will get desktop effects working.

3) Also install "linux-backports-modules-wireless-karmic-generic-pae" to improve wireless signal strength and prevent dropouts

4) add "acer-wmi" to /etc/modules to allow wireless toggle switch to work properly.

5) Touchpad disable button fails to re-enable touchpad, to fix this add kernel boot parameter "i8042.nomux" in /etc/default/grub right after the default boot parameters.
look for this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
change to this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux"

Give that a shot, pretty sure this fixes the wireless

---

### Post by slooksterpsv on 2010-08-15
Hmm I wonder why mine just works. I think the kernel update helped a lot of the issues I was having; could be the router I use as well (Netopia Qwest DSL Modem/Router).

Have you guys updated your kernel to the newest one they have in update manager? I think its 2.6.32.26 - I could be wrong on that.

---

