---
title: "Asus usb-n13"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by rnadmoiezd on 2013-08-15
```
lee@lee-TZ77A:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]


```

It works it just won't stay connected and it's really slow. Every few  minutes it stops working and I have to unplug it and plug it back in
```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [Bucket] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:     

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    txjohnson:       Infra, 28:C6:8E:B4:EC:60, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    insight_wifi_6708: Infra, 00:22:75:63:FD:D8, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    insight_wifi_6120: Infra, 00:22:75:08:B5:D6, Freq 2452 MHz, Rate 54 Mb/s, Strength 99 WPA WPA2
    deluca:          Infra, 4C:60:DE:E0:7B:CD, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    *Bucket:         Infra, 2C:B0:5D:34:87:BE, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2

  IPv4 Settings:
    Address:        
    Prefix:          
    Gateway:        

    DNS:             


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by chili555 on 2013-08-15
Have you tried disabling N speeds in the router? Which Ubuntu version are you using?```
lsb_release -a
```Thanks.

---

### Post by rnadmoiezd on 2013-08-16
> **chili555 said:**
> Have you tried disabling N speeds in the router? Which Ubuntu version are you using?```
lsb_release -a
```Thanks.

```
lee@lee-TZ77A:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


```


x64
and bringing it down to 54mbps didn't work.

---

### Post by chili555 on 2013-08-16
Please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
```I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd Desktop/backports-3.11-rc3-1/
make defconfig-rtlwifi
make
sudo make install
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu
```Any improvement?

---

### Post by rnadmoiezd on 2013-08-17
Sorry for the delay in posts I've had to work on my car today. Ok, here's the low down. After setting it at 54mb/s it miraculously started working. However, the speeds are still a little on the slow side. Loading webpages seems sluggish for example. I tried your method and everything installed just fine, no errors that I could see. I set it back to 300 and that was like instant death. So what's next?

---

### Post by praseodym on 2013-08-17
Did you try Chilis installation? If not, there is also a pre-compiled package with a patched driver available. Installation instructions here with dkms:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

It will build the driver automatically after a kernel upgrade.

---

