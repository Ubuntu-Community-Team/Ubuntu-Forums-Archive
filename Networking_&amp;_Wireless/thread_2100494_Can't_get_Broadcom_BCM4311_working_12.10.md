---
title: "Can't get Broadcom BCM4311 working 12.10"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by moddinati on 2013-01-01
Hello,

Recently installed LUbuntu 12.10.  I can't seem to get my wireless working though.  Here's where I've got to:

```
$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

So it's the Broadcom BCM4311. In LUbuntu, I went to Menu->Preferences->Software Sources->Additional Drivers

The following box is checked:
> Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)

However, the wireless card does not seem to be properly enabled, as I can not get it to find any available networks.

I've tried removing and re-installing bcmwl-kernel-source (and re-booting) to no avail.

On re-installing bcmwl-kernel-source, I get the following errors:

```
wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-21-generic/updates/dkms/

depmod....

DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules

```

One thing I read mentioned something about the linux headers, I have the following headers packages installed:
linux-headers-generic
linux-headers-3.5.0-21-generic
linux-headers-3.5.0-21
linux-headers-3.5.0-17-generic
linux-headers-3.5.0-17

Any suggestions?  Thanks in advance

---

### Post by Hadaka on 2013-01-01
Hi, try this,,

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```

then click the wireless indicator, upper right corner and see
if Enable Wireless is checked.

---

### Post by moddinati on 2013-01-02
Thanks for the reply.

The linux-headers-generic were already installed.  I tried using the --reinstall flag on the headers then tried reinstall the bcmwl-kernel-source.  I get the same errors as above.

When I click on the wireless indicator, the "Enable Networking" check box is selected.  There is no other check boxes.

EDIT:

Also when I run the iwconfig command I get the following:
```
$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
```

---

### Post by Hadaka on 2013-01-02
Hi, here is a possible fix..
[http://askubuntu.com/questions/202688/wifi-doesnt-work-under-quantal](http://askubuntu.com/questions/202688/wifi-doesnt-work-under-quantal)

Enable Wireless and Networking in the pull down should also be checked.

---

### Post by moddinati on 2013-01-02
Installed the linux-source package and re-installed bcmwl-kernel-source.  This is what I get now:

```
wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-21-generic/updates/dkms/

depmod....

DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Error inserting wl (/lib/modules/3.5.0-21-generic/updates/dkms/wl.ko): Invalid argument
FATAL: Error running install command for wl

```

> Enable Wireless and Networking in the pull down should also be checked.

Is this the same for LUbuntu? I only have an "Enable Networking" checkbox. See attached image.

---

### Post by Hadaka on 2013-01-02
Hi, not a lubuntu user...sooo...
lets try this

```
sudo apt-get remove --purge bcmwl-kernel-source 
```
it may say "not found"

```
sudo apt-get update && sudo apt-get upgrade 
```

```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl 
```

---

### Post by bkratz on 2013-01-02
The STA driver really isn't the one to use for 12.10, see this link ( from Dr. Chili )for details

[http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed](http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed)

---

### Post by melwin.a3 on 2013-01-02
Me too have same prob. none of the solution wont work properly because of bloody closed source drivers. BROADCOM BCM4312 also does not support much linux. Thanks for linux developers..

if u belive in luck
try this

sudo modprobe -r b43 ssb wl
sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install build-essential dkms linux-headers-generic
sudo apt-get install bcmwl-kernel-source

---

### Post by moddinati on 2013-01-02
> **bkratz said:**
> The STA driver really isn't the one to use for 12.10, see this link ( from Dr. Chili )for details

[http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed](http://askubuntu.com/questions/228821/bcm4311-wireless-not-working-with-drivers-installed)

Thanks! This got it working.  Only problem is, I have to manually type "sudo modprobe b43" on rebooting the machine.  I checked the blacklist, nothing that seemed obvious was blacklisted (but that may not be saying much).

For anyone who comes across this thread, I re-posting the solution below:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by Hadaka on 2013-01-03
Hi, glad its almost better, 

```
sudo gedit /etc/modules 
```type      b43    as the last line, save and close.
boot and it will load the the driver for you.

@melwin.a3 thanks !

---

