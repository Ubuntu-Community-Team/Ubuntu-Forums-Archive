---
title: "Cannot install b43-fwcutter"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by jstrowe on 2009-10-10
I have a machine with a Broadcom wireless adapter that I cannot get to run with 9.04.

john@john-laptop:~$ lspci -vnn | grep 14e4
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

I got it to work with 8.10, but I had to try so many things to get it to work, I don't remember what did the trick. It's a dual boot machine with XP. I had to scratch and re-load, so I re-installed XP, which works, and I updated to 9.04. The wireless no longer works and I can't get it to work.

When I use "hardware drivers" to activate the Broadcom b43legacy driver, I get a message that Jockey has crashed and the driver does not show as activated. It says that I should post a report to jockey-common, but there's no link and I can't find where it says I should go.

When I try to use "sudo apt-get install b43-fwcutter" it always times out when trying to access [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2). I had the same problem with 8.10. I can access this file with other machines, but not with my Ubuntu machine.

How can I install b43-fwcutter from a file and not from the web?

I have tried to use ndiswrapper, but I can't find a .inf file for my adapter in windows.

What else can I try?

Thanks,
John

---

### Post by menikmati on 2009-10-10
try installing b43-fwcutter by typing

sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter

make sure you answer with YES when prompted if you want to fetch the firmware
restart your computer and check if it work

it worked fine for me, thanks to sam_delta

---

### Post by jstrowe on 2009-10-10
> **menikmati said:**
> try installing b43-fwcutter by typing

sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter

make sure you answer with YES when prompted if you want to fetch the firmware
restart your computer and check if it work

it worked fine for me, thanks to sam_delta
Thanks, but that is exactly what I cannot do on my machine for some reason.

It still tried to fetch a file from mirror2.openwrt.org and timed out instead of accessing it. I have never been able to access mirror2.openwrt.org on my Ubuntu machine. I can access anything else, but not that.

Is there any way that I can get the files on another machine, put them on a flash drive and install it from the flash drive?

Here is what happens when I install b43-fwcutter:

> john@john-laptop:~$ sudo aptitude install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  b43-fwcutter 
0 packages upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 0B/16.7kB of archives. After unpacking 111kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 108926 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a011-5_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:011-5) ...
--2009-10-10 15:41:57--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... 78.24.191.177
Connecting to downloads.openwrt.org|78.24.191.177|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652866 (638K) [application/octet-stream]
Saving to: `wl_apsta-3.130.20.0.o'

100%[======================================>] 652,866      259K/s   in 2.5s    

2009-10-10 15:42:00 (259 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--2009-10-10 15:42:00--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Resolving mirror2.openwrt.org... 88.198.39.176
Connecting to mirror2.openwrt.org|88.198.39.176|:80... failed: Connection timed out.
Retrying.

--2009-10-10 15:45:10--  (try: 2)  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Connecting to mirror2.openwrt.org|88.198.39.176|:80... 


---

### Post by menikmati on 2009-10-10
Hmm strange, you can check this link..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Really don't know why your connection is getting timed out

---

### Post by jstrowe on 2009-10-10
> **menikmati said:**
> Hmm strange, you can check this link..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Really don't know why your connection is getting timed out
You did it!

Once I figured out what that link was telling me what to do, I was able to get it to work. Also, I needed to unplug the USB wireless that I was using so that installing b43-fwcutter from the CDROM did not get hung up getting the files from the net.

Thanks loads!

---

