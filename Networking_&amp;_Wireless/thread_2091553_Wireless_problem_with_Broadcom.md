---
title: "Wireless problem with Broadcom"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by sauzer00 on 2012-12-05
I read some thread and i tryed something but doesent works

I have an acer aspire 5755G
and my wireless card should be a a broadcome 57765 

I installed ubuntu 12.10 but doesent reconize any wireless connection.

Alredy update the system through an ethernet cable but i really need to get my wireless working 

Any ideas how to fix it ?

Thanks for any advice 
Regards
Alessandro

---

### Post by chili555 on 2012-12-05
We need more details about your wireless card. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by sauzer00 on 2012-12-05
this is the output

sauzer00@sauzer00-Aspire-5755G:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

---

### Post by chili555 on 2012-12-05
> **sauzer00 said:**
> this is the output

sauzer00@sauzer00-Aspire-5755G:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [[COLOR="Red"]14e4:4358[/COLOR]]With the ethernet connected, please do:```
sudo apt-get install linux-headers-generic bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and let us hear your report.

---

### Post by sauzer00 on 2012-12-05
at the first command the answer is this 
E: Impossibile trovare il pacchetto bcmwl-kernel-sourc

means impossible to find the package 

at the second
 
FATAL: Module wl not found.

Look like that somthing is missing :confused:

---

### Post by sauzer00 on 2012-12-05
btw probably i just did a retard action 
after i discoverd that my card was 4322

looking on some tutorial, i tryed to install the STA driver
with thoose commands
sudo apt-get update sudo apt-get install bcmwl-kernel-source

but nothing happend i also had come kind of errors

DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
update-initramfs: deferring update (trigger activated)
Elaborazione dei trigger per initramfs-tools...
update-initramfs: Generating /boot/initrd.img-3.5.0-19-generic

---

### Post by sauzer00 on 2012-12-05
Ok i restart the PC and it works :)

---

### Post by chili555 on 2012-12-05
Glad it's working! Please use thread tools at the top to mark Solved.

---

