---
title: "Another wifi problem - D-Link DWA-130"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by SterlingM on 2011-01-15
I am having troubles getting my wifi to work on my laptop with ubuntu 10.10 installed. I am trying to use a D-Link DWA-130 USB wireless card. Right now my wireless light is blinking on and off rapidly. My iwconfig is - 
```

lo        no wireless extensions

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```I have tried doing what [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) says to do, but I can't seem to get it to work. I have also looked at many other sites google directed me too.

When I click on Windows Wireless Drivers, I get one driver present. The driver is netmw245, but it says Hardware present: No. 

My lsmod | grep ndiswrapper results are -
```

ndiswrapper           184207  0 

```ndisgtk and ndiswrapper-common are both installed. I would have ndiswrapper-utils too, but it tells me ndiswrapper-common replaces it - 
```

sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common


```When I do ndiswrapper -l, I get -
```

netmw245 : driver installed

```I have also done the [FONT=monospace]commands - 
[/FONT] sudo depmod -a[FONT=monospace]
[/FONT]sudo modprobe ndiswrapper

I have restarted after these steps as well. I'm not sure what else to do so I thought I would ask the forums. According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink) the D-Link DWA-130 should work after getting ndiswrapper. I can see the Bluetooth icon in the top right, but when I go to Network Connections I don't see any wireless networks. If anyone can help me get this working I would be very grateful. I have been trying to put up with no wifi, but I can't do it any longer. I really need this to work. Thanks.

---

### Post by SterlingM on 2011-01-15
bump before driving for a few hours

---

### Post by SterlingM on 2011-01-15
.

---

### Post by SeePU on 2011-01-15
What does the command 'lsusb' give you?

What is the revision letter?  The D-Link DWA-130 has a few revisions so it will be some letter and number.  Most likely, though, it's a realtek chipset, most likely the  and uses the RTL8192SU chipset so r8192s_usb driver (I think this is getting changed to a r8712u driver.

Search the forum for those terms as there's a few posts already regarding these chipsets and drivers.  

Also, check here for further info:
[http://wireless.kernel.org/en/users/Drivers/rtl819x](http://wireless.kernel.org/en/users/Drivers/rtl819x)

---

### Post by SterlingM on 2011-01-15
lsusb gives me - 

Bus 002 Device 004: ID 07d1:3c13 D-Link System DWA-130 802.11n Wireless N Adapter(rev.B) [Ralink RT2870]
Bus 002 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0461:4db6 Primax Electronics, Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by bkratz on 2011-01-15
You have a different model than I do, see this thread

[http://art.ubuntuforums.org/showthread.php?p=10281528](http://art.ubuntuforums.org/showthread.php?p=10281528)

---

### Post by SterlingM on 2011-01-15
The problem with this set of instructions is that I have no /os directory. I tried making it myself and continuing, but I don't get a ra0 connection from iwconfig when I am finished.

---

### Post by Talon2 on 2011-01-15
> **SterlingM said:**
> lsusb gives me - 

Bus 002 Device 004: ID 07d1:3c13 D-Link System DWA-130 802.11n Wireless N Adapter(rev.B) [Ralink RT2870]


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

---

### Post by SterlingM on 2011-01-16
Okay I solved it. The /os is in the files I downloaded, I thought it was supposed to be in my / directory. Thank you guys for all of the feedback and help!

---

