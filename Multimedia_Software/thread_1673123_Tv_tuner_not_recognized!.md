---
title: "Tv tuner not recognized!"
date: 2011-01-21
forum: Multimedia Software
---

### Post by ac00 on 2011-01-21
Hi all,

I am running Ubuntu 10.10 32bit.

I have a "PixelView PlayTV USB Ultra " TV TUNER card, which runs thru USB interface. Now, When I plug it in my ubuntu machine it displays following in dmesg
"usb 2-1.2: new high speed USB device using ehci_hcd and address <xx>" 
[xx keeps changing, it seems its count of USB device attached and detached]

and no dvb-usb dmesg, that is, the card is not getting recognized.

I would like to add here that I have already tried v4l, but no luck.
To install v4l, I followed these steps,

after downloading branch,
make config
make all
make install 
make load

[The card has a Conexant Polaris chipset on it, as per my lsusb log].

Am I missing some thing???

I am using following version of kernel 
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

-- Thanks in advance,

---

### Post by xc3RnbFO8P on 2011-01-22
> [The card has a Conexant Polaris chipset on it, as per my lsusb log].
Show the output of:
> lsusb

---

### Post by aslam on 2011-02-17
I have a Enter usb tv stick (Model E-220U) which have a connexant polaris chipset as per information from windows 7 does not recognised by ubuntu 10.10 32 bit

my lsusb result 

Bus 002 Device 010: ID 1f4d:0237 G-Tek Electronics Group 
Bus 002 Device 008: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 007: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 006: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 003: ID 04e8:6721 Samsung Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6480 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


If run lsusb removing the device the first line is missing so it says G-Tek Electronic 
any help to get the driver

---

