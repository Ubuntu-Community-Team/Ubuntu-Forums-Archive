---
title: "WiFi adapter works with my desktop; new alternate install can't find it"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by algernon83 on 2011-03-27
I have a USB WiFi adapter that my Ubuntu desktop install (10.10) automatically detects, and it works great. I just used the alternate installer to set up an old box as a server, and it doesn't install the driver for the adapter. lsusb finds the adapter, but I don't get a wlan* listed in /dev/.

Can someone please advise how I can determine what module(s) are used to run this adapter on the desktop so I can load them on the older box? Or is there some package I should install from the CD to help auto-detect the adapter?

---

### Post by mrhhug on 2011-03-27
make and model of wifi adapter? 

does the manufacturer supply linux drivers right on their web page? 

can you connect this machine to the Internet some other way temporarily to see if ubuntu can find the drivers once you plug it in?

---

### Post by Cheesehead on 2011-03-27
Since it shows up in lsusb, take a look at /var/log/dmesg. Try filtering (grep) for 'usb' or 'wlan' or 'udev'. Most common problems (interface renamed, missing firmware, can't find driver, etc) show up there.

mrhhug is right: Also do a search-engine check for your chipset (which you determine using 'lspci -vv') to find others who have had this problem, what the problem was, and how they resolved it...assuming you have the same problem.

If it's really a firmware or driver issue, check and see if the 'linux-backports-modules' package will help before you spend a lot of time installing drivers from websites.

---

### Post by algernon83 on 2011-03-27
Thanks a lot for your help so far. To answer your questions:

1. It's a Tenda w311u. The chipset is supported by the rt2870sta module.
2. According to links I found, this hardware is sometimes not recognized by the driver as provided, but will work if modprobe is told to use it. So I followed instructions to do so, and modprobe will load the rt2870sta driver, but it doesn't seem to put a wlan0 into /dev -- even though dmesg indicates that the device is connected to /dev/wlan0.

Again, thanks -- I'll reply again in the morning with dmesg output.

---

### Post by TBABill on 2011-03-27
[http://ubuntuforums.org/showthread.php?t=1586945&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=1586945&highlight=rt2870)

Message # 8 in that thread has your answer I hope.

---

### Post by algernon83 on 2011-03-27
Thank you, Bill, but no such luck I'm afraid.

This is what dmesg tells me after removing and re-inserting the module (having added the entries you mention in the other thread to /etc/modules and /etc/modprobe.d/blacklist.conf and rebooting):

[  152.856126] usbcore: deregistering interface driver rt2870
[  152.856281] rtusb_disconnect: unregister usbnet usb-0000:00:07.2-1
[  152.856314] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=wlan0!
[  152.881443]  RTUSB disconnect successfully
[  152.884385] <--- rtusb exit
[  158.584280] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  158.720471] rtusb init --->
[  158.725572] === pAd = c8f5f000, size = 472668 ===
[  158.725608] <-- RTMPAllocAdapterBlock, Status=0
[  158.765120] usbcore: registered new interface driver rt2870


I'm afraid nothing calls out to me -- there's nothing I interpret as an error, yet I still don't have a /dev/wlan0.

---

### Post by TBABill on 2011-03-28
Can you try the same thing, but precede rt2870 in /etc/modules with # and leave rt2870sta as is?
 
Also, the system may not designate wireless as wlan0. Sometimes it can be designated eth1 or other.

---

### Post by algernon83 on 2011-03-29
I tried that change, too, but I'm afraid I'm still stuck. No /dev/eth* or /dev/w*. Thanks anyway.

---

### Post by algernon83 on 2011-03-29
Well, this is embarrassing. Turns out the alternate installer didn't add the libs for wifi support, so the driver wasn't going to do much! I copied the packages for wireless-tools and libiw30 with a USB key and installed them, and I now have a wlan0. Thanks again for your contributions everyone!

---

