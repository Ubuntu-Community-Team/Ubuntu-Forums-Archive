---
title: "UNR Jaunty, AspireOne ath5k is disconnected."
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by Weevil on 2009-05-01
Hi,

I have installed Jaunty UNR on my AspireOne 110-Aw and everything was fine. But today I couldn't make a wireless connection (or find one), I don't know why.

So after some searching on the internet I installed linux-backports-modules-jaunty, blacklisted ath_pci, ath_hal and acer_wmi in /etc/modprobes.d/blacklist.conf, added ath5k to /etc/modules, checked if ath5k was blacklisted anywhere in /etc/modules.d/, ran 'modprobe -r ath5k acer_wmi ath_pci ath_hal' and then 'modprobe ath5k' (and a reboot).

This in order to get the (much advised) ath5k wifi drivers/module.


They seem to be loaded, according to nm-tool, and the wifi LED does burn at least on start-up but ath5k is disconnected. I'm not sure what to do next, couldn't find anything on teh internetz sofar.

Included some terminal outputs which I hope are useful :)



nm-tool output:
```
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:22:68:B7:E3:3A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



```




dmesg | grep ath
```
[    3.024795] device-mapper: multipath: version 1.0.5 loaded
[    3.024801] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.940405] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.940432] ath5k 0000:03:00.0: setting latency timer to 64
[    6.940540] ath5k 0000:03:00.0: registered as 'phy0'
[    7.160581] Registered led device: ath5k-phy0::rx
[    7.160723] Registered led device: ath5k-phy0::tx
[    7.160733] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   22.004088] ath5k phy0: gain calibration timeout (2412MHz)
[   22.348308] ath5k phy0: noise floor calibration timeout (2412MHz)
[   22.806576] ath5k phy0: gain calibration timeout (2417MHz)
[   23.152299] ath5k phy0: noise floor calibration timeout (2417MHz)
[   23.600480] ath5k phy0: gain calibration timeout (2422MHz)
[   23.942626] ath5k phy0: noise floor calibration timeout (2422MHz)
[   24.365638] ath5k phy0: gain calibration timeout (2427MHz)
[   24.711876] ath5k phy0: noise floor calibration timeout (2427MHz)
[   25.122727] ath5k phy0: gain calibration timeout (2432MHz)
[   25.464941] ath5k phy0: noise floor calibration timeout (2432MHz)
[   27.384285] ath5k phy0: gain calibration timeout (2447MHz)
(timeouts continue hereafter)

```

---

### Post by Weevil on 2009-05-03
For the interested... turning power off for a while did seem to work in my case.

---

### Post by beefcurry on 2009-06-03
yeah I have the same symptoms, tried dmesg and got the same result as you, I am using the Acer Aspire One ZG5. The ath5k drivers are really choppy, sometimes it works, sometimes it dosn't this is quite annoying since the main purpose of a netbook is to go on the net!

PS the buy report is here if anyone needs it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269253](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269253)

---

### Post by Sera88 on 2009-06-08
I had the exact same probelm with Acer AspireOne A110. Removed UNR shortly after discovering the bug.

EDIT: Oh, just found a workaround for it:
[https://bugs.launchpad.net/ubuntu/+bug/350352](https://bugs.launchpad.net/ubuntu/+bug/350352)

---

### Post by E_lexy on 2010-10-28
I have the same issue on a Toshiba Satelite A215. But it got worse after I switch from the 'stock' 5400rp disk to a larger 7200rpm.m
Now the area of the disk seems to be getting warmer, and the WiFi is worse!

---

