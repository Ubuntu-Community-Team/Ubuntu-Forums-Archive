---
title: "Issue with Gigafast WF 741-UIC USB wireless dongle"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Glaciusor on 2009-05-17
I recently obtained several "obsolete" computers that I am putting Ubuntu 9.04 on, by obsolete I mean they were considered obsolete by the institution I purchased them from because they can't support Vista, but they easily handle XP. I have a Gigafast WF 748-UIC dongle that I bought to give my Win98 desktop a wireless connection, and I tried using it on the Ubuntu boxes and it works without any problem.
 
The problem is I gave one of these machines to my stepdad as a gift, bought a similar device for that computer for them (they bought it through me), and I didn't compare the exact numbers when I grabbed it. I got it in the mail today and it looked different from mine, and it is a 741 not 748. It doesn't connect to the network right, although I can view wireless networks just fine. I tried using the driver for Linux included and they have you going in and using "make" a lot. One thing appears to require some source code in /usr/src/(linux version here). They had it set up for 2.4, but I have 2.6 and I think something is different.
 
I'm at the point where I am using "make" to build their driver, however their setup requires me to point them to the "Linux source directory", and when I do I get this message:
"Linux source tree /usr/src/linux-headers-2.6.28-11 is incomplete or missing! The kernel header files are present, but not the full source code. See the HOWTO for a list of FTP sites for current kernel sources."
 
I get from this that I don't have the source code in the /usr/src directory, and I don't understand how to fix this. I tried Google for a little while but it didn't provide a solution.
 
Just to make sure the information is clear, I'm running Ubuntu 9.04 desktop and I'm trying to set up a Gigafast WF 741-UIC USB wireless dongle on it but it doesn't work automatically and I can't get their driver to build while getting that error message.
 
Any help would be greatly appreciated.

---

### Post by chili555 on 2009-05-17
> They had it set up for 2.4, but I have 2.6 and I think something is different.Yes, indeed. You can't put that 1949 Dodge flathead six in your 2009 Viper! I doubt that any amount of fiddling will get that moldy oldy to work. Was there a README in the package? Please post it as an attachment and we will look for a better solution.

---

### Post by chili555 on 2009-05-17
Please insert the device and open a terminal and do:```
lsusb -vv
```If the device turns out to be a Zydas 1201, please do:```
sudo modprobe zd1201
```Does your wireless spring to life?

---

### Post by Glaciusor on 2009-05-17
Well, I've attached the readme. Also, after going through the output of lsusb I found the device and it is a Zydas 1201, however modprobe doesn't do anything.
 
Just something interesting that this device does is that it does let me see wireless networks, and it does try to connect, but it fails after trying for a few minutes (timeout?). Also, the signal strength meter in the dropdown menu is at a constant percentage of about 25%, whereas my working device shows over 50%, and it varies a little bit.
 
Oh, and thanks for helping me with this ^_^.

---

### Post by chili555 on 2009-05-18
> Just something interesting that this device does is that it does let me see wireless networks, and it does try to connectWell, that means the device is working. No additional rusty 1949 parts are needed. Please open a terminal and do:```
iwconfig
```Please post the result here. 

*iwconfig* will show the logical name for your wireless interface, wlan0 or eth1, for example. Please run:```
dmesg | grep wlan0
```Substitute your interface if it's not wlan0. We should see some clues as to why it refuses to connect.

By the way, the README shows that a driver, prism2, is being built. It is wrong for your Zydas.

---

### Post by Glaciusor on 2009-05-18
Here's the output of iwconfig:
 
>  
glaciusor@glaciusor-desktop:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions.
wlan1 IEEE 802.11b ESSID:"" Nickname:"zd1201"
Mode:Managed Channel:6 Access Point: Invalid 
Bit Rate:11 Mb/s 
Retry RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

 
and here from dmesg
> 
glaciusor@glaciusor-desktop:~$ dmesg | grep wlan1
[ 743.119070] udev: renamed network interface wlan0 to wlan1
[ 758.512028] wlan1: no IPv6 routers present

 
The output from dmesg leads me to believe it isn't trying to use IPv4, and using ifconfig I don't get an inet addr, Bcast, or Mask for that device, but it does have an inet6 addr. I'm not sure if this is useful or not, but it was something I noticed that seemed a potential problem.
 
Is this what you wanted me to put up? Sorry it took so long, I had to do something this morning/early afternoon.

---

### Post by chili555 on 2009-05-18
I see nothing here that points to a problem. At some point, we could work on the udev wlan0 -> wlan1 issue, but I highly doubt it's keeping you from connecting.

When you click on the Network Manager icon, do you see your wireless interface? Your network? If you select your network and ask it to connect, what happens?

---

### Post by Glaciusor on 2009-05-18
I'm assuming you mean that icon where there is a dropdown menu that lets you select between the connected wired and wireless network connections and allows for VPN. If my assumption is correct, then yes, I can see my network and it recognizes the device is there, however it only shows a signal strength of about 25% in the dropdown menu, and that is a constant value whereas with my working device it varies. If I unplug the device that doesn't work, I see no networks at all so I know the device sees the networks. I just cannot actually connect. I don't get any errors when I try though, it just gives up after a few minutes.

---

