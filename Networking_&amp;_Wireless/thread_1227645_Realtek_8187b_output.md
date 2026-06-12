---
title: "Realtek 8187b output"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Lila_IT_CMU on 2009-07-30
here's the result



albert@ubuntu:~$ lspci -nn 
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 671MX [1039:0671] 
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003] 
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] [1039:0968] (rev 01) 
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) 
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f) 
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002] 
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02) 
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] SATA Controller / IDE mode [1039:1183] (rev 03) 
00:06.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] PCI-to-PCI bridge [1039:000a] 
00:09.0 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0730] 
00:09.1 SD Host controller [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller [1524:0750] 
00:09.3 FLASH memory [0501]: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller [1524:0751] 
00:0f.0 Audio device [0403]: Silicon Integrated Systems [SiS] Azalia Audio Controller [1039:7502] 
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10) 
albert@ubuntu:~$ lsusb 
Bus 001 Device 005: ID 14cd:6700 Super Top  
Bus 001 Device 004: ID 5986:0200 Acer, Inc  
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 15d9:0a4c   
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
albert@ubuntu:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: 191 Gigabit Ethernet Adapter 
       vendor: Silicon Integrated Systems [SiS] 
       physical id: 4 
       bus info: pci@0000:00:04.0 
       logical name: eth0 
       version: 02 
       serial: 00:90:f5:8a:09:3c 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sis190 driverversion=1.2 latency=0 module=sis190 multicast=yes 
  *-network:0 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:15:af:d5:df:1c 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.53+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 3 
       logical name: pan0 
       serial: 32:35:dc:fa:40:d5 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
albert@ubuntu:~$ lsmod | grep ndis 
ndiswrapper           193436  0  
albert@ubuntu:~$ dmesg | grep -e ndis -e wlan 
[   10.070803] ndiswrapper version 1.53 loaded (smp=yes, preempt=no) 
[   11.178233] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,12/26/2007,5.1116.1226.2007) loaded 
[   14.700878] wlan0: ethernet device 00:15:af:d5:df:1c using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8189.F.conf 
[   14.700910] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[   14.700963] usbcore: registered new interface driver ndiswrapper 
[   40.153023] wlan0: no IPv6 routers present 
albert@ubuntu:~$ sudo iwlist scan 
[sudo] password for albert:  
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     No scan results 
 
pan0      Interface doesn't support scanning. 
 
albert@ubuntu:~$  
what do you think is the problem?

---

### Post by pytheas22 on 2009-07-30
I'm not sure what's wrong, because according to everything above there are no problems, but it looks like the device is unable to see wireless networks.  My first guess would be that your network is operating in a different mode from your wireless card, which is on 802.11g mode.  If your wireless network is on 802.11n mode, for example, your card wouldn't wouldn't be able to detect it.  That said, this seems unlikely to be the problem because most networks these days are on 802.11g mode.

There is a native Linux driver for your card, so you shouldn't have to use ndiswrapper and Windows drivers to make this work.  The native driver is included by default in Ubuntu 8.10 and up, meaning your card should "just work" if you're using 8.10 or 9.04.  Which version of Ubuntu are you using?

If you have Ubuntu 8.10 or 9.04, please try running these commands to see if they make the wireless work:
```

sudo rmmod ndiswrapper
sudo modprobe rtl8187
sudo ifconfig wlan0 up
lshw -C Network
dmseg | grep -e rtl -e wlan
sudo iwlist scan
```

Please post all output so I can see what's going on.

If you have 8.04 or earlier, there are instructions here for installing a driver for your card [here]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b").  But don't try these on a later version of Ubuntu; they won't work.

---

### Post by Lila_IT_CMU on 2009-07-31
I am currently using Ubuntu 9.04...
Yes, there is a native Linux driver. It can detect a network even without ndiswrapper and it can also connect to that network but when Im going to download new Updates or applications, the transfer rate is always zero(I look in the network tools). 
what do you think is the problem sir?

---

### Post by martinbaselier on 2009-07-31
My

The realtek driver has only been recently added to the kernel. The module in the current kernel doesn't really work well. (I couldn't even get my usb dongle to work). You can download and install a newer kernel:

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-4-generic](http://packages.ubuntu.com/karmic/linux-image-2.6.31-4-generic)

Even with the new driver I still had to change the speed for it to work.

**sudo iwconfig wlan0 rate 11M**

---

### Post by pytheas22 on 2009-07-31
> Yes, there is a native Linux driver. It can detect a network even without ndiswrapper and it can also connect to that network but when Im going to download new Updates or applications, the transfer rate is always zero(I look in the network tools).
what do you think is the problem sir?

That's strange.  Are you at least able to browse web pages using the native driver?

I suspect that updating to a more recent version of the driver would help.  One way to do that is to install a newer kernel, as martinbaselier recommends above.  Another (possibly less complicated) way is to recompile just the Linux wireless stack (instead of installing a whole new kernel) using the latest code.  To do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file compat-wireless-2.6.tar.bz2 to your desktop.  Then run:

```
cd ~/Desktop
sudo apt-get update
sudo apt-get install build-essential
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot for changes to take effect, and see if the native driver works better (Be sure to verify that the native driver, not ndiswrapper, is really controlling the card by checking the output of 'lshw -C Network'.  The native driver should take precedence over ndiswrapper automatically, but if it doesn't, you will need to 'rmmod ndiswrapper' manually.)

---

### Post by martinbaselier on 2009-07-31
@pytheas22

I tried your suggestion and it caused a kernel panic with me (I have an ipw200 onboard; and just happen to have a usb rtl8187B for testing). I had to reboot with an older kernel, blacklist the ipw2200, reboot with the current kernel and do a **sudo make uninstall** in the directory where I had the source files to make everything work again.

---

### Post by pytheas22 on 2009-07-31
> I tried your suggestion and it caused a kernel panic with me (I have an ipw200 onboard; and just happen to have a usb rtl8187B for testing). I had to reboot with an older kernel, blacklist the ipw2200, reboot with the current kernel and do a sudo make uninstall in the directory where I had the source files to make everything work again.

I'm sorry it caused that problem.  The compat-wireless code is not always as stable as it should be, but it is considerably more up-to-date than the versions of wireless drivers that ship with Ubuntu by default.

In any case, if blacklisting the ipw2200 module was the solution to the kernel panic, then this issue shouldn't affect Lila_IT_CMU unless he or she also happens to have an Intel wireless card, which seems unlikely.  So I still think that recompiling compat-wireless is worth it as the most likely and easiest solution to the Realtek issue.

---

### Post by Lila_IT_CMU on 2009-08-01
> **pytheas22 said:**
> That's strange.  Are you at least able to browse web pages using the native driver?

I suspect that updating to a more recent version of the driver would help.  One way to do that is to install a newer kernel, as martinbaselier recommends above.  Another (possibly less complicated) way is to recompile just the Linux wireless stack (instead of installing a whole new kernel) using the latest code.  To do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file compat-wireless-2.6.tar.bz2 to your desktop.  Then run:

```
cd ~/Desktop
sudo apt-get update
sudo apt-get install build-essential
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot for changes to take effect, and see if the native driver works better (Be sure to verify that the native driver, not ndiswrapper, is really controlling the card by checking the output of 'lshw -C Network'.  The native driver should take precedence over ndiswrapper automatically, but if it doesn't, you will need to 'rmmod ndiswrapper' manually.)



I can't browse the internet, but it says(in the network applet) "Connection Established"

---

### Post by Lila_IT_CMU on 2009-08-01
> **pytheas22 said:**
> I'm not sure what's wrong, because according to everything above there are no problems, but it looks like the device is unable to see wireless networks.  My first guess would be that your network is operating in a different mode from your wireless card, which is on 802.11g mode.  If your wireless network is on 802.11n mode, for example, your card wouldn't wouldn't be able to detect it.  That said, this seems unlikely to be the problem because most networks these days are on 802.11g mode.

There is a native Linux driver for your card, so you shouldn't have to use ndiswrapper and Windows drivers to make this work.  The native driver is included by default in Ubuntu 8.10 and up, meaning your card should "just work" if you're using 8.10 or 9.04.  Which version of Ubuntu are you using?

If you have Ubuntu 8.10 or 9.04, please try running these commands to see if they make the wireless work:
```

sudo rmmod ndiswrapper
sudo modprobe rtl8187
sudo ifconfig wlan0 up
lshw -C Network
dmseg | grep -e rtl -e wlan
sudo iwlist scan
```

Please post all output so I can see what's going on.

If you have 8.04 or earlier, there are instructions here for installing a driver for your card [here]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b").  But don't try these on a later version of Ubuntu; they won't work.

You said here that there is no problem, So i will both try the ndiswrapper method and the native linux driver again...I will just post the output


Thanks a lot!

---

### Post by Lila_IT_CMU on 2009-08-02
Hello, I cant connect to the network. but when I use the live cd, it can connect at ease but I can't use the internet( I mean there is no download rate or speed.) and it can't also open any website. please help

---

### Post by pytheas22 on 2009-08-02
Please boot to the live CD and connect, then post the output of these commands (while running the live CD):
```

ifconfig
iwconfig
lshw -C Network
dmesg | grep -e wlan -e rtl
ping -c 5 google.com
ping -c 5 74.125.45.100
```

---

### Post by julioipn on 2009-08-02
Hi, a few months ago I had the same problem in Ubuntu 8.10, at first everything was fine, I could even download updates, but after 10 or 15 minutes nothing, network manager stated "conection established" but I couldn't browse any web pages nor download updates. I couldn't even ping to the router, the message was something like "destination host unreachable", however, network manager app still stated "conection established".

I tried several methods, what worked the best was the original driver, more details here:

[http://ubuntuforums.org/showthread.php?p=7722355#post7722355](http://ubuntuforums.org/showthread.php?p=7722355#post7722355)

PS:

It works the same in ubuntu 9.04

---

### Post by pytheas22 on 2009-08-02
julioipn: do you have a copy of the driver file from Realtek that you used?  If so, I'll put in on my web server so others can access (without having to email Realtek) if you email it to me (send me a private message for email address).

---

### Post by Lila_IT_CMU on 2009-08-02
> **julioipn said:**
> Hi, a few months ago I had the same problem in Ubuntu 8.10, at first everything was fine, I could even download updates, but after 10 or 15 minutes nothing, network manager stated "conection established" but I couldn't browse any web pages nor download updates. I couldn't even ping to the router, the message was something like "destination host unreachable", however, network manager app still stated "conection established".

I tried several methods, what worked the best was the original driver, more details here:

[http://ubuntuforums.org/showthread.php?p=7722355#post7722355](http://ubuntuforums.org/showthread.php?p=7722355#post7722355)

PS:

It works the same in ubuntu 9.04




Ok I will try, I just post the output


thanks

---

### Post by julioipn on 2009-08-02
> **pytheas22 said:**
> julioipn: do you have a copy of the driver file from Realtek that you used?  If so, I'll put in on my web server so others can access (without having to email Realtek) if you email it to me (send me a private message for email address).


of course, I'll email it to you, just send me your email adress in a private message, anyway, I think It will always be better to ask companies for the driver, this way they will realise there are many linux users, I mean,for instance, as I have mentioned, the driver is not available in the web page, you have to ask for It, that's because they don´t think it neccesary to make it publicly available, also, if you update your O.S. very often at some point this driver won't work anymore, old drivers from realtek does not work with latest kernels, each time you ask for a driver you get an updated version. For ubuntu 9.04 which comes with linux 2.6.28 I had to ask for the driver again.

---

### Post by Lila_IT_CMU on 2009-08-03
> **julioipn said:**
> of course, I'll email it to you, just send me your email adress in a private message, anyway, I think It will always be better to ask companies for the driver, this way they will realise there are many linux users, I mean,for instance, as I have mentioned, the driver is not available in the web page, you have to ask for It, that's because they don´t think it neccesary to make it publicly available, also, if you update your O.S. very often at some point this driver won't work anymore, old drivers from realtek does not work with latest kernels, each time you ask for a driver you get an updated version. For ubuntu 9.04 which comes with linux 2.6.28 I had to ask for the driver again.


hey, please email me the link

---

### Post by pytheas22 on 2009-08-03
I uploaded the file to [http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz](http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz).  julioipn makes a very good point about emailing Realtek to remind them that they should support Linux, and to make sure you're getting the most up-to-date driver code, but in the meantime, or if you don't have time to wait for a reply from Realtek, you can use that link.

---

### Post by Lila_IT_CMU on 2009-08-03
> **pytheas22 said:**
> I uploaded the file to [http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz](http://burnthesorbonne.com/files/rtl8187B_linux_26.1052.0225.2009.release.tar.gz).  julioipn makes a very good point about emailing Realtek to remind them that they should support Linux, and to make sure you're getting the most up-to-date driver code, but in the meantime, or if you don't have time to wait for a reply from Realtek, you can use that link.

Thanks a lot...

---

### Post by thomasaaron on 2009-08-05
Hey, guys.

This fix worked great in Jaunty's *-13 kernel. It broke with the update to the *-14 kernel.

I tried recompiling it with...

make
sudo make install
sudo reboot -h now

...and everything seemed to go well. However, it doesn't seem that the new driver works at all in the *-14 kernel. 

Any ideas?

---

### Post by julioipn on 2009-08-05
> **thomasaaron said:**
> Hey, guys.

This fix worked great in Jaunty's *-13 kernel. It broke with the update to the *-14 kernel.

I tried recompiling it with...

make
sudo make install
sudo reboot -h now

...and everything seemed to go well. However, it doesn't seem that the new driver works at all in the *-14 kernel. 

Any ideas?


I'm not sure I understood you thomasaaron, I just update to 2.6.28-14 kernel and the driver I sent to phyteas22 (rtl8187B_linux_26.1052.0225.2009.release) still works, I suppose you get the driver from his server, or if you asked for it to realtek you should have an more up-to-date driver, anyway, according to your message I suppose you installed the driver when you had *-13 kernel, did you install It again once you updated the kernel?? you have to install it again every time you update. Right after executing those instructions you mention:

make
sudo make install
sudo reboot

I check in "System->Administration->Hardware Drivers" that the driver is listed( Linux driver for Realtek RTL8187 WiFi cards) and the message should be "This driver is activated and currently in use"

---

### Post by pytheas22 on 2009-08-05
> Hey, guys.

This fix worked great in Jaunty's *-13 kernel. It broke with the update to the *-14 kernel.

I tried recompiling it with...

make
sudo make install
sudo reboot -h now

...and everything seemed to go well. However, it doesn't seem that the new driver works at all in the *-14 kernel.

Any ideas?

Yes, as julioipn points out, you have to recompile the driver against the newest kernel whenever you upgrade kernels (and you have to be booted into the newest kernel when compiling in order to compile against that kernel).  Maybe this is the problem.

If not, seeing the output of these commands would help to figure out what could be wrong:
```

lsmod | grep rtl
lshw -C Network
dmesg | grep -e rtl -e wlan
```

---

