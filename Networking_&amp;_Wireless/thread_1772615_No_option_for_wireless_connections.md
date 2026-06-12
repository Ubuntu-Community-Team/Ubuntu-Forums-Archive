---
title: "No option for wireless connections"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by Bryn1987 on 2011-05-31
I own an hp dv9000 laptop, it comes with a Broadcom STA Wireless card... I currently have my laptop connected to the internet through a wired connection, but there is no option at all for wireless.

I've already installed the Additional Drivers to install the Broadcom STA Wireless Drivers, and after I reset, there was no difference, no option to choose wireless instead.

Any help please?

---

### Post by chili555 on 2011-06-01
Let's do some diagnosis. Please open a terminal and run and post:```
lspci -nn | grep -i 14e4
dmesg | grep -e b43 -e wl
```Thanks.

---

### Post by timobis on 2012-02-02
I'm having the same problem...
 
I ran:
 
"lspci -nn | grep -i 14e4"
 
showing:
 
"0b:00.0 Network controller [0280]: Broadcom corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
 
but after running the second command nothing showed up

---

### Post by chili555 on 2012-02-02
> **timobis said:**
> I'm having the same problem...
 
I ran:
 
"lspci -nn | grep -i 14e4"
 
showing:
 
"0b:00.0 Network controller [0280]: Broadcom corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
 
but after running the second command nothing showed upCan you temporarily get a wired ethernet connection and do:```
sudo apt-get install dkms bcmwl-kernel-source
sudo modprobe wl
```Disconnect the ethernet cable and your wireless should be working.

---

