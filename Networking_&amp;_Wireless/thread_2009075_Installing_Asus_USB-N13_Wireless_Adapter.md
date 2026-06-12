---
title: "Installing Asus USB-N13 Wireless Adapter"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by eman0531 on 2012-06-23
I've recently built a mini-HTPC and have installed xbmcbuntu (Ubuntu 11.10) as I will solely be using this machine as a HTPC to run XBMC.  

The issue that I'm having is that the machine does not have a CD/DVD drive installed, so I'm not able to use the supplied driver CD that came along with the Wireless Adapter (ASUS USB-N13).  I chose this wireless adapter specifically because it was called out as Linux 'friendly'. Unfortunately, my limited Linux experience is preventing me from getting the correct drivers installed and connecting to my network.

I've tried various solutions from these forums but so far have came up empty (this is one that I spent the most time with: 

[http://ubuntuforums.org/showthread.php?t=1444746&page=2]("http://ubuntuforums.org/showthread.php?t=1444746&page=2")

Here is a bit of info upfront: 

```
htpcbox@HTPCBOX:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 001 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 002 Device 003: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

```
htpcbox@HTPCBOX:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

htpcbox@HTPCBOX:~$ 
```


This is the last hurdle that I have to overcome to get my HTPC up and running so I would greatly appreciate any help that you crazy ubutu lovers could provide! :)

---

### Post by steeldriver on 2012-06-23
you need to be careful which thread(s) you follow for that device - iirc there are several different chipset/driver combinations all branded as "ASUS N13" - in your case your lspci gives an id of 0b05:17ab so I suggest you search specifically for that, e.g.

[http://ubuntuforums.org/showthread.php?t=1965558](http://ubuntuforums.org/showthread.php?t=1965558)

sorry I can't be more help - I have one with the Ralink RT2870 chip and fortunately that works  out of the box in Myth/Xubuntu 11.10 using the  default rt2800usb  driver - it may be that the driver is blacklisted as suggested in the above thread - or there may be other kernel specific issues

---

### Post by eman0531 on 2012-06-24
Thanks for the tips steeldriver, I didn't realize the chipset/driver combinations could be different for the Asus USB-N13.

Thankfully I was able to track down the needed info from a few posts.  I will copy the solution to this problem just in case any other xbmcbuntu users find themselves in the same situation.

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/32/20/2844083-rtl8192cu-3.3.23192_dkms.tar.gz
sudo tar xvf 2844083-rtl8192cu-3.3.23192_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8192cu -v 3.3.23192
sudo dkms build -m rtl8192cu -v 3.3.23192
sudo dkms install -m rtl8192cu -v 3.3.23192 
```

```
sudo gedit /etc/rc.local
```

Right above exit 0 add these two lines:

```
modprobe rtl8192cu
echo "0b05 17ab" > /sys/bus/usb/drivers/rtl8192cu/new_id
```

By following the above steps, I was able to get my ASUS USB-N13 (0b05:17ab) wireless adapter working on XBMCbuntu 11.10.  

A big thanks to SteelDriver, Chili555, and Flash63 for providing the necessary info at the following links:

[http://ubuntuforums.org/showthread.php?t=1965558&highlight=0b05%3A17ab]("http://ubuntuforums.org/showthread.php?t=1965558&highlight=0b05%3A17ab")

[http://ubuntuforums.org/showthread.php?t=1930616]("http://ubuntuforums.org/showthread.php?t=1930616")

---

