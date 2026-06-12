---
title: "Sitecom WL-011v2 not installed?"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by RubenK on 2009-06-25
How can get my sitecom wl-011v2 to work in Ubuntu 9.04?

---

### Post by pytheas22 on 2009-06-25
Please open a terminal, run the following commands and post the output here:
```

lsusb
lspci -nn
uname -rm
lshw -C Network
```

With that information we'll be able to help you.

---

### Post by RubenK on 2009-06-25
lsusb:
```
Bus 001 Device 002: ID 1970:0000 Dane-Elec Corp. USA 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
lspci -nn:
```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
01:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)
02:00.0 RF controller [0d10]: Advanced Micro Devices [AMD] Am 1771 MBW [Alchemy] [1022:2003] (rev 04)
```
uname -rm:
```
2.6.28-13-generic i686
```
lshw -C Network:
```
  *-network
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:c6:d8:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:d4:f2:3a:3d:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

Hope it helps!

---

### Post by pytheas22 on 2009-06-25
Thanks for the information.  Unfortunately I'm going to have to ask for a bit more, because I originally thought this was a USB device, but I guess it's PCMCIA, correct?

If you could please also post a link to the Windows driver that you used to make this device work, that would be really helpful.  With that information, I can write you out instructions for making the card work in Ubuntu.

---

### Post by RubenK on 2009-06-25
No problem. Under windows, I (or rather my dad) used the supplied disc, but I take it, it's also available on the web: [click](http://www.sitecom.com/drivers_result.php?groupid=5&productid=134&version=V2;001).

---

### Post by pytheas22 on 2009-06-26
Thanks for that link--it makes things easier.

To get the card installed, please run these commands (you will need to be plugged into ethernet for these commands to work; if that's impossible, let me know):
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://www.sitecom.com/showdownload.php?id=1133
unzip showdownload*
sudo ndiswrapper -i Driver/WinXP/wlannic.inf
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot.  After the reboot, the wireless card will hopefully work.  If it still doesn't, please post the output of:
```

dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by RubenK on 2009-06-26
Works like a charm! Now let's set up the rest...

---

### Post by RubenK on 2009-06-26
Ok so the network card works (I guess...). iwlist scanning gives me a list of signals, but I can't connect to any. I give the proper SSID and the proper WEP Key, but it won't connect...

---

### Post by pytheas22 on 2009-06-27
> Ok so the network card works (I guess...). iwlist scanning gives me a list of signals, but I can't connect to any. I give the proper SSID and the proper WEP Key, but it won't connect...

How are you trying to connect?  Are you using the command line or the graphical interface (named NetworkManager)?  Are you sure that the WEP authentication method (open vs. shared key) and key type (hex vs. ASCII) are correct?  Usually NetworkManager can auto-detect what these should be, but sometimes it gets it wrong so please double-check.

You may also want to try installing wicd, an alternative to NetworkManager that may work better.  You can install wicd by typing:
```

sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Can you connect using this application?

It would also be helpful if you could please post the output of:
```

sudo iwlist scan
```

and tell me the name of the network you're trying to connect to.

---

### Post by RubenK on 2009-06-27
Thank you for wicd! It will not however, connect... I'm positive I've entered the correct WEP key (hex).

Here is the interesting part of iwlist scan:
```
Cell 02 - Address: 00:E0:98:50:68:64
                    ESSID:"Kwast"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```
Hope it helps! And thank for helping me so far!

---

### Post by pytheas22 on 2009-06-27
Thanks for the output.  Let's try connecting from the command line.  If even this doesn't work, then we'll probably have to try a different driver.

Please run these commands and post the output:
```

sudo killall dhclient
sudo iwconfig wlan0 mode managed channel 11 essid "Kwast" key **yourWEPkeyhere**
sudo dhclient wlan0
ifconfig wlan0
dmesg | tail -25
```

(Obviously, fill in your WEP key where appropriate.  This assumes you're using a hex WEP key and open authentication.  A hex WEP key would only contain the letters A-G and numbers.  If your router doesn't use open authentication and a hex key, let me know.)

Hopefully at this point you'll be connected and able to browse web pages.  But if you're not, this will at least give me a better idea of what's wrong.

---

### Post by RubenK on 2009-06-27
dhclient:
```
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
rnet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0c:f6:0c:7c:ba
Sending on   LPF/wlan0/00:0c:f6:0c:7c:ba
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
^Z
[2]+  Stopped      
```
It started to repeat those last two lines only with different intervals, so I terminated it.

dmesg:
```
[   14.644714] type=1505 audit(1246133087.085:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1884
[   14.644935] type=1505 audit(1246133087.085:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1884
[   14.645005] type=1505 audit(1246133087.085:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1884
[   14.645057] type=1505 audit(1246133087.085:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1884
[   14.697919] type=1505 audit(1246133087.137:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=1889
[   14.854060] type=1505 audit(1246133087.293:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1893
[   14.854370] type=1505 audit(1246133087.293:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1893
[   14.889708] type=1505 audit(1246133087.329:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1897
[   21.298677] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.795578] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.795583] Bluetooth: BNEP filters: protocol multicast
[   21.839962] Bridge firewalling registered
[   24.449255] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.837350] [drm] Initialized drm 1.1.0 20060810
[   24.872054] pci 0000:00:02.0: power state changed by ACPI to D0
[   24.872066] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.872071] pci 0000:00:02.0: setting latency timer to 64
[   24.872300] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   24.875900] [drm:i915_setparam] *ERROR* unknown parameter 4
[   24.875936] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   26.507527] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   42.466236] CPU0 attaching NULL sched-domain.
[   42.466350] CPU0 attaching NULL sched-domain.
[  105.809258] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 0 failed (00010003)
[  105.809265] ndiswrapper (add_wep_key:835): encryption couldn't be enabled (FFFFFFA1)
```
ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:0c:7c:ba  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:90000000-90010000 
```
The other commands didn't give any output (well the first one told me no process was killed). Thanks again!

---

### Post by pytheas22 on 2009-06-27
Ah, I think these lines from dmesg represent the culprit:
```

[  105.809258] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 0 failed (00010003)
[  105.809265] ndiswrapper (add_wep_key:835): encryption couldn't be enabled (FFFFFFA1)
```

Apparently the driver isn't wanting to handle WEP properly (it would probably work if you disabled security).

Unfortunately, I'm not sure why encryption doesn't want to work, but it may help to install a different version of the Windows driver into ndiswrapper.  To do that, run these commands:
```

sudo ndiswrapper -r wlannic
wget http://www.sitecom.com/showdownload.php?id=1133
unzip showdownload*
sudo ndiswrapper -i Driver/Win98SE/wlannic.inf
echo ndiswrapper | sudo tee -a /etc/modules
```

After this is done, reboot and see if things work better.

This will install the Windows 98 version of the driver, rather than the XP one.  I recall reading somewhere the other day (can't find the page now) that someone mentioned the Windows 98 driver in particular working for this device.

---

### Post by RubenK on 2009-06-27
Nope same error... (same hang in sudo dhclient wlan0 & in the dmesg)

---

### Post by pytheas22 on 2009-06-27
hmmm.  Could you please try disabling security on your router, just to see if you can connect then (just try connecting using wicd, not the command line)?  It would be good to know for sure that it actually can connect, and that just the WEP is the issue.

Once we know that, we can figure out where to go next.

---

### Post by RubenK on 2009-06-29
My dad decided to give up and buy a new pc...with windows... I'm pretty sure that it would have worked without the WEP enscryption. I've read other people with other cards having the same problem with WEP. But I doubt he will be getting back to Linux, so... :(

---

### Post by pytheas22 on 2009-06-29
Ah, sorry to hear that.  Did you buy this computer with Linux preinstalled?  Or was it an old machine that you installed Linux on yourself?

Wireless on Linux is usually not this complicated these days (it was a few years ago); a good number of devices will work "out of the box" in Ubuntu, which is better than Windows.  But with old PCMCIA cards like yours, it can be trickier.  You were one of the unlucky ones...

Also keep in mind that you can install Linux and Windows on the same computer at the same time--if you use [wubi]("http://wubi-installer.org"), you can add Ubuntu to your computer just like you would install any other application in Windows.  If you ever want to give Ubuntu another try, this is an easy way to do it, and I'm happy to help you figure out the sitecom card if you go at it again.

---

### Post by RubenK on 2009-06-30
It was an old windows laptop my dad bought like 4-5 years ago. My dad had problems using Window$ so he asked me to install Linux on it, since I've been using it for 1.5 years now and never had any problems with it that wer not due to my own actions. He now has a new laptop with vista (and no downgrade to xp option...) so I wished him all the best. He's now installing tons of drivers, anti virus software and lots of other stuff. Ah well, not my problem... :o

---

