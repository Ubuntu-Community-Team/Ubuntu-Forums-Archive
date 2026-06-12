---
title: "BCM 4306 yet again"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by billfinch on 2009-12-09
My first post..
I loaded a version of Ubuntu (gOS) trying to resuscitate an old Compaq M2000 laptop. No Linux experience, but all worked great except wireless. After 2 weeks and many hours of reading forums, I am about to give up. Here are details:
kernel = 2.6.24-25
wireless card=BCM4306 / 14e4:4320
I have tried included b43 driver with b43-fwcutter. Lights are on, but no association with my router either auto or command line. I can turn it on and off with ifconfig. I can see the driver with lshw-C network and get details with iwconfig.
Tried NDISwrapper, but this seems abogus approach as it conflicts with ssb which is always loaded by somebody. Remove and blacklist doesn't work with this thing.
So, has anybody ever gotten this thing to work with ANY version of Ubuntu? If so, could I get the recipe? I need detailed step by step as there are many things I don't know how to do like compile source to create some new kernel module (just one example).
Linux definitely is the answer for old laptops with limited memory. Makes an excellent netbook alternative if the damn wireless could work.

Thanks

---

### Post by dmizer on 2009-12-09
I did get the card to work with ndiswrapper, but only when thenative ssb module does not load.

Problem is that the ssb module loads no matter what, even if it is in the blacklist. I have been working on this for a few dayr with limited success.

Sometimes it works as it should, sometimes it doesen't.

---

### Post by billfinch on 2009-12-10
After my post I found this thread..
[http://ubuntuforums.org/showthread.php?t=939658](http://ubuntuforums.org/showthread.php?t=939658)
Not sure if you saw it but it claims to solve the problems using NDISWrapper. Maybe you could comment on this.
I am still trying to figure out why 9.10 doesn't work on the 4306 rev03. There has to be something such as wrong firmware being loaded or some conflict I cannot find. I can not get an association to the router with either Hardy or Karmic using b43, etc. Apparently the rev 02 works. I don't want to try NDIS approach until I am sure it is the only way.
One last question. If I try to use the Win XP driver, do I just need the inf and sys files in the same folder or are there other files from Windows that are needed??

---

### Post by dmizer on 2009-12-10
"Works" is relative. If you can get it to load correctly, the ssb driver works, but it only connects at 1mb and you have to be nearly sitting on top of the router for it to connect.

To make the card work at all with native drivers, you need to install b43-fwcutter, and make sure the ssb module loading the b43legacy driver instead of the b43-pci-bridge. Check this by looking at the output of lshw -C network.

I did get the card to work with ndiswrapper again. To make ndiswrapper work, you must uninstall b43-fwcutter. Blacklist both b43-legacy and ssb, and modify /etc/rc.local so it looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod b43legacy
rmmod ssb
modprobe ndiswrapper
exit 0
```

Also, make sure that the output of ndiswrapper -l looks like this:
```
$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
```
And that lshw -C network looks like this:
```
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wlan0
       version: 02
       serial: 00:0e:a6:22:ae:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ndiswrapper+bcmwl5[/COLOR] driverversion=1.53+Broadcom,03/23/2006, 4.40.1 ip=10.2.0.162 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

If everything looks right for ndiswrapper as I've described, you should be able to reboot and have the card work.

---

### Post by billfinch on 2009-12-14
Finally....

I got it going and here's how. First I went back to 8.04 Hardy. 9.10 Karmic wouldn't play nice.

First, it is imperative to get the right Win Driver, as all have noted. This is not trivial, as it appears BCM made a config du jour for the PC manf. I found the right one for my rev 03 card on the Compaq support site, not the HP support site. sp29361 for M2000 Presario.

I expamded this thing on my PC and copied the bcmwl5.inf and bcmwl5a.inf plus bcmwl5.sys to the Ubuntu machine into my user folder.

Then the technique is fairly simple. Thanks to Dapperme17 for the basics..You have to make sure the b43 and ssb modules are removed. I removed ndiswrapper as it was being loaded by somebody and I wanted a clean slate.

sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper

Installed the ndis gtk from the repository. I wanted to see what drivers I really was loading. Navigated to /home/bill/driver folder and selected both 5 and 5a as I wasn't sure what the significance of the a was. No complaints, so I checked with lshw after doing a network restart.

sudo /etc/init.d/networking restart
sudo lshw -C network

I saw the ndiswrapper+bcmwl5 as the driver used. No lights, so I tried the switch and damn if it didn't turn on and connect! As stated inother posts it is easy to lose track of where the hardware switches are set.

To make this permanent, I created a shell script to run at start up bsed on help from dmizer among others.

Here's the code. I called my script wireless.sh.

sudo gedit /etc/init.d/wireless.sh

then write the script....

#!/bin/bash

sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
modprobe ndiswrapper

Thats it. Save it. Now you have to make the script executable and update yet another file, rc.d.

sudo chmod +x /etc/init.d/wireless.sh
sudo update /etc/rc.d/ wireless.sh start s 50 .

The dot is important. Terminal should tell you the rcS has been updated

Reboot and it should all work.

This only took 3 weeks and there are probably a zillion things that could go wrong between distros and hardware and all. One thing for sure. b43 and ssb DO NOT WORK with the 4306 rev 03.

Thanks again to all that helped.

:D

---

