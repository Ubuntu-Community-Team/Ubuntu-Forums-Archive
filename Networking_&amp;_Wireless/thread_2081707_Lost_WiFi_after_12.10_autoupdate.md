---
title: "Lost WiFi after 12.10 autoupdate"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by m808 on 2012-11-07
System: Dell Precision M4500 (laptop)
Ubuntu 12.10 desktop x64.

My wireless was working fine and all of a sudden, it stopped working.

This seemed to coincide with a recent auto-update. Yes, the WiFi hardware switch is on and I've tried rebooting several times.

When plugged into ethernet networking/internet works perfectly.

Here are various outputs of various commands that were suggested:

lspci -nn | grep "Broadcom"
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

iwconfig
eth2      no wireless extensions.

lo        no wireless extensions.

Can't find module with lsmod
lsmod | grep -i broadcom 
lsmod | grep -i wireless 
lsmod | grep -i wifi
lsmod | grep -i bcm

lsb_release -d
Description:	Ubuntu 12.10

uname -mr
3.5.0-18-generic x86_64

snippet from
sudo lshw -C network

  *-network UNCLAIMED
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0

dpkg --get-selections | grep -i 43   
b43-fwcutter					install
firmware-b43-installer				install

(I may have installed these after the problem started)

sudo apt-get install --reinstall bcmwl-kernel-source

Building only for 3.5.0-18-generic
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
update-initramfs: Generating /boot/initrd.img-3.5.0-18-generic

---

### Post by chili555 on 2012-11-07
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.Please see post #8 here: [http://ubuntuforums.org/showthread.php?t=2081537](http://ubuntuforums.org/showthread.php?t=2081537)

---

### Post by m808 on 2012-11-07
> **chili555 said:**
> Please see post #8 here: [http://ubuntuforums.org/showthread.php?t=2081537](http://ubuntuforums.org/showthread.php?t=2081537)

After those commands and a reboot, WiFi is working again!

Thank you so much!

So, was this really just broken by an auto-update? Was this a kernel update? I'm surprised there aren't a lot more people complaining.

---

### Post by chili555 on 2012-11-07
> **m808 said:**
> So, was this really just broken by an auto-update? Was this a kernel update? I'm surprised there aren't a lot more people complaining.There are plenty complaining. Of course, we don't know how many are affected that read and impliment the fix and from whom we never hear.

I am not sure where the trouble lies. I will continue to explore. You might, since you have the hardware and can provide logs, file a bug. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by Cleminuke on 2012-11-07
Hi,

I had the same problem on my Acer Netbook, Aspire One 725. The wifi worked until the recent kernel update it seems. Your instructions worked for me to so thanks chilli555!.

Now to get the Elantech touchpad working!

---

