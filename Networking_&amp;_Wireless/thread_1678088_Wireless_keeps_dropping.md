---
title: "Wireless keeps dropping"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Skyhawk5421 on 2011-01-29
Hello all. I have xubuntu 10.10 and after like a half hour or an hour of using my laptop the internet will just die.

I didn't have this problem in 10.04, and I have since done a clean install which also didn't help

I also switched from the standard network-manager to wicd for the default connection manager but same problem. 

When it dies, it will say its connected but nothing will be able to access the internet. And when I try to reconnect it gets stuck ad "obtaining IP address" forever

I've heard of other people having similar problems but I haven't seen any solutions

Any ideas?

---

### Post by SaintDanBert on 2011-01-29
A possible work around ...

[list]
[*]connect to wire network
(you won't be able to use wifi for a short time)
[*]completely remove **network-manager**
[*]reboot
[*]your wire network should be there after system start
[*]install the **wicd** package
[*]reboot
[/list]
Wicd is a replacement for network-manager. My troubles with dropped connections ended when I made the change.

Depending on your kernel edition and the wireless parts in use and the driver module edition used there are known driver defects -- bugs.
I did the wicd swap and my troubles "went away". I liked wicd and continue to use it even after several ubuntu distro updates.

Bonne chance,
~~~ 0;-Dan

---

### Post by Skyhawk5421 on 2011-01-29
I did that but I believe I used my wireless to download wicd...so maybe it didn't uninstall completely? I'll try removing everything and installing wicd before I boot gdm

---

### Post by SaintDanBert on 2011-01-29
I used **apt-get ... purge** with network-manager.
You really need to get rid of network-manager software.
The data and configuration details may hang around without trouble.

In spite of this being linux, I did remove-reboot more often than I would normally then used **ps** looking for running remnants.

Bonne chance,
~~~ 0;-Dan

---

### Post by Skyhawk5421 on 2011-01-29
> **SaintDanBert said:**
> I used **apt-get ... purge** with network-manager.
You really need to get rid of network-manager software.
The data and configuration details may hang around without trouble.

In spite of this being linux, I did remove-reboot more often than I would normally then used **ps** looking for running remnants.

Bonne chance,
~~~ 0;-Dan

Damn thats thorough. I've never used purge before but it said it removed something...0 bytes of something. We'll see

---

### Post by bkline on 2011-11-14
> **SaintDanBert said:**
> A possible work around ...

[list]
[*]connect to wire network
(you won't be able to use wifi for a short time)
[*]completely remove **network-manager**
[*]reboot
[*]your wire network should be there after system start
[*]install the **wicd** package
[*]reboot
[/list]


Didn't work that way for me.  Without network-manager, the wired network didn't come up (not surprising).  I had to pull down the wicd packages on another system, drop them onto a memory stick, move the memory stick to the target system, and install from those local copies.

---

