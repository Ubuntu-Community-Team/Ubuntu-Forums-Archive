---
title: "Wireless issues with Vostro A90 &amp; 12.04"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by justin12 on 2013-08-27
I just did a fresh install of Ubuntu 12.04 on my Vostro A90 (previously was running Ubuntu 8 and the wireless card worked). 

The system is not recognizing the wireless card when I enter "rfkill list all" in the terminal. 

I tried reinstalling the wireless driver - bcmwl-kernel-source - in the Synaptic Package Manager, but that failed with the message "System program problem detected". 

Then based on some other threads I saw, I tried:
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl

```
But on the install of the driver, I see an error:
 ```
Error! Bad return status for module build on kernel: 3.8.0-29-generic (i686)

```

and on the "sudo modprobe wl" command I get this:
```
FATAL: Module wl not found.

```

Any suggestions? Should I try Ubuntu 13? Or try to install an earlier version?

---

### Post by chili555 on 2013-08-27
Please tell us about your wireless card:```
lspci -nn | grep 0280
```

---

### Post by justin12 on 2013-08-27
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

---

### Post by chili555 on 2013-08-27
This message here:> Error! Bad return status for module build on kernel: 3.8.0-29-generic (i686)...is super-secret Ubuntu code for:> The 'Additonal Drivers' utility, also known as jockey, is trying to install the wrong drivers on me! Stop it! Get away from me!!!Let's do the right thing:```
sudo apt-get install firmware-b43-lpphy-installer
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and tell us if it's working now.

---

### Post by justin12 on 2013-08-27
Yes, it's working now, but I'm still getting an error message that pops up after I log in. It's a crash report, and it says "Sorry, a problem occurred while installing software. Package: bcmwl-kernel-source". How can I fix this?

Thanks much for your help!

---

