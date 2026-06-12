---
title: "Ubuntu 11.04 Realtek RTL8192SU firmware/driver issues"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by CODO69 on 2011-05-28
Ok time for the stereotypical opening line, I'm a complete noob to Ubuntu (Linux in general). I have been pulling my hair out (if I had any) for days trying to remedy my situation. A brief background on what's going on. I'm currently stationed in Afghanistan and while here, to get internet access you need to register your MAC address with the base to access the free Wifi hotspots. Well luckily for me there is a hotspot in range of my shop so I purchased a BlueProton WiFi 300 Mbps 802.11b/g/n MIMO USB 500mW High-Gain Adapter 2 Antennas by Gsky ([http://gadgetshop.co.tv/blueproton-wifi-300mbps-802-11bgn-mimo-usb-500mw-high-gain-adapter-2-antennas-by-gsky/](http://gadgetshop.co.tv/blueproton-wifi-300mbps-802-11bgn-mimo-usb-500mw-high-gain-adapter-2-antennas-by-gsky/)), registered the MAC address and then I shared the Internet connection across a wired hub so others in my shop could use it as well. That's under Windows 7. But now that I'm trying to learn how to use Ubuntu, it doesn't know what to do with the device. For days I've been Googleing the issue and have been to probably a dozen forums with no luck ([http://ubuntuforums.org/showthread.php?p=9931085](http://ubuntuforums.org/showthread.php?p=9931085), [http://ubuntuforums.org/showthread.php?p=10718746#post10718746, ]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")[http://ubuntuforums.org/showthread.php?p=9788240, ]("http://ubuntuforums.org/showthread.php?p=9788240")[http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/](http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/)) Just to name a few.

In the terminal when I enter the command 'lsusb', it'll recognize the USB wifi adapter as being there but nothing else. When I try to connect to it by clicking on the WiFi icon on the top right i see the internal wifi card in my laptop, but underneath that I see a shaded 'Wireless Network (Ralink 802.11 n WLAN)' and under that a shaded 'Device not ready (firmware missing)'. Through my readings of the forums, the general census was that the RTL8192SU drivers/firmware were in the wrong location. so I moved them from /lib/firmware/RTL8192SE to /lib/firmware/RTL8192SU, rebooted with still no luck. I'm running out of ideas. Unfortunately buying another WiFi adapter is a little out the question. I can't afford to keep buying adapters. There has to be a solution out there.

If you have any solutions for me to try, please keep in mind that Ubuntu is still very foreign to me (though I'm a pretty quick learner), so please don't assume I know exactly where to go or what to type/do. I Thank you in advance, and so do my fellow co-workers!

I.Y.A.A.Y.A.S.!

---

### Post by chili555 on 2011-05-28
I wish they were all this easy. Please check here:  [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)> Initially I was just going to copy the file and hope it worked, but I found the correct file in the debian svn repository. Although it has the same name, its md5sum is different:

Unplug the device. You will need an internet connection and then open a terminal and download the right stuff:```
wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin
```Now let's ditch the incorrect firmware:```
sudo rm /lib/firmware/RTL8192SU/*
```And now we move the firmware you downloaded to the correct location:```
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```Plug the device back in and post back to tell us how your wireless is working.

Stay safe and thanks for your service.

---

### Post by CODO69 on 2011-05-28
Thanks for the reply chili555. Well things didn't go well from the start:
1) The command 'wget [http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)' didn't work. All I got was a 404 error. So scrounging around on the net, I found an alternate link to download it.
2) sudo rm /lib/firmware/RTL8192SU/* gave me the error that it couldn't remove RTL8192SU because it's a directory.
3) When I actually looked in /lib/firmware/RTL8192SU i found the folder RTL8192SE that apparently was placed in there during one of the earlier attempts that I tried from another forum. inside that were all the drivers that should have been in RTL8192SU. So just to say I tried it, I copied them to the SU folder... Still no luck.
4) I plugged in the antenna and nothing, rebooted and still nothing.

Any other suggestions, or ideas what I may have done wrong?

---

### Post by chili555 on 2011-05-28
> When I actually looked in /lib/firmware/RTL8192SU i found the folder RTL8192SE that apparently was placed in there during one of the earlier attempts that I tried from another forum. inside that were all the drivers that should have been in RTL8192SU. So just to say I tried it, I copied them to the SU folder... Still no luck.Those are the firmware files that are known *not* to work according to the bug report. Please remove them:```
sudo rm -rf /lib/firmware/RTL8192SU/*
```-rf means recursive and force. That is, remove everything inside /lib/firmware/RTL8192SU and any directoies and files inside and inside there, ad infinitum.

Next, place the file you downloaded in it:> So scrounging around on the net, I found an alternate link to download it.You should end up with /lib/firmware/RTL8192SU/rtl8192sfw.bin; the latter being the good new firmware you downloaded and none other. 

You shouldn't need to reboot; the insertion of the device should automagically trigger driver and firmware loading if we have all our firmware ducks in a row. Post back, I'm here for you. I hope the file you found is the new, good and not the old, bad. I'm going to Google a bit.

Ammo, eh? 

Stay safe.

---

### Post by chili555 on 2011-05-28
Here is the link I've been looking for! [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

The link is alive. I suggest you download the firmware afresh to be sure.

Whew! I was just about to doubt my mojo.

---

### Post by CODO69 on 2011-05-28
Chili, I appreciate all your help but still no luck. I deleted the contents of RTL8192SU again, downloaded the file from the new link you posted, copied it to the correct folder again and still nothing. I've attached a few screen captures if they'll help at all. As I'm trying to learn Ubuntu, just throwing an idea out there. Could I have the wrong drivers installed or not at all? It's been days I've been messing with this an don't remember all that I've done. The install disk that came with the WiFi adapter came with Linux drivers on it (granted they're from 2009) And Heck if i know if I installed them correctly or at all. This is the Windows trouble shooting side of me coming out lol sorry.

---

### Post by chili555 on 2011-05-28
Let's get back to basics. First, let's identify the USB device for sure. Please run and post:```
lsusb
dmesg | grep 8192
```The pipe symbol | is on the right side of my US keyboard on the same key with \. 

Are you sure that RTL8192SU is the correct driver? 

I realize it's late over there but I'll be here for several hours if you need me. I'm committed to getting you going sooner than later.

---

### Post by CODO69 on 2011-05-28
Ok I bought this from Amazon ([http://www.amazon.com/High-Gain-Wireless-300Mbps-802-11b-Network/dp/tech-data/B002XVTDNO/ref=de_a_smtd](http://www.amazon.com/High-Gain-Wireless-300Mbps-802-11b-Network/dp/tech-data/B002XVTDNO/ref=de_a_smtd)) and the website [http://gadgetshop.co.tv/blueproton-wifi-300mbps-802-11bgn-mimo-usb-500mw-high-gain-adapter-2-antennas-by-gsky/](http://gadgetshop.co.tv/blueproton-wifi-300mbps-802-11bgn-mimo-usb-500mw-high-gain-adapter-2-antennas-by-gsky/) says it has the rtl8192su RF chipset on it. now lets see what the commands yo told me to enter have to say....

chris@Toshiba:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@Toshiba:~$ dmesg | grep 8192
[    1.027824] agpgart-intel 0000:00:00.0: detected 8192K stolen memory

I'll be up for a while as well, it was my day off today and slept way more than I should have. I noticed you have an AIM account, would it be better for you (certainly quicker) if I IM you on it?

thanks again

---

### Post by chili555 on 2011-05-28
It's better to put it on the forum so the searchers can learn from our experience. Hopefully, when I'm done, you'll have it all set but I'll turn on my AIM anyway.> 148f:3072 Ralink Technology, Corp. RT3072 Wireless AdapterThis is not an RT8192SU device. It is driven by a module called rt2870sta.```
$ modinfo rt2870sta | grep 3072
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3072[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```The trouble is, it's also claimed by another crummier driver rt2800usb. Let's tweak a couple of files and reboot.```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modules
```Add one thing:```
rt2870sta
```Proofread carefully, save and close gedit. Now reboot and tell me how beautifully your wireless is working!

---

### Post by CODO69 on 2011-05-28
All my kudos to you good Sir! It works like a charm. Thanks you so much. Feel a bit stupid about trying to use the incorrect driver but eh live and learn. Guess if it's on the internet it's not always true. I thank you once again, and so do all of my co-workers. You've helped restore our morale Wifi in our shop.

P.S. lol I'm guessing you googled and figured out I'm AMMO.

I.Y.A.A.Y.A.S.!

---

### Post by chili555 on 2011-05-28
Please check private messages at the top right.

---

### Post by chili555 on 2011-05-28
> **CODO69 said:**
> All my kudos to you good Sir! It works like a charm. Thanks you so much. Feel a bit stupid about trying to use the incorrect driver but eh live and learn. Guess if it's on the internet it's not always true. I thank you once again, and so do all of my co-workers. You've helped restore our morale Wifi in our shop.

P.S. lol I'm guessing you googled and figured out I'm AMMO.

I.Y.A.A.Y.A.S.!It was my pleasure. I just wish I could do more. Call on us here any time.

---

### Post by baxter33 on 2011-10-08
Yaahoo!! Worked like a charm for my Gigaware 25-1197 usb adapter from RahoShack(which turns out to be a Ralink 3071). Gettin downloads of 1.2 MB/s thru 5 walls & lovin it! Thank-You.   Baxter33

---

