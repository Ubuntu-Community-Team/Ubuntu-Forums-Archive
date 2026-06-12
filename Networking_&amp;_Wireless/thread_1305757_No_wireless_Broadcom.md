---
title: "No wireless Broadcom"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by ubuntu27 on 2009-10-30
Hello. I just made a Fresh Install of Ubuntu Karmic 64-bit with ext4.

I am having trouble with wireless internet. I have Broadcom chipset.

I have installed "bcmwl-kernel-source" as I read in many threads. But it did not work. No drivers is showing at System-->Hardware Drivers.

I cannot connect to the Internet with Ethernet since there is no-one who uses that. I always use wireless.

lspci  shows that it has Broadcom 4312

---

### Post by pro003 on 2009-10-30
try this thread  [http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632)

---

### Post by Ayuthia on 2009-10-30
Can you check and see if the following file exists:
/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko

```
ls /lib/modules/2.6.31-14-generic/updates/dkms/wl.ko
```
If it is found, please try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```

---

### Post by ubuntu27 on 2009-10-30
THank you guys. The wireless is now fixed.
I have been doing many random things to get it to work.

*Downloading KDMS and installing and reinstalling
*Restarting the computer for more than 7 times
*Going to the Hardware drivers multiple times, no drivers appeared
*Inserting the Karmic Desktop CD and do the same thing.
*install and reinstall diifferent packages..

*And behold! Suddenly a driver appears in the Hardware Drivers.

---

### Post by addtoqueue on 2009-10-30
> **Ayuthia said:**
> Can you check and see if the following file exists:
/lib/modules/2.6.31-14-generic/updates/dkms/wl.ko

```
ls /lib/modules/2.6.31-14-generic/updates/dkms/wl.ko
```If it is found, please try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```

This didn't work for me and I'm having the same problem as Ubuntu27.  I did the things he/she did too with a laptop Broadcom chipset.:  "I have installed "bcmwl-kernel-source" as I read in many threads. But it did not work. No drivers is showing at System-->Hardware Drivers."

The output of the sudo iwlist scan is:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Thanks for any help provided.

---

### Post by addtoqueue on 2009-10-30
I just noticed that also, the output of lspci doesn't list any Network controller whereas it did before upgrading (downgrading) to 9.10.  Now it only list the Ethernet controllers.

---

### Post by spyderpride on 2009-10-30
> **ubuntu27 said:**
> THank you guys. The wireless is now fixed.
I have been doing many random things to get it to work.

*Downloading KDMS and installing and reinstalling
*Restarting the computer for more than 7 times
*Going to the Hardware drivers multiple times, no drivers appeared
*Inserting the Karmic Desktop CD and do the same thing.
*install and reinstall diifferent packages..

*And behold! Suddenly a driver appears in the Hardware Drivers.
Any idea what made it work? I am trying to help a friend with this same issue.

---

### Post by richard270384 on 2009-11-23
I got my working.

I found that these lines
> 
sudo modprobe wl
sudo iwlist scan

activate my wireless (broadcom on Inspiron 1525). So I inserted 'wl' into the file /etc/modprobe - rebooted and all appears to be well.

The only other changes I can remember making to my laptop since the fresh install of 9.10 was to activate the Broadcom STA Wireless Driver in System->Administration->Hardware Drivers, and to install all updates using update manager.

Hope this works for others as well.

---

