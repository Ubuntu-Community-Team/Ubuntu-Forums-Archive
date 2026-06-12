---
title: "Want to Just Get Wifi Working?"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by BruisedQuasar07 on 2011-04-23
I had to use my new Thinkpad Edge (AMD Dual Core Model) in Windows 7 or Ethernet Cable in Ubuntu since I bought it. I do not have the time to invest seeking information, wadding through macho enter these 100 lines of code in terminal, etc to get the wifi card running right in Ubuntu (10.10), so until a feasible solution presented itself, I just booted into Win 7 when I needed to use Wifi.

I have found an excellent solution and it should work for anyone using any major Linux Distro because the solution is an excellent USB device and right in every Linux kernel since 2008 (version 2.6.13).

The device is the Wi-Fire long range Wifi adapter which gives you fast Internet up to 1,000 feet from access points. I do not need that level of power at home but it does come in handy away from home. 

Ubuntu software connected my Edge wifi card well enough but the driver gives highly unstable, inconsistent connections. One time, it connects quick and runs quick but always slows down to a crawl and\or begins disconnecting. From the same position with the same access point, Windows 7 gives excellent performance most of the time.

The Wi-Fire adapter is very Linux friendly. Its is true plug and play in Ubuntu 10.10 and most other more recent Linux distros. hField intentionally used the UW2353 radio which is included in Linux Kernel since 2008 (version 2.6.16 and newer). It operates on ZD1211rw driver which is in Linux Kernel drivers folder
under net>wireless.zd1211rw.zd.usb.c

I've been getting fast, undisrupted wifi with my Thinkpad T-60 with an Alpha High Gain USB adapter in Ubuntu 10.10 32-bit Gnome for weeks. It was plug and play, after I removed the internal wifi card and had wifi switch turned on. I find in laptops you will get false connected messages from Ubuntu if you have your wifi switch on "off." It must be turned on even if you are using a USB adapter.

In the Edge, I could not get the plug and play Wi-Fire to work until I clicked on the wifi icon and unchecked "enable wireless". The Ubuntu software must disconnect internal wifi before the USB Wi-Fire sotware can take over. 

Now I get outstanding Wifi using Ubuntu 10.10 and no longer need Windows 7 for anything. To see a Wi-Fire adapter and get info about it visit [http://www.hfield.com/](http://www.hfield.com/)

--Bruised

---

