---
title: "RTL8191SEvB wlan UNCLAIMED even after driver install"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by Deadboy420 on 2011-04-06
So, here's my situation:  My rtl8191se pci card was working fine. Then I bought an ALFA usb wifi adaptor. Both were working fine. Then I decided to patch my drivers via

```
Download drivers: [Compat-wireless-aircrack-maverick-patched ]("http://www.janoweb.net/drivers-patch/compat-wireless-aircrack-maverick-patched.tar.bz2") 
 
sudo rmmod rtl8187 zd1211rw iwl3945 ath5k rt73usb rt2800usb mac80211 cfg80211 
sudo mkdir /usr/src/drivers 
cd /usr/src/drivers 
sudo tar jxvf compat-wireless-aircrack-maverick-patched.tar.bz2 
cd compat-wireless-aircrack-maverick-patched 
sudo make 
sudo make install 
sudo make unload 
 
sudo modprobe rtl8187 
```

From this point my rtl8191se pci card is no longer recognized (shown as UNCLAIMED). So, I downloaded the driver from realtek's website and reinstalled, but it still is listed as UNCLAIMED.

---

