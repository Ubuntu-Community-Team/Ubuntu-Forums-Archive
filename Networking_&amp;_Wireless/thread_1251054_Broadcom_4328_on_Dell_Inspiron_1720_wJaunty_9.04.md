---
title: "Broadcom 4328 on Dell Inspiron 1720 w/Jaunty 9.04"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by hofstra14 on 2009-08-27
As noted in the title; I installed 9.04 Jaunty on a Dell Inspiron 1720 - ditching Vista. Based on previous experience with other Inspiron laptops I decided to cut to the chase and go straight to the ndiswrapper based configuration. Here is what I did:

[LIST=1]
[*]Installed [COLOR=red]ndisgtk[/COLOR]
[*][COLOR=black]Blacklisted the native drivers[/COLOR]
[*]ran lspci to determine the wireless card; it reported [COLOR=red]14e4:4328[/COLOR], a Broadcom 4328 (no surprise)
[*]obtained the correct windows drivers for the card from the Dell website; [COLOR=red]bcmwl6.inf[/COLOR] and [COLOR=red]bcmwl6.sys[/COLOR]
[*][COLOR=black]installed the drivers which reconized the hardware (but I get an error when I click on Configure)[/COLOR]
[*]and... NOTHING
[/LIST]When I run ifconfig there is no listing for the wlan0 interface, same when I run iwconfig. I know the wireless card is there and working because it worked previously under Vista.
 
I've been through the various forum threads and I can't find anything different than what I did. 
 
Ideas?
 
Thanks in advance

---

### Post by t0mppa on 2009-08-27
Well, what does the error say? Usually errors tend to tell you what went wrong.

And another thing to check is **lshw -C network** from the terminal and see if your interface really gets associated with Ndiswrapper. Simply blacklisting b43 and ssb won't work, if your wired interface is using b44 as a driver since b44 uses the ssb module as well (and thus its gets around the blacklisting), which tends to hog your wireless interface before any other drivers have a chance to get associated with it.

---

### Post by hofstra14 on 2009-08-27
> **t0mppa said:**
> Well, what does the error say? Usually errors tend to tell you what went wrong.
 
And another thing to check is **lshw -C network** from the terminal and see if your interface really gets associated with Ndiswrapper. Simply blacklisting b43 and ssb won't work, if your wired interface is using b44 as a driver since b44 uses the ssb module as well (and thus its gets around the blacklisting), which tends to hog your wireless interface before any other drivers have a chance to get associated with it.
 
Thanks for the rpely; there is no error message.  But I will try the lshw when I get back in front of the screen later.
 
Interesting comment about b43 and ssb.  If I rmmod b43 and ssb and then modprobe both of them, I can get wireless to appear as eth1 which is pretty bizarre.

---

### Post by Ayuthia on 2009-08-27
The bcmwl6 files is the problem.  As far as I know, the Vista drivers do not work with NDISwrapper yet.

As for why you are able to see something as eth1, the 4328 card can also use the Broadcom STA drivers (wl).  That can be found under System->Administration->Hardware Drivers.  It is written by Broadcom.  If you don't want to use that one, you will also have to blacklist it.

---

### Post by hofstra14 on 2009-08-27
> **Ayuthia said:**
> The bcmwl6 files is the problem.  As far as I know, the Vista drivers do not work with NDISwrapper yet.

As for why you are able to see something as eth1, the 4328 card can also use the Broadcom STA drivers (wl).  That can be found under System->Administration->Hardware Drivers.  It is written by Broadcom.  If you don't want to use that one, you will also have to blacklist it.
Thanks - I did not know that about ndiswrapper not supporting the Vista drivers.  So I need to dump the bcmwl6 drivers and go back to ?native? wl?  If I do that do I still need ndiswrapper?  Or what if I used XP drivers for the 4328 card instead of bcmwl6 (assuming I can find them)?

---

### Post by hofstra14 on 2009-08-28
> **hofstra14 said:**
> Thanks for the rpely; there is no error message.  But I will try the lshw when I get back in front of the screen later.
 
Interesting comment about b43 and ssb.  If I rmmod b43 and ssb and then modprobe both of them, I can get wireless to appear as eth1 which is pretty bizarre.
OK, when I run lshw -C network it show the 4328 driver as b43-pci-bridge.  I went back and did a clean install, just to make sure I was not running myself in circles and got the same thing out of the box.  It also shows Width = 64 for the 4328, Width = 32 for the ethernet adapter.  Does this mean it's a 64 bit interface and needs a 64 bit driver?
 
 
I tried installing b43-fwcutter as suggested in the work arounds thread for Jaunty, but that did not work either.

---

### Post by hofstra14 on 2009-08-28
According to the Wiki showing the supported cards [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI) ; the BCM4328 is supposed to work 'out of the box' using the wl restricted driver.  How do I get that driver to load on the 4328?
 
Thanks

---

### Post by t0mppa on 2009-08-28
*b43-pci-bridge* is the "driver name" for the module called ssb. Why I mentioned it is a longer story (*) and possibly irrelevant. To answer a few of your questions:
[LIST]
[*]no, you don't need Ndiswrapper for wl and like Ayuthia already told you and it can be found from System / Administration / Hardware Drivers although it might need a working Internet connection (through your wired card) to install itself properly
[*]yes, you can also use Ndiswrapper with older drivers, but then you can't have wl or b43 running, always have to pick just one driver
[*]no, you don't need a specific 64 bit driver for wireless interface
[/LIST]
(*) Simply blacklisting b43 will work for most cases, but if you happen to have a wired card that uses b44 (that also uses ssb and always loads it, even if it's blacklisted), you'll have to make a simple script that rmmod's b43, b44 & ssb, then modprobes whichever other driver (other than b43) you choose to use and then modprobes the b44 back. The problem is that b44 tends to get loaded before any wireless drivers, so it loads up ssb, which in turn hogs the wireless, when it is not associated with any drivers yet thus causing it not to get associated with the other drivers that get loaded later.

---

### Post by BigCityCat on 2009-08-28
I use the wl driver. Here is the thread whith an explanation of what I did.

under Bigcitycat. Not sure if this applies to you but maybe you can get some clues here.

[http://ubuntuforums.org/showthread.php?t=1176117&page=4](http://ubuntuforums.org/showthread.php?t=1176117&page=4)

---

### Post by hofstra14 on 2009-09-15
The following script resolved the problem;

#!/bin/sh
# 
echo "Reconfigure Broadcom BCM4328 Wireless Driver"
echo ""
#
modprobe -v -r b44
modprobe -v -r ssb
modprobe -v wl
modprobe -v ssb
modprobe -v b44
#
iwconfig eth1 ESSID "kaos"
iwconfig eth1 rts 2346
iwconfig eth1 frag 2346
#
echo "Done"
exit 0

Thanks to everyone who posted help on this.

---

