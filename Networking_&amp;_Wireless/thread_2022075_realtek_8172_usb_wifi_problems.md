---
title: "realtek 8172 usb wifi problems"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by crosmuller on 2012-07-10
Hi,

I am trying to get a realtek 8172 usb wifi device working on ubuntu 10.04, but no luck.


lsusb output:
```
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp.
```

I first tried to install the device with the realtek linux driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=2&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

But when I execute ./install.sh I get a compilation error

```
 error: ‘struct wiphy’ has no member named ‘max_num_pmkids’
make[2]: *** [/home/freddy/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/home/freddy/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-41-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
```


I found a lot of information on installing this driver for example here: 

[http://samiux.blogspot.nl/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.nl/2010/05/howto-realtek-8192su-usb-dongle.html)

but it is all about an older version of the driver that's not online anymore. I used RTL819xSU_usb_linux_v2.6.6.0.20120405.zip and the documentation is about rtl8192SU_usb_linux_v2.6.0006.20100226.zip

I tried using ndiswrapper

```
sudo ndiswrapper -i RTL8188_8191_8192_SU_WindowsDriver_1086.48.0809.2011.F0049_12.P0406_UI_1.00.0187.L/88_91_92_SU_Driver/WinXP/net8192su.inf
```

the driver is installed:

```
sudo ndiswrapper -l
net8192su : driver installed
	device (0BDA:8172) present (alternate driver: r8192s_usb)
```

the network device is found by gnome network manager but unfortunately I cannot authenticate so still no wifi. I tried the key 10 times so I'm pretty sure it is not a typo.

Can someone help me with this?

---

### Post by chili555 on 2012-07-10
> sudo ndiswrapper -l
net8192su : driver installed
	device (0BDA:8172) present (alternate driver: r8192s_usb)I think this suggests that both ndiswrapper and a native driver r8192s_usb are loaded. Is that so?```
lsmod | grep -e ndis -e r819
```If so, unload first one and then the other:```
sudo modprobe -r ndiswrapper
```And second:```
sudo modprobe -r r8192s_usb
sudo modprobe ndiswrapper
```Can you connect with one or the other? If so, we'll blacklist the driver that's *not* working.

---

### Post by crosmuller on 2012-07-11
Thank you!!!!!!!!!! You are the best. The ndiswrapper works. What did I do wrong? Did the other module get installed while I was trying to compile the native module?

---

### Post by chili555 on 2012-07-11
> **crosmuller said:**
> Thank you!!!!!!!!!! You are the best. The ndiswrapper works. What did I do wrong? Did the other module get installed while I was trying to compile the native module?The driver r8192s_usb is installed by default. It was there all along and probably would work fine, perhaps with a bit of tweaking. However, if ndiswrapper is working well for you, you may as well stick with it.

Did you get the blacklist in place successfully? Does everything work perfectly on reboot?

---

### Post by crosmuller on 2012-07-11
> **chili555 said:**
> The driver r8192s_usb is installed by default. It was there all along and probably would work fine, perhaps with a bit of tweaking. However, if ndiswrapper is working well for you, you may as well stick with it.

hmm...... I did not know that.. however I'm pretty sure the wireless network was not working

> **chili555 said:**
> 
Did you get the blacklist in place successfully? Does everything work perfectly on reboot?

Yes, I added the native module to the blacklist and ndiswrapper to /etc/modules

---

### Post by crosmuller on 2012-07-11
The bad news... the connection does not seem to be stable

---

### Post by chili555 on 2012-07-11
Any clues in:```
dmesg | grep -e wlan -e ndis
```

---

### Post by crosmuller on 2012-07-11
not really :)

```
[   12.798778] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.427931] ndiswrapper: driver net8192su (Realtek Semiconductor Corp.,08/09/2011,1084.53.0809.2011) loaded
[   15.345037] wlan0: ethernet device 00:0c:f6:93:73:fc using NDIS driver: net8192su, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192S Wireless LAN USB NIC                                     ', 0BDA:8172.F.conf
[   15.345103] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   15.346795] usbcore: registered new interface driver ndiswrapper
[   15.391192] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.430658] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   44.829765] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   55.428031] wlan0: no IPv6 routers present
[  193.049969] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  221.043059] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  221.359129] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  231.732037] wlan0: no IPv6 routers present
[  274.929255] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  305.083350] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  305.586244] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  316.400036] wlan0: no IPv6 routers present
[ 2568.926328] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2633.059411] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 2633.363153] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2644.040026] wlan0: no IPv6 routers present
[ 2693.924893] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3290.256540] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 3290.579394] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3300.848022] wlan0: no IPv6 routers present
[ 3513.934988] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3542.192566] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 3542.458881] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3553.368035] wlan0: no IPv6 routers present
[ 3613.930465] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3642.220746] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 3642.505234] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3652.772036] wlan0: no IPv6 routers present
[ 3713.930590] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3762.182518] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 3762.478988] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3772.620029] wlan0: no IPv6 routers present
```

---

### Post by chili555 on 2012-07-11
No clues? No clues you say? The *answer* is in there!!!> ndiswrapper (iw_set_auth:1602): invalid cmd 12This is an error common to the older version of ndiswrapper which makes sense because you're running an older version of Ubuntu:> I am trying to get a realtek 8172 usb wifi device working on [COLOR="Red"]ubuntu 10.04[/COLOR], but no luck.You could:
  # Upgrade to 12.04 where your troubles are over because the native driver will probably work fine. You could test with a live CD. Or;

  # Compile a newer version of ndiswrapper that fixes the error I quoted. A complex process but do-able by mortal man. Or;

  # Remove ndiswrapper and try to get the native driver going.

Which do you prefer? I will be happy to help in any case.

---

### Post by crosmuller on 2012-07-15
> **chili555 said:**
> No clues? No clues you say? The *answer* is in there!!!This is an error common to the older version of ndiswrapper which makes sense because you're running an older version of Ubuntu:You could:
  # Upgrade to 12.04 where your troubles are over because the native driver will probably work fine. You could test with a live CD. Or;

  # Compile a newer version of ndiswrapper that fixes the error I quoted. A complex process but do-able by mortal man. Or;

  # Remove ndiswrapper and try to get the native driver going.

Which do you prefer? I will be happy to help in any case.

Thanks, I used 10.04 because I didn't like the 12.04 interface for the user of this computer (he is a windows user that wants to switch) but ofcourse I can install 12.04 and change the interface so that's what I did. Problem solved!

---

