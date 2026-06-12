---
title: "trouble installing azurewave aw-nu221 wireless usb adapter"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by ctimbrell on 2012-04-23
newbie and first post so any help very much appreciated.

i have a aw-nu221 wireless adapter that i am trying to set up. at the moment i am connected to the net via cable so still have functionality.

i believe the adapter requires the driver for the RT2870 chip? which i have download. I have found and configured the /os/linux/config.mk file as informed but when i try to run make, i just get errors:

cc1: some warnings being treated as errors

make[2]: *** [/home/ctimbrell/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/ctimbrell/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make: *** [LINUX] Error 2

Any ideas or direction would be most appreciated. 

ps i did have a wireless dongle connected and working which i no longer have, not sure if this is causing any trouble.

---

### Post by chili555 on 2012-04-23
> make[1]: *** [_module_/home/ctimbrell/Downloads/[COLOR="Red"]2010_0709[/COLOR]_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-[COLOR="Red"]3.0.0-17[/COLOR]-generic'This old driver is not going to compile against this newer kernel. As well, if your device is indeed an RT2870 chipset, it ought to work with the rt2800usb module already built in to your default install. Let's do some diagnostics. Please insert the device and then run and post:```
lsusb
sudo modprobe rt2800usb
dmesg | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by ctimbrell on 2012-04-23
lsusb returns

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
Bus 004 Device 003: ID 0603:00f2 Novatek Microelectronics Corp.

Basically my keyboard and mouse

modprobe returned

[12818.532184] usbcore: registered new interface driver rt2800usb

Thanks for the reply, hows it looking?

---

### Post by chili555 on 2012-04-23
> Basically my keyboard and mouseExactly. Where was your AzureWave all this time? Plugged in or not?

---

### Post by ctimbrell on 2012-04-23
plugged in. no light showing on it though?

---

### Post by chili555 on 2012-04-23
If it is plugged in to a USB port and doesn't show up in *lsusb*, something is defective, either in the device or the USB port. Let's dig deeper. With it plugged in, let's see:```
lspci -nn | grep 0280
sudo lshw -C network
```Thanks.

---

### Post by ctimbrell on 2012-04-23
The output for the above is:

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:11:09:18:2d:d3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.6 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:c800(size=256) memory:ed000000-ed0000ff memory:40000000-4000ffff

Hope this sheds some light on the subject, thanks

---

### Post by chili555 on 2012-04-23
That's simply your ethernet card. Here is my last attempt. Unplug the device and run:```
sudo tail -f /var/log/syslog
```Leave the terminal open and watch it as you plug the device in. Is there any recognition of the device? If so, post it. Try all the USB ports you can.

Get out of *tail* with Ctrl+c.

---

### Post by ctimbrell on 2012-04-23
is there anyway to clear the log. i got nothing when plugging in the usb at the rear, i unplugged the mouse and keyboard from the front and swapped them over but then got loads about mail etc

Apr 23 16:31:06 ctimbrell-PJ454AA-ABU-a608-uk nullmailer[13746]: smtp: Failed: Connect failed
Apr 23 16:31:06 ctimbrell-PJ454AA-ABU-a608-uk nullmailer[782]: Sending failed:  Host not found
Apr 23 16:31:06 ctimbrell-PJ454AA-ABU-a608-uk nullmailer[782]: Delivery complete, 37 message(s) remain.
Apr 23 16:31:10 ctimbrell-PJ454AA-ABU-a608-uk zmwatch[1447]: ERR [Shared data size conflict in shared_data for monitor Monitor-7, expected 328, got 316]

No idea at all what this means but only happened when i swapped the devices over i think

---

### Post by chili555 on 2012-04-23
I don't believe any of that has anything to do with a wireless USB adapter. Does the device work on other computers? Are you sure the USB port is working?

I'm not sure how we can install a driver and have the device work if it isn't recognized in any form by the computer.

---

### Post by ctimbrell on 2012-04-23
looks like you may be right. I will go to the shop and buy another adapter in case this one is faulty and post back either later this evening or tomorrow. not sure what time zone you're on.

Thanks for your help this far, hope you're still available once i get the new adapter

rgds
ctimbrell

---

### Post by chili555 on 2012-04-23
I am subscribed to the thread, so I'll see your reply via email. Good luck and I'll look forward to your post.

---

### Post by ctimbrell on 2012-04-23
Back with new adapter which i now seem to be making progress with. It has a light when plugged in and i am getting a response from commands issued but not working yet.

It is an azurewave aw-nu120.

lsusb now returns
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 003: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse
**Bus 001 Device 006: ID 13d3:3310 IMC Networks** 

which has got the last line showing a network reference which it didnt before

dmesg | grep rt2 now returns
[12818.532184] usbcore: registered new interface driver rt2800usb

 sudo lshw -C network now returns
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:11:09:18:2d:d3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:c800(size=256) memory:ed000000-ed0000ff memory:40000000-4000ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan1
       serial: 00:08:ca:c2:dd:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

Which clearly now has a wireless interface.

I just need to now get it functional but dont know where to go next with it. Help is once again very much appreciated. Thanks in advance

---

### Post by chili555 on 2012-04-23
We're getting somewhere now! The driver r8712u is definitely correct for your device:```
 modinfo r8712u | grep 3310
alias:          usb:v[COLOR="Red"]13D3[/COLOR]p[COLOR="Red"]3310[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```You have a wireless interface wlan1. Do you see networks when you click the Network Manager icon? Does it scan?```
iwconfig
sudo iwlist wlan1 scan
```

---

### Post by ctimbrell on 2012-04-23
solved

i disconnected the wired connection and made an attempt to reconnect from the wireless network manager which worked. it scanned as expected and connected as it should.

The (lshw -C network) command returned

*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan1
       serial: 00:08:ca:c2:dd:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.7 multicast=yes wireless=IEEE 802.11bg

Not sure what part of what i did earlier with the help of chilli555 made it work as clearly the wireless adapter was also faulty. Thanks to chilli555 for getting me to that point, the help was very much appreciated.

---

### Post by chili555 on 2012-04-23
> ip=192.168.0.7Awesome! Glad it's connected and you're solved. Have fun!

---

