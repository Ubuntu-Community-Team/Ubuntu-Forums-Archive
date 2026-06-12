---
title: "Installed Driver Via Ndiswrapper. Wireless Still Not Working?"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by Yoyoatw on 2011-03-30
Before I start off, I must say that I know NOTHING about Ubuntu. I only know how to run .deb files :P . So I installed my wireless driver via the graphical ndiswrapper (FYI my wireless adapter is a Proxim 8424-WD). It then said "Unable to see if hardware is present". After I exited out of that message, it said "Hardware: Present" (or something of that sort) next to the newly installed driver.  I tried searching for wireless networks and found none... I'm guessing something didn't work right. I used this command "lshw -C network" and got the following result.

```
administrator@administrator-EW209AA-ABA-s7415c:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:17:31:0f:7f:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:cfffe000-cfffefff ioport:e400(size=64)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:20:a6:55:02:b9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+ampsmnic driverversion=1.56+Proxim Corporation,11/28/20 multicast=yes wireless=IEEE 802.11b



```
All help will be appreciated. Thanks!

---

### Post by Yoyoatw on 2011-03-30
Got an update for you guys. This might help a lot. I went through all the steps in the NDISWRAPPER sticky tutorial, and I got stuck here:

```
administrator@administrator-EW209AA-ABA-s7415c:~$ dmesg | grep -e ndis -e wlan
[  354.414825] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  354.688889] ndiswrapper: driver ampsmnic (Proxim Corporation,11/28/2002, 2.1.0) loaded
[  355.580751] wlan0: ethernet device 00:20:a6:55:02:b9 using NDIS driver: ampsmnic, version: 0x20100, NDIS version: 0x501, vendor: 'ORiNOCO 802.11b USB', 0BB2:0304.F.conf
[  355.588030] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[  355.588035] wlan0: encryption modes supported: none
[  355.605843] usbcore: registered new interface driver ndiswrapper
[  355.657169] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  355.664247] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)


```
Ooops. Did not see the "Edit" button on my first post. Sorry for double posting.


EDIT: If you need more info, just tell me what command I need to use, and I'll post the results ASAP.

---

### Post by pytheas22 on 2011-03-31
The following line in your dmesg output suggests that ndiswrapper isn't liking the Windows driver you loaded into it for some reason:
```

[  355.664247] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
```

Often you'll have better luck with a different version of the Windows driver.  I would remove the one you currently have installed (you can do that via the GUI) and install a different version.  You may have to do some experimenting to find one that works.

[This page]("http://burnthesorbonne.com/ndiswrapper/o-z.html") mentions your device (search for "Proxim 8424-WD Wireless USB Adapter") and might provide ideas on where to find a driver that would work.  Posters there seem clearly to have had success with ndiswrapper and this device in the past, so it should work once you find the right Windows driver.

---

### Post by Yoyoatw on 2011-03-31
I used the specified driver (the one that came with the cd, as it said). I can now see wireless networks, but I can't connect to them... :( [WEP]

EDIT: I tried the same command as before, and I got A LOT of times. I am using the driver that the website specified.

"setting AP mac address failed"

---

### Post by Yoyoatw on 2011-03-31
Okay, so far I've tried 3 drivers (Win XP, Win 98, and Win 2000), and none of them are able to connect to my router.

I ran these 4 commands. I think these may help:

[COLOR=Red]lsusb [/COLOR](My wireless adapter is a usb, and it's funny that I don't see it on here)
```
administrator@administrator-EW209AA-ABA-s7415c:~$ lsusb
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:076c Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bb2:0304 Ambit Microsystems Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
[COLOR=Red]ndiswrapper -l[/COLOR]
```
administrator@administrator-EW209AA-ABA-s7415c:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
ampsmnic : driver installed
    device (0BB2:0304) present
```
[COLOR=Red]lshw -C Network[/COLOR]
```
administrator@administrator-EW209AA-ABA-s7415c:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:17:31:0f:7f:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:cfffe000-cfffefff ioport:e400(size=64)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:20:a6:55:02:b9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+ampsmnic driverversion=1.56+Proxim Corporation,11/28/20 multicast=yes wireless=IEEE 802.11b
```[COLOR=Red]
dmesg | grep -e ndis -e wlan[/COLOR]
```
administrator@administrator-EW209AA-ABA-s7415c:~$ dmesg | grep -e ndis -e wlan
[   15.583470] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   16.883477] ndiswrapper: driver ampsmnic (Proxim Corporation,11/28/2002, 2.1.0) loaded
[   17.772790] wlan0: ethernet device 00:20:a6:55:02:b9 using NDIS driver: ampsmnic, version: 0x20100, NDIS version: 0x500, vendor: 'ORiNOCO 802.11b USB', 0BB2:0304.F.conf
[   17.780075] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   17.780081] wlan0: encryption modes supported: none
[   17.796145] usbcore: registered new interface driver ndiswrapper
[   17.986163] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.000191] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
[   48.128063] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
[   48.928344] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.616029] wlan0: no IPv6 routers present
[   94.287364] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
[   99.396075] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
[  116.266979] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
[  124.063178] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
[  142.578691] ndiswrapper (iw_set_ap_address:566): setting AP mac address failed (C00000BB)
```
Thanks!

EDIT: Wow, I would double post...again. Sorry

---

### Post by pytheas22 on 2011-03-31
Thanks for the additional information.  I'm wondering if you'd have better luck using wicd to connect instead of NetworkManager.  You can install wicd from the Software Center, or by typing:

```
sudo apt-get install wicd
```

After it's installed, disable NetworkManager by typing:
```

sudo /etc/init.d/network-manager stop
```

Then launch wicd from the Applications>Internet menu and try connecting.  Note that in wicd, you have to enter the WEP key before trying to connect--it does not automatically prompt you for the key as NetworkManager does.

Please let me know how it goes with wicd.  If it doesn't work, it will at least help to narrow down the potential sources of the problem.

Also, I'm not sure I'll get a chance to respond as quickly as I like (maybe not till Saturday), but I'll do my best.

---

### Post by Yoyoatw on 2011-03-31
> **pytheas22 said:**
> Thanks for the additional information.  I'm wondering if you'd have better luck using wicd to connect instead of NetworkManager.  You can install wicd from the Software Center, or by typing:

```
sudo apt-get install wicd
```After it's installed, disable NetworkManager by typing:
```

sudo /etc/init.d/network-manager stop
```Then launch wicd from the Applications>Internet menu and try connecting.  Note that in wicd, you have to enter the WEP key before trying to connect--it does not automatically prompt you for the key as NetworkManager does.

Please let me know how it goes with wicd.  If it doesn't work, it will at least help to narrow down the potential sources of the problem.

Also, I'm not sure I'll get a chance to respond as quickly as I like (maybe not till Saturday), but I'll do my best.


Alright thanks I'll do that and report on it asap. For now though, I have some info. Seems that it can connect to networks that have no encryption (I used my itouch to create a network with no passkey on it). As soon as I made a wep key for the itouch hotspot, Ubuntu would not connect. Also I checked my router and it seems that the WEP key is 64bit as opposed to the 128 bit WEP, dynamic WEP and something else WEP on Ubuntu. Thanks, will post asap.


EDIT: Okay Sucessfully installed WICD. Tried to connect to router with encryption (WEP 64bit), failed (said, wrong password). Then I tried the other options for WEP, and one of them came up with the error "Could not get an IP address". I then removed the WEP key on my router. I tried connecting again, and it said "Could not get an IP address". I tried assigning it a static IP (instead of DHCP), and it didn't work either (error: "Could not contact router", or something like that) . Need help ASAP. Thanks! :)

---

### Post by pytheas22 on 2011-04-01
If you could connect to a network created using your iTouch but you can't connect to your router, even without a WEP key, then perhaps changing some of the settings on your router would get you connected.  Sometimes changing the channel or mode (e.g., from 802.11b/g to just 802.11g) can make a difference.  I'd disable all encryption on the router, then see if playing with other settings gets you anywhere.

Also, are you sure you don't have MAC address filtering enabled on your router, which could be preventing you from connecting a new machine?

---

### Post by Yoyoatw on 2011-04-01
> **pytheas22 said:**
> If you could connect to a network created using your iTouch but you can't connect to your router, even without a WEP key, then perhaps changing some of the settings on your router would get you connected.  Sometimes changing the channel or mode (e.g., from 802.11b/g to just 802.11g) can make a difference.  I'd disable all encryption on the router, then see if playing with other settings gets you anywhere.

Also, are you sure you don't have MAC address filtering enabled on your router, which could be preventing you from connecting a new machine?

I disabled the encryption on my router and BAM, it worked! But unfortunately I cannot leave it like that.... I think it has something to do with this:

```
[   17.780075] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015) 
[   17.780081] wlan0: encryption modes supported: none
```

But of course I know that my adapter does support encryption keys, because I use it with Windows :P

---

### Post by pytheas22 on 2011-04-02
That at least makes a little more sense...I was under the impression that you could not connect to your router at all, even with encryption disabled, and that it was only to your iTouch that you were able to connect.

The line you point to in dmesg about lack of encryption support does indeed appear problematic.  Unfortunately, after googling around, the only suggestion I can make on that front is, again, to try different versions of the Windows driver.  Even if the driver you currently have loaded into ndiswrapper is supposed to support encryption under Windows, ndiswrapper may have an issue with it for some reason.

I wish I could offer a more concrete solution, but I think the trial-and-error approach is your best bet for now.  If that doesn't get you anywhere we could try connecting to your router with encryption enabled from the command line, just in case ndiswrapper is lying when it says it has no encryption support, but I doubt that would change anything.  (On the other hand, sometimes things do work if you connect from the command line instead of via a GUI application like Wicd or NetworkManager.)

---

### Post by pytheas22 on 2011-04-06
Any luck on this?  I'm curious to see what you figure out.

---

