---
title: "ath9k_htc driver - ar9271.fw download failed error"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by Nw01f on 2010-11-07
Hi all,

I followed this blog post:

[http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/](http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/)

to setup my TP-Link TL-WN722N 150M USB WIFI Adapter for my 64bit ubuntu 10.04 server.

All the things go well but after I reboot I cannot see my wlan0 device presents.

Here are the error messages I get after installed the driver:
```

dmesg | grep ath9k

[ 1499.960040] usb 1-4: ath9k_htc: Firmware - ar9271.fw download failed
[ 1500.050101] ath9k_hif_usb: probe of 1-4:1.0 failed with error -22
[ 1500.050166] usbcore: registered new interface driver ath9k_hif_usb

```

I have downloaded my ar9271.fw firmware from here:

[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)

What I choose is the raw version of it. It is 51280 bytes in size. So, I guess the file is correct.

I also checked that the module is loaded after reboot.
```

lsmod | grep ath9k

ath9k_htc              44789  0
mac80211              273623  1 ath9k_htc
led_class               3764  1 ath9k_htc
ath9k_common            3119  1 ath9k_htc
ath9k_hw              293049  2 ath9k_htc,ath9k_common
ath                    16117  2 ath9k_htc,ath9k_hw
cfg80211              166783  3 ath9k_htc,mac80211,ath
compat_firmware_class     7504  1 ath9k_htc


```

My adapter is detected as follow:
```

lsusb

Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc.

```

I have no idea what the error message "download failed" means.

Are there brothers faced the same issue and solved it?

Nw01f

---

### Post by chili555 on 2010-11-07
Is the firmware in the right place with the right owner and permissions?```
 ls -al /lib/firmware/ar9271.fw
-rw-r--r-- 1 root root 51280 2010-08-16 15:02 /lib/firmware/ar9271.fw
```

---

### Post by Nw01f on 2010-11-07
Hi chili,

The firmware is located under /lib/firmware with proper permission:
```

ls -la /lib/firmware/ar9271.fw

-rw-r--r-- 1 root root 51280 2010-11-07 15:38 /lib/firmware/ar9271.fw

```

---

### Post by Nw01f on 2010-11-14
No one?:confused:

---

### Post by Ion Silverbolt on 2010-12-02
I had the same issue as you. The ar9271.fw downloads a 0 byte file for whatever reason. I got the firmware elsewhere and it works great.  [http://www.2shared.com/file/D3dVFI9N/ar9271.html](http://www.2shared.com/file/D3dVFI9N/ar9271.html)

---

