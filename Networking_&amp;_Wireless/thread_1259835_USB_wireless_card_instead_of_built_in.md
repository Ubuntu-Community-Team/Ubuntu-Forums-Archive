---
title: "USB wireless card instead of built in?"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by slughappy1 on 2009-09-06
Is there a way to use my Belkin USB Wireless Adaptor F6D4050 v1 instead of my built in wireless card?

---

### Post by nandemonai on 2009-09-07
Either disable the internal card with the switch on the laptop (if applicable), disable it in BIOS or blacklist the module used by the internal adaptor.

---

### Post by rogerdean on 2009-09-23
Hi all
How would I blacklist the driver for my internal wireless? I guess I'll have to do some info-gathering first to know what hardware I have - what command would I run for that?
Cheers!
Roger

---

### Post by t0mppa on 2009-09-23
First run **lshw -C network** and pick up your wireless interface from there. It shows what driver (and what the module name for that one is) your interface is using on the *configuration* line, which you can then blacklist by running **echo blacklist <module_name> | sudo tee -a /etc/modprobe.d/blacklist.conf**

That will stop it from loading on future boots and if you want to unload the driver right now, run **sudo modprobe -r <module_name>**

---

### Post by rogerdean on 2009-09-23
Perfect, thanks very much!

---

