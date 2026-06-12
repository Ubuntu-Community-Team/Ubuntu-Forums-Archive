---
title: "Broadcom Wireless connection issue"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by linux-tn on 2010-07-08
I have installed the driver of my Broadcom Wireless card BCM4312 ( Acer extenza 5620 laptop)
and when i try to connect to my wireless connection it just try to connect for a while and then go offline
i tested another usb wireless card and still no success

$lspci
```
# lspci | grep Broadcom
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

# iwconfig wlan0
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

I am on Ubuntu 10.04 LTS

---

### Post by Zip247 on 2010-07-08
the ubuntu help wiki has a page for broadcom 43xx's

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

hope it can help you!!

---

### Post by TBABill on 2010-07-08
I have the same laptop. Plug it into your router and allow it to do a system update. Once it updates it will also prompt you to use the proprietary hardware driver. While still plugged into the router directly, say yes and allow it to download and install the Broadcom driver. You will only do this once (unless you install the OS again or upgrade to the next OS) but you do have to be plugged in to get the driver. 
 
If you are not prompted to install the proprietary driver, just go to settings/admin/hardware and it will probe the system and offer you the opportunity to install the driver.
 
Works great, just a pain. Plug in, download, install, reboot, enjoy.

---

### Post by linux-tn on 2010-07-08
i think that the problem isn't with the driver ( i have installed it manually from the official broadcom's website)
so how to uninstall the driver and use the method described by TBABill.thanks for the help guys :)

---

