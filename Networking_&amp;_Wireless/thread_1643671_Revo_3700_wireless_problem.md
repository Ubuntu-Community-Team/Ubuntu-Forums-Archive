---
title: "Revo 3700 wireless problem"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by spwilkinson on 2010-12-12
Hi,


I've recently bought an Acer Revo 3700 and installed ubunutu.  It came with linpus which worked great with my wireless router, but as soon as I installed ubuntu I've had problems.  

After some research, I think this link shows the bug I've encountered. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662288?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662288?comments=all) 



Unfortunately, I've tried the workaround in post #9 but I still can't get wireless working.

 When I issue the following command - sudo lshw -C network - I get:
   *-network UNCLAIMED
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: d0:27:88:0e:7c:a4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:e800(size=256) memory:fbffb000-fbffbfff memory:fbffc000-fbffffff
 

I have tried uninstalling and reinstalling the kernel mentioned in post #9 as well as editing the  /etc/modprobe.d/blacklist.conf file.
 Here is the latest version of my blacklis.conf file


 # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
 # evbug is a debug tool that should be loaded explicitly
blacklist evbug
 # these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
 # replaced by e100
blacklist eepro100
 # replaced by tulip
blacklist de4x5
 # causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu [bug #2011]("https://bugs.launchpad.net/bugs/2011"), #6810)
blacklist snd_intel8x0m
 # Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
 # replaced by p54pci
blacklist prism54
 # replaced by b43 and ssb.
blacklist bcm43xx
 # most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
 # replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
 # low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
 # ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
 # EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
 blacklist rt2800pci
blacklist rt2860sta


 Any help is greatly appreciated as my machine is pretty much useless unless I can connect to the wireless router.


 Regards

---

### Post by chili555 on 2010-12-12
May we please see:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -i rt2
dmesg | grep -i rt3
```Thanks.

---

### Post by spwilkinson on 2010-12-12
Hi,  Unfortunately, none of those commands returned anything.  Have I missed something?  Or is that normal/to be expected?  Regards

---

### Post by chili555 on 2010-12-12
Sometimes, Dr. Chili learns as much from what is not said as from what is said. The *lsmod* entries tell me that there are no unneeded rt2800 or rt2x00 modules being loaded. That's good. However, it also says that the module that is the subject of the workaround you linked is also not being loaded. That's a bad thing.

Let's load it explicitly and see if we can bring your Ralink to life. Please do:```
sudo modprobe rt3090sta
sudo lshw -C network
```Is that horrible word UNCLAIMED gone? Did your wireless spring to life? If this does it, we'll need to take one more step to make it permanent. If not, post:```
dmesg | grep -i rt3
```Thanks.

---

### Post by spwilkinson on 2010-12-12
Hi,  Some very promising signs :-)  

When I typed in the first command I got: 

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper.old, it will be ignored in a future release.  

ndiswrapper.old is a file I renamed.  It was called simply ndiswrapper and I assumed it was to do with windows drivers for my wireless (something I stumbled upon when googling).  Should I rename it to what it was originally, leave it as is or delete it?  

The 'UNCLAIMED' message has now gone :    *-network                       description: Wireless interface        product: RT3090 Wireless 802.11n 1T/1R PCIe        vendor: RaLink        physical id: 0        bus info: pci@0000:02:00.0        logical name: ra0        version: 00        serial: 1c:65:9d:59:a5:a2        width: 32 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless        configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.7 latency=0 multicast=yes wireless=Ralink STA        resources: irq:18 memory:febf0000-febfffff   *-network        description: Ethernet interface        product: RTL8111/8168B PCI Express Gigabit Ethernet controller        vendor: Realtek Semiconductor Co., Ltd.        physical id: 0        bus info: pci@0000:03:00.0        logical name: eth0        version: 06        serial: d0:27:88:0e:7c:a4        size: 100MB/s        capacity: 1GB/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s        resources: irq:43 ioport:e800(size=256) memory:fbffb000-fbffbfff memory:fbffc000-fbffffff

 I am still unable to connect to my wireless router as I can't input a WPA key. Do I need another driver for this?  Thanks for your help, it is very much appreciated.

 Regards

---

### Post by chili555 on 2010-12-12
When you click the Network Manager icon after disconnecting the ethernet cable, do you see your network? Are you able to click it and try to connect?

With the ethernet cable detached, please run and post:```
dmesg | grep -i rt3
```Thanks.

---

### Post by spwilkinson on 2010-12-12
Hi,

I've rebooted my machine and re-issued the command you said - 

```
sudo modprobe rt3090sta
```and now I can connect to my wireless device! :-)

Now, just one last question.  How can I make it so that I don't have to manually enter the modprobe command each time I reboot?

Thanks for your help so far.

For completeness, the command you asked me to enter now shows
[  248.057194] ====> rt30xx Read PowerLevelMode =  0x3.
[  248.057199] ====> rt30xx F Write 0x83 Command = 0x3.
[  248.525543] ====> rt30xx Read PowerLevelMode =  0x3.
[  248.525554] ====> rt30xx F Write 0x83 Command = 0x3.
[  267.791992] ====> rt30xx Read PowerLevelMode =  0x3.
[  267.791997] ====> rt30xx F Write 0x83 Command = 0x3.


Regards

---

### Post by chili555 on 2010-12-12
> and now I can connect to my wireless device! Awesome! Good work.> How can I make it so that I don't have to manually enter the modprobe command each time I reboot?Let's instruct the computer to load the module on boot all the time, every time:```
sudo su
echo rt3090sta >> /etc/modules
exit
```If that fixes it, don't forget to drop down Thread Tools and mark the issue 'Solved.'

---

### Post by spwilkinson on 2010-12-12
Thank you very much chili555!  Wireless now seems to be working fine.

Thanks for all your help

Regards

---

### Post by elgs on 2011-02-22
sudo su
echo rt3090sta >> /etc/modules
reboot now

Worked like a charm!!! Thank you very much!!!

---

