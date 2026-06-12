---
title: "Problems with ad-hoc networking between Jaunty 9.04 and Vista using Linksys adapter"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by Sethleben on 2009-09-23
I have a Linksys WUSB54GR wireless-G USB network adapter that works fine picking up wireless networks when connected to my desktop running Jaunty 9.04. However, I wish to set up an ad-hoc network with a laptop running Windows Vista/Windows 7 so that the laptop can access files from the desktop.

Firstly I tried going to Network Connections in Ubuntu and adding a new wireless network, with Mode set to Ad-Hoc, DHCP enabled, and no encryption to begin with. I then left-clicked on the network icon and selected "Connect to hidden wireless network", and attempted to connect to the network I had just created. The network icon then changed to indicate connection in progress. 

At this point I used the Windows laptop to scan for wireless networks, but did not pick up the ad-hoc network. I chose to "Manually connect to a wireless network" in Windows, and then entered the details of the network, but it still did not appear.

Using manual IP settings instead of DHCP, as suggested [here]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html") didn't make any difference. 

If I create an ad-hoc network using another Windows PC/phone, Vista can see it and connect fine, so it seems that the problem lies in whether Ubuntu is actually putting the card into ad-hoc mode. If I try and do it manually, I obtain the following error:

```
$ sudo ifconfig wlan0 down
$ sudo iwconfig wlan0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
```

Could this mean that the driver doesn't support ad-hoc mode? This seems to have been the cause of a [similar problem]("http://ubuntuforums.org/showthread.php?t=812569") with a different card. Moreover, exactly the same thing happens (including the failure to manually set ad-hoc mode) using a different wireless USB adapter, an Edimax EW-7318Ug, which I believe uses the rt73usb driver. 

I haven't tried ndiswrapper yet on either of these, but would appreciate any thoughts before I start messing around with the drivers...


Many thanks in advance.

---

### Post by prabhat123 on 2010-02-16
I'm seeing a similar problem with a Netgear WG111 v3 device. I was able to get wireless working, but not Ad-Hoc mode. I'm still trying ...

---

