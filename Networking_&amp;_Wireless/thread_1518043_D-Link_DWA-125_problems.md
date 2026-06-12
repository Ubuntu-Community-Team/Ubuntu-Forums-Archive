---
title: "D-Link DWA-125 problems"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by kakonsan on 2010-06-25
So, I know this problem has occured often, and many times has been fixed. I am a complete newbie to linux, and the only bash that I've run is for this problem, following others. But, due to my incompetence, I havn't been able to completely settle the problem, as I cannot follow the instructions all the way through, or they are not properly suited to my problem/setup. So I was wondering if someone would be kind enough to walk me through it, at a rate that I can understand.

So far, I have the usb input, the usb ID of 07d1:3c16 and ndiswrapper is installed (I did both the code, and the graphical front). The driver is installed and the device present, though this happens ```
:~$ ndiswrapper -l
WARNINGL All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release,
drt2870 : driver installed
device (07D1:3C16) present
```
Like I said, I'm new to all of this, kind of learning as I go along. If anyone would be able to help, I would be very grateful. I bought this, unsure of whether it would work, so I have 29 days left in the return policy....

Thanks again in advance

---

### Post by flash63 on 2010-06-26
Hello,
try this
```

sudo modprobe -rf ndiswrapper
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07D1 3C16" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
sudo iwlist scan

```

---

### Post by kakonsan on 2010-06-26
Wow, thats crazy, it worked perfectly, I can scan, and recognize all networks around. The device is finally activated. now. Thank you so much. But I'm not finished yet...I figured this might become a problem from the beginning, and it turns out it is. The wireless router I use is an Apple Express. For all the non-Apple computers I use, I install the Airport Utility through the CD drive. But those are Windows, and have CD drives, this is Linux, and no CD drive. So, do you think you would be able to help?

*EDIT* Also, when I shut my computer down, and restart, the device reverts back to what it was before, but can be fixed by redoing that code. Is there a way to make it permanent? Or a quick way to run the code on startup so I don't have to everytime?

---

### Post by flash63 on 2010-06-26
OK, let's remove the Win-Driver and ndiswrapper
```

sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/ndiswrapper/*
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9

```
Create a new udev-Rule to load the driver rt2870sta automatically
```

sudo gedit /etc/udev/rules.d/10-wlan.rules

```
Insert the following code and save the file
```
# UDEV-Rule for D-Link DWA-125 ID 07D1:3C16
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c16", RUN+="/sbin/modprobe rt2870sta"
```
Activate it (or restart)
```
sudo service udev reload
```
Connect the Stick.

---

### Post by kakonsan on 2010-06-26
Okay, so that works perfectly too, thanks again. Now its just the issue of not actually being able to connect to my WiFi, because its an Airport Extreme. Any ideas?

*EDIT* Also, the network panel on the top tool-bar disappeared when I restarted, not really necessary, but it was helpful.

---

### Post by flash63 on 2010-06-27
Hmm,
click right on the upper Panel > Add to Panel > "Indicator Applet" ("notification area") > Add

If necessary
```
sudo service network-manager restart

```
Checkout the configuration file
```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```
Preferences must be
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```

Use WPA2-AES (CCMP) Encryption an not WPA/WPA2 mixed mode for a trouble-free and safe connection with the Network-Manager. That's a feature of your Airport Extreme Router.

---

### Post by kakonsan on 2010-06-27
Wow, you are a god. Thank you so much for helping me, everything works great, except that I can't seem to get the applet back, but thats not a major problem, since I should only be connecting to the one network. Thanks again, you're a great help.


*EDIT* I've got the applet back, turns out it was part of the notification area, instead of the indicator applet.

---

### Post by flash63 on 2010-06-27
Thank's for your friendly reply. I hope your WiFi works fine.

I use the german localisation and some things are a bit different compared to the interational (english) version.

Best regards from Germany
Rainer

---

### Post by Zanzacar on 2010-08-10
> **flash63 said:**
> Hello,
try this
```

sudo modprobe -rf ndiswrapper
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07D1 3C16" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
sudo iwlist scan

```


After doing this my windows 7 os wont reconize my D-link. Even after I uninstalled the drivers and reinstalled them. It work fine on unbuntu though that is for sure, the only problem is that after each restart I have to open the terminal and redue it all again.

Any thoughts? Does the install/edit that you wrote above in the quote change anything on the device, or drivers on the windows side?

Thanks in advance.

---

### Post by CherryBear on 2011-08-12
> **flash63 said:**
> Hello,
try this
```

sudo modprobe -rf ndiswrapper
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07D1 3C16" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
sudo iwlist scan

```

I just want to say thanks for this. It worked perfectly! :D

---

### Post by mym2f on 2011-09-18
Hi flash63 .... 
I am a new user of Ubuntu (64-bit) system

I can see that your codes work from the first try ... ^_^

Please help me to get my DWA-126 usb adapter working so that I can crack some WPAs !!

My Ubuntu is installed through VMware player and its kernel version is
2.6.38-11-generic.

The problem is that the interface is not detected (when using iwconfig).
But it seems that the device itself is detected bcuz when using lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 071d:3a10 D-Link System
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Waiting for your reply since I'v got tired from firmware and compat-wireless instruction and nothing will help me more than your magical codes
^_^

---

