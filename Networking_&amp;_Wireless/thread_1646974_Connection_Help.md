---
title: "Connection Help"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by BurningDaylight on 2010-12-16
Thought I'd give it another go.

My D-Link DWA-131 dongle does not work with Ubuntu on my desktop.  This is the information I am given when I type 

Sudo lshw -c Netowork

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:22:b3:4e
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:de00(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:fdf00000-fdf0ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:e7:c3:18:e2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g
james@james-GA-MA770-UD3:~$ 

and then when I type "iwconfig":

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I honestly don't know what any of that means or how to fix it. Any help would be much appreciated.

I'm running a dual-boot Windows 7 64-bit and Ubuntu 10:10 64-bit, clean install.

PS: I've read the Samiux blog posting concerning the DWA-131 but I have absolutely no idea what he is talking about.  I tried typing all of that stuff into Terminal and it tells me no directory, no this, no that.  I'm lost.  Honestly, after two weeks of dicking around with it, I can't even fathom why I'm still trying, except that I haven't had a single problem on my laptop.  Still, this kind of glitchy **** is why I can't recommend Ubuntu to my mom or my sisters or my girlfriend or my friends.  Nothing is ever as simple as inserting a disk or downloading a file, double-clicking the .exe and following simple instructions until it loads.  And if I sound slightly frustrated, rest assured: I am.

---

### Post by chili555 on 2010-12-16
We could go on all day; I could defend Ubuntu and point you to several Windows whiner forums (and Mac forums for that matter) where it isn't always as simple as clicking an .exe to fix any problem. 

Or...

We could simply solve the problem. Your symptom is often caused by a firmware problem. Let's see if there are any kernel messages about the issue. Then let's find and install it. Please run and post:```
dmesg | grep -i firm
```Do you have an ethernet connection so we can download said firmware, or will we be relying on a USB key?

---

### Post by BurningDaylight on 2010-12-16
Thanks Chili and I'm sorry if I came off as an Ubuntu-bashing *******. I am not an Ubuntu-basher (I may be an ******* though.) In fact, part of my frustration stems from the fact that I've had such a nice experience with it on my laptop (I even removed Windows entirely because I always used Ubuntu instead) and I desperately want it my desktop. And now when I use Windows I wonder why it isn't as well organized or as Ubuntu.

But I guess the main reason for my frustration is that when it comes to computer programming, I'm about as knowledgeable as a monkey.

So again, I apologize, and thank you for helping.

Here is what I get when I type what you told me into Terminal:




james@james-GA-MA770-UD3:~$ dmesg | grep -i firm
[    1.242798] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.242799] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[   11.072151] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   11.072388] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   11.081268] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   11.081512] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   11.105152] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   11.105387] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   11.114023] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   11.114266] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
james@james-GA-MA770-UD3:~$

PS: I will be using a USB stick, since I don't have any access to the Internet without the Wi-Fi dongle.

PSS: I downloaded a zip package from Realtek called RTL8192SU_usb_linux_v2.6.0006.20100625 and transferred it to that computer but I have no idea how to install it.

---

### Post by chili555 on 2010-12-16
Grab this file on your USB stick and then drag and drop it to your desktop: [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)

Now open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192SU
cd Desktop
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```Remove the device and reinsert it and try again:```
iwconfig
```Is your wireless working? If not, let us see:```
dmesg | grep 819
```Thanks.

---

### Post by BurningDaylight on 2010-12-16
It WORKED!!! Thank you so much (and sorry again for being so pissy earlier.)

Should I still post the information you asked for to check for possible conflicts or anything? Or is it good to go?

Thank you,

Jim

---

### Post by chili555 on 2010-12-16
Hey, if it works, it's all good.

I know things are frustrating sometimes, even for me. I'm just glad it's working now. You have helped some searchers, too.

---

### Post by BurningDaylight on 2010-12-17
Hey Chili, I wanted to thank you again for helping me get the wireless working.

I'm a freelance writer, and having my documents automatically synced between computers with Ubuntu One is a huge advantage.  In the past, I had to go through the hassle of dragging my docs to Windows Skydrive or Google Doc, then downloading them, and then uploading, and then...well, you get the picture.

So you've been a big help.  Thanks.

---

### Post by wme7 on 2011-02-14
chili555 Thanks so much! 
I just installed the Ubuntu10.1 64 version and I was facing the same problem here. it worked for me too ;)

---

