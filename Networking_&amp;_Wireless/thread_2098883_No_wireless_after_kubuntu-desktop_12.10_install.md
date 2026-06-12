---
title: "No wireless after kubuntu-desktop 12.10 install"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by roadracer on 2012-12-27
After installing kubuntu-desktop 12.10 64-bit, there is no wireless (not even wlan0 device) in Ubuntu or Kubuntu.  No wired lan either.  Dual booting with Win 8, but wireless works fine there--just not linux.  

lenovo G580 with Broadcom BCM4313.  Any ideas?

---

### Post by daslinkard on 2012-12-30
> **roadracer said:**
> After installing kubuntu-desktop 12.10 64-bit, there is no wireless (not even wlan0 device) in Ubuntu or Kubuntu.  No wired lan either.  Dual booting with Win 8, but wireless works fine there--just not linux.  

lenovo G580 with Broadcom BCM4313.  Any ideas?

Here is a [link]("http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working") that might work for you in getting your Broadcom card to work. Basically it is stating to do the following:

```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Afterwards install the following packages
  ```
sudo apt-get install b43-fwcutter firmware-b43-installer
``` ```
sudo echo b43 >> /etc/modules
```
then reboot and check if your card is found. (You can try by hand without rebooting. If you currently use the wl driver execute
  ```
sudo modprobe -r wl 
``````
sudo modprobe b43
```

---

