---
title: "Acer Aspire 5750Z broadcom wireless problems"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by opensourcevegan on 2013-02-24
Hello!

I am running Ubuntu 12.10 and I'm having problems with recognizing wireless networks. I am somewhat confused, as during installation, Ubuntu successfully recognized my wireless card and was able to display wireless networks. After reboot, the list is completely gone from Network Manager.

I have already tried the fix suggested [here]("http://ubuntuforums.org/showthread.php?t=1967515"), and it didn't help.

rfkill list
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```    lspci -nn | grep 0280
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
```sudo apt-get install --reinstall bcmwl-kernel-source
```
[sudo] password for opensourcevegan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,181 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/restricted bcmwl-kernel-source amd64 5.100.82.112+bdcom-0ubuntu3 [1,181 kB]
Fetched 1,181 kB in 4s (281 kB/s)                
(Reading database ... 147103 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-25-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic

```sudo modprobe wl
```
FATAL: Module wl not found.

```Thanks in advance for your help. I really have no idea what I'm doing. ;)

~ OSV

---

### Post by chili555 on 2013-02-24
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.Uh oh...

Hook up the ethernet a few more minutes and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by opensourcevegan on 2013-02-24
> **chili555 said:**
> Uh oh...

Hook up the ethernet a few more minutes and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
Thank you very much!
I have no idea why those headers weren't already installed, but they weren't. Following those steps fixed my problem.

Thanks for the help. It is very much appreciated! :)

---

### Post by chili555 on 2013-02-24
Happy to help. Glad it's working!

---

