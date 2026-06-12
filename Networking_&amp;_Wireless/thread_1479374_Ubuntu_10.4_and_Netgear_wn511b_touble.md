---
title: "Ubuntu 10.4 and Netgear wn511b touble"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by 3t- on 2010-05-10
New to Linux so be gentle.

Loaded Ubuntu 10.4lucid on TransPort NX Mobile Pentium II, 328MiB,

Using Netgear Rangemax wn511b. with Broadcom STA wirless driver. bcm43gx.

Boot computer and network manager shos "no network devices available" 

Run system/administration/hardware drivers and the Broadcom STA driver shows up (only one that shows up)  REMOVE and then ACTIVATE and the network manager sees it and connects fine.  

Shut down computer,  restart and no device.  I am forced to Remove and Activate each time I start the computer.  

Is there a way to set this driver to be found and run at computer start. 

Tell me what you need to see from the Terminal (tell me what command to use)

Thanks

---

### Post by chili555 on 2010-05-10
From the terminal, when it's working:```
lsmod | grep -e wl -e b43
```Thanks.

---

### Post by 3t- on 2010-05-10
tim@tim-desktop:~$  lsmod | grep -e wl -e b43
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
tim@tim-desktop:~$

---

### Post by chili555 on 2010-05-10
Please do this:```
sudo su
echo wl >> /etc/modules
exit
```Reboot and let us know.

---

### Post by 3t- on 2010-05-10
chili,

done and works great.  network manager loads and connects to wireless at start up.

thanks you very much.

can you recommend a very basic text for a beginner to Linux and Ubuntu.

---

