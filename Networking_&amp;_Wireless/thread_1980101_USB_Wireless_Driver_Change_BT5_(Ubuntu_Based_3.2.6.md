---
title: "USB Wireless Driver Change BT5 (Ubuntu Based 3.2.6)"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by Bionic711 on 2012-05-14
Since the Backtrack 5 forums won't let me post and BT5 is ubuntu 3.2.6 based, I figure I would try to get some help here with my issue.

I currently have a Realtek chipset that is capable of using the rtl8187 drivers as I've used them with it before in 11.10 release of Ubuntu. Upon switching to BT5R2, The default driver that is loading is the rtl8172u.

How do I force the use of the rtl8187 driver for the specific device?

Both drivers are already installed and ready to use on the system, the system just defaults to the 8172u. When I lsmod it's showing that no devices are using the rtl8172u driver, but the dmesg is showing that the rtl8172u driver is being used by the device.  Lastly, the real issue I'm having is the rtl8172u driver is loading the wireless card as an 'ethernet' encap type and I'm unable to pick up any wireless signals with it at all.  

I'm 99% certain loading the new driver will revert the encap type back to 80211 as the ifconfig wlan0 should be reading.

Thanks in advance.

---

### Post by chili555 on 2012-05-14
> I'm 99% certain loading the new driver will revert the encap type back to 80211 as the ifconfig wlan0 should be reading.
Seeing a wireless device as encap:Ethernet is perfectly normal. Here is my ifconfig; my wireless works perfectly:> wlan0     Link encap:Ethernet  HWaddr xx:19:d2:c2:1b:xx  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:587060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:604044037 (604.0 MB)  TX bytes:90952384 (90.9 MB)Usually, drivers attach based on their device id. Usually r8712u (is that what you're referring to?) and rtl8187 have completely differing usb.id aliases. I doubt you can substitute one for the other. You can certainly temporarily try:```
sudo modprobe -r r8712u
sudo modprobe rtl8187
```Is your wireless working now?

If you'd care to troubleshoot, please post:```
lsusb
```I love a mystery!

---

