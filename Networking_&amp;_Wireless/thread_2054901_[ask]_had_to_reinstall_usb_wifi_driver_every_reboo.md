---
title: "[ask] had to reinstall usb wifi driver every reboot"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by Paleskin on 2012-09-08
I got Edimax EW-7811Un usb wifi adapter, I just upgraded to the latest driver from realtek website, I downloaded the driver file RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622 from realtek website, and I ran "sudo bash install.sh", then I ran "sudo gedit /etc/modprobe.d/blacklist.conf" and put the line "blacklist rtl8192cu"

It installed and working fine, but the weird thing is, on every reboot the device is missing and I had to reinstall it, so the device can be detected and used

Is there a solution for this ?



Thanks

---

### Post by vasilbelarus on 2012-09-08
You can use script which will re-eject device.
But you should better try to find solution from internet.

---

### Post by steeldriver on 2012-09-08
If it's not getting loaded automatically, you may need to add the module to /etc/modules so that it's loaded at boot time

**NB I'm guessing you built the 8192cu module from Realtek - adjust the module name as appropriate if that is not the case**

```
echo "8192cu" | sudo tee -a /etc/modules
```If you're not sure which module the device is using you can use

```
nm-tool | grep 'Driver'
```

---

### Post by Paleskin on 2012-09-08
> **steeldriver said:**
> If it's not getting loaded automatically, you may need to add the module to /etc/modules so that it's loaded at boot time

**NB I'm guessing you built the 8192cu module from Realtek - adjust the module name as appropriate if that is not the case**

```
echo "8192cu" | sudo tee -a /etc/modules
```If you're not sure which module the device is using you can use

```
nm-tool | grep 'Driver'
```

It works, thanks a lot sir ^____^

SOLVED

---

### Post by rehnis on 2012-09-08
I had pretty much the same problem, I had to re-install the realtek drivers after each restard to get the wireless network to run at normal speed. This solved my problem, I was just going to make a post about it, thanks alot. The driver name for me was &quot;rtl8192cu&quot;

---

### Post by garthos on 2012-10-12
```
nm-tool | grep 'Driver'
```[/QUOTE]

many thanks, this also resolved my problem. Although nm-tool incorrectly identified my driver as rtl8192cu when infact its 8192cu

$ nm-tool | grep 'Driver'
  Driver:            e100
  Driver:            rtl8192cu

$ lsmod | grep 8192
8192cu                502485  0

---

