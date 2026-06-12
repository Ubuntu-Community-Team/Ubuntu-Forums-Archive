---
title: "Rosewill RNX-G1W USB wireless card issues (RTL8187L)"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by nash black on 2010-04-23
Hi 
Sorry for the repost... I posted this in Absolute Beginner Talk because I thought that this place might be too technical for me, but I didn't get much of a response there...

Does anyone know where I can find a decent driver for this USB wireless card? It uses the RTL8187L chipset for Ubuntu 9.10?

I can connect to my wi-fi network, but I can only seem to download any data for 10 seconds to a minute after connecting. After this it still says that it is connected but updates and web browsing do not work. The connection works fine on my windows partition with the drivers that came with the device.

I found this, old thread about the issue but I frankly have no idea what these people are talking about:

[http://ubuntuforums.org/showthread.php?t=911581](http://ubuntuforums.org/showthread.php?t=911581)

There do appear to be linux drivers on the CD that came with the device but I don't understand how to install them and the above thread seems to suggest that I shouldnt bother trying...

There is a folder titled Linux on the driver CD which contains two folders, a .zip of each of them is attached if it helps.

I also found this and tried it will a lot of errors and confusing output...

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

update:
Interestingly enough, the USB wireless card works rather well when plugged into my monitor's usb ports, just not the ones on my computer itself... This is especially strange because the monitor USB ports just connect directly to the ones on my computer through a second USB cable...

It still isn't working as well as it does on the Windows partition, so I am still thinking that I might have some driver issues... Maybe it just won't perform as well on Ubuntu, but it would be nice if I could get it up to par with its performance with the standard windows drivers on the XP partition.

Here is some terminal fun if it helps...

*******@Computus:~$ dmesg | grep -e ndis -e wlan
[   15.474814] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.770506] wlan0: authenticate with AP 00:1f:33:26:51:32
[   50.772627] wlan0: authenticated
[   50.772630] wlan0: associate with AP 00:1f:33:26:51:32
[   50.774633] wlan0: RX AssocResp from 00:1f:33:26:51:32 (capab=0x411 status=0 aid=2)
[   50.774636] wlan0: associated
[   50.778271] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.860018] wlan0: no IPv6 routers present
*******@Computus:~$ sudo modprobe ndiswrapper
[sudo] password for *******: 
*******@Computus:~$ dmesg | grep -e ndis -e wlan
[   15.474814] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.770506] wlan0: authenticate with AP 00:1f:33:26:51:32
[   50.772627] wlan0: authenticated
[   50.772630] wlan0: associate with AP 00:1f:33:26:51:32
[   50.774633] wlan0: RX AssocResp from 00:1f:33:26:51:32 (capab=0x411 status=0 aid=2)
[   50.774636] wlan0: associated
[   50.778271] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.860018] wlan0: no IPv6 routers present
[  715.288597] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  715.290742] usbcore: registered new interface driver ndiswrapper
*******@Computus:~$

---

### Post by nash black on 2010-04-27
Any ideas..?

I'm liking ubuntu so far, but without reliable Internet it would be difficult for me to rely on it as a primary OS...

---

