---
title: "Broadcom Ubuntu 12.04 - Connecting issue"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by TheeEraa on 2012-06-10
I have a Dell Inspiron N7010 on Ubuntu 12.04. I had issues with all the other ubuntus and upon switching to this, the wireless worked. I tried reinstalling the kernel source then modprobe wl. I tried modprobe -r wl then modprobe wl as well. Help would be appreciated.

---

### Post by praseodym on 2012-06-10
Hi,

please show the outputs of:

```
lsmod
rfkill list
lspci -nnk | grep -iA2 net
iwconfig
```

---

### Post by TheeEraa on 2012-06-10
NVM, I am just going to try Debian.

---

### Post by praseodym on 2012-06-10
Your outputs have been shown in the email ;)

```
sudo apt-get install --reinstall linux-headers-$(uname -r) dkms patch fakeroot bcmwl-kernel-source
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and activate the Broadcom driver in "additional drivers"

---

### Post by TheeEraa on 2012-06-11
> **praseodym said:**
> Your outputs have been shown in the email ;)

```
sudo apt-get install --reinstall linux-headers-$(uname -r) dkms patch fakeroot bcmwl-kernel-source
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```Reboot and activate the Broadcom driver in "additional drivers"
Didn't work.

---

### Post by carl4926 on 2012-06-11
Since kernel 3>
Most broadcom work with b43

Anyway, did you reboot?

---

### Post by andyhelloween on 2012-06-11
Just set up Broadcom BCM4313 (14e4:4727) and the solution I found here was to blacklist drivers bcma, brcmsmac and later install bcmwl-kernel-source from Software Center. Last step was to enable STA propietary driver in Additional Drivers.

Wireless works at 100% with no drops!!

---

