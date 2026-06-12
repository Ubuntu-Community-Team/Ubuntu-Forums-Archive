---
title: "Asus N13 B1 install with no internet access"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by tenright11b on 2013-06-22
*I'm going nuts trying to install an asus n13 b1 wifi adapter on a desktop with no internet access.  This is on a new mITX build with everything else working just fine.  I do have an old laptop with net access so I can post messages.  All instructions I read require net access before compiling the driver source.  I've spent a good six hours updating my laptop to Ubuntu 13.04* to be the same as the desktop.  I thought I could get the deb packages accross that way; no luck.  Ubuntu software center sees the package in "/var/cache/apt/archives/" but blows up on the dependancies.  Using "apt-get install xxxxxxx" isn't working either.  Does anyone have some ideas?  This is turning into a "major catch-22."

---

### Post by praseodym on 2013-06-22
Please show the output of:
```

lsusb
```

---

### Post by tenright11b on 2013-06-22
Here is the output from lsusb, lshw -c network and nm-tool.  The symptoms on the desktop are the usb adapter keeps trying to connect with no success.  The "low-rent" laptop connect easily at 54 Mb/s.  I am at a retirement facility with wifi hotspot provided as only internet access.  This system is not my first build, but it is the first one trying to use wifi.  Prior builds have used dsl.  I started out on an S100 system with RS-232 serial terminal and 8" floppies more years ago than I really care to admit.

tenright@me:~$ lsusb

Bus 001 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 004 Device 003: ID 046d:c064 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

tenright@me:~$ sudo lshw -c network
[sudo] password for tenright: 
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 08:60:6e:cf:2f:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu
           driverversion=3.8.0-19-generic firmware=N/A
           link=no multicast=yes wireless=IEEE 802.11bgn

tenright@me:~$ nm-tool
NetworkManager Tool
State: disconnected
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        08:60:6E:CF:2F:E3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    EnGenius1: Infra, 00:02:6F:8E:38:B9, Freq 2417 MHz, 
                   Rate 54 Mb/s, Strength 97

---

### Post by praseodym on 2013-06-23
The driver needs a patch for 13.04. But there is a pre-compiled package available:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

---

### Post by tenright11b on 2013-06-23
Up and running, your link worked like a charm; thanks much.

BTW, how do I mark the thread as solved?  The "thread tools" only offer "Show Printable version, Email Page and suscribe to thread.
I'm probably missing something obvious.

---

### Post by praseodym on 2013-06-23
Imho its editing the 1st posting.

Glad it worked ;)

---

### Post by almark on 2013-08-02
Hey thanks a lot for sharing this fix, my n13 wifi stick worked but just kept on disconnecting and now it's working FINE :)

Much regards
Mark

---

### Post by dccmgb on 2013-08-10
I have the same problem with my Asus N13 B1.  I now have a fresh copy of 13.04 ready to go.  Do I then run the following commands;

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms

wget [https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1](https://realtek-8188cus-wireless-drivers-3444749-ubuntu-1304.googlecode.com/files/rtl8192cu-tjp-dkms_1)
sudo dpkg -i rtl8192cu-tjp-dkms_1.6_all.deb
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf

Also, can you let me know what these commands actually do?  Thanks.  dc

---

### Post by praseodym on 2013-08-11
"sudo apt-get ..." installs the files needed for compiling driver automatically.

"wget" downloads the .deb-file of the driver

"sudo dpkg -i" installs the .deb file

"echo 'blacklist' " blacklists the native module rtl8192cu. The new module is named 8192cu

---

### Post by dccmgb on 2013-08-11
Thanks for the clarifications.  One question, since I am relatively new to Ubuntu, was this driver modification performed by Realtek or by someone at/on the Ubuntu Forum?  I'm trying to get an idea of how Ubuntu support is conducted/initiated with third party providers.

---

### Post by praseodym on 2013-08-11
More infos can be found here:

[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

I dont know who the guy is...

---

