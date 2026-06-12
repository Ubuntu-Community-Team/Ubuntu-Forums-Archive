---
title: "Intrepid TP-Link WN821N on an old laptop"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Jimmy9pints on 2009-01-27
This is a problem I come back to once every couple of weeks to try to solve. As yet I have had no luck. So I just put up with no wireless :(

I have an old laptop (Lenevo Sunrise 410L) with no built in wireless capability. You may not have heard of it as it was made and bought in China.

Here in China there is basically not a lot of choice when it comes to wireless cards. The choice boils down to TP-Link or D-Link usually. 

I ended up with a TP-Link TL-WN821N, it's a USB dongle. lsusb gives:
```
Bus 001 Device 002: ID 0cf3:9170 Atheros Communications, Inc. 

```
For this device. 

I checked on the supported [wireless cards wiki]("http://https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") (amongst other places) and couldn't find anything about my usb wireless card being supported. 

So I have gone down the ndiswrapper road. I set it up as per the usual instructions apart from I found that the XP drivers didn't work. All choices except the Vista drivers came up "invalid driver". So i went with the X86 Vista drivers. 

It didn't work still, so I started working through pytheas22's very wonderful and user-friendly C[omprehensive ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847") (thanks to him for that!!). Anyway, I won't run you through everything that happened there, but I complete steps 1&2 and then 3 gives me a problem. 

When I run ```
lshw -C Network
``` I get ```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 02
       serial: 00:16:36:ce:f3:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.100 latency=32 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:db:ab:fd:ec:ab
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
There seems to be no mention of my USB dongle here. According to the trouble shooting guide I have two options, but neither apply to my situation. 

Can somebody please help out at this point? I would LOVE to get this solved.

---

### Post by Jimmy9pints on 2009-02-03
Nobody have any idea? Need some more information perhaps? Please ask.

---

### Post by NeverM$4Me on 2009-02-05
Have you tried this?

[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

---

### Post by pinklerose on 2009-02-10
Jimmy9pints did you successfuly run this card on Ubuntu without ndiswrapper?

---

### Post by Jimmy9pints on 2009-02-13
Sorry for taking a long time to reply. I didn't see any replies for a while and kind of gave up. I'll try madwifi again.

---

### Post by excogitation on 2009-04-09
[Apparently]("http://marc.info/?l=linux-wireless&m=122464107408916&w=2") one could make it work.

If I can get it to work I'll let you know.

edit:

Ok so I don't have enough knowledge to get it to work.
[otus driver]("http://wireless.kernel.org/en/users/Drivers/otus") <- if anybody gets it to work ... please write a howto.
[ar9170 driver based on otus]("http://wireless.kernel.org/en/users/Drivers/ar9170")

[Howto for OpenSuse 10.3/11.0]("http://www.pc-forum24.de/suse-treiber/10256-atheros-veroeffentlicht-linuxtreiber-fuer-usb-draft-n-sticks-rpms-zum-test-inside.html") (german)

---

### Post by Jimmy9pints on 2009-04-09
That'd be amazing if someone could help out on that.

---

### Post by excogitation on 2009-04-14
I could only get it to work with non-encrypted networks - but it's a start. An os driver would be better though.

> **rogues29 said:**
> 
[...]
Anyway, I just figured out a way to get the adapter to work.

[...]

Firstly you need to use **ndiswrapper** [...]

```
sudo apt-get install ndisgtk
```

once that is installed it should put a link in **System->Administration** called **Windows Wireless Drivers**

What that program requires is the windows drivers for the device. unfortunately the drivers for the TP-Link device don't work in ndiswrapper, at least all the ones i could find from TP-Link. There are a few other Wireless USB dongles that come with the same chip set, and it is one of these that i got to work 10 minutes ago. The drivers you need to download are for a IOGear device and are available at **[GWU623.zip]("http://www.iogear.com/support/driver/GWU623.zip")** [...]

the only things you need are the files in **GWU623.zip/drivers/XP** and then whichever architecture you are running i can only verify that the 32-bit ones worked because i don't have 64-bit. so extract the 3 files in either of those directories all to the same directory (i don't think it matters where).

Then go into the **Windows Wireless Drivers** app and click **Install New Driver** find the folder you extracted the files to and select the file ending in **.inf** click **Install** and that should be it. Wait a couple of seconds to let the device start up and then Left click the network icon in the system tray to connect to wireless networks in range.



---

### Post by excogitation on 2009-04-19
```
[ 6560.088150] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 6560.269289] usb 1-2: configuration #1 chosen from 1 choice
[ 6560.858177] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[ 6561.157861] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 6561.407830] ndiswrapper: driver arusb_xp (,02/04/2008,3.0.0.99) loaded
[ 6561.849098] wlan1: ethernet device 00:21:27:cf:05:21 using NDIS driver: arusb_xp, version: 0x40700, NDIS version: 0x501, vendor: 'Atheros OTUS Wireless Network Adapter', 0CF3:9170.F.conf
[ 6561.849351] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 6561.849441] usbcore: registered new interface driver ndiswrapper
[ 6565.915061] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6571.443584] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 6581.708040] wlan1: no IPv6 routers present

```

@pytheas22: is this "wlan1: no IPv6 routers present" hinting to a problem with ipv6? (I only use ipv4 with my router, afaict).

---

### Post by pytheas22 on 2009-04-19
> @pytheas22: is this "wlan1: no IPv6 routers present" hinting to a problem with ipv6? (I only use ipv4 with my router, afaict).

No, don't worry about this; dmesg always says stuff about ipv6 routers not being present, unless you're one of the (seemingly) three people in the world who actually owns an ipv6 router :)

If you want to try to connect from the command line, the first step is to edit your /etc/wpa_supplicant.conf file.  You can open it by typing:
```

sudo gedit /etc/wpa_supplicant.conf
```

Erase whatever's in it now (if anything), and add this:

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="myhomenetwork"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="**ASCII PSK Password in Quotes**"
        pairwise=TKIP
        group=TKIP
}
```

Then save and close the file.

To connect, run these commands:
```

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
iwconfig
sudo dhclient wlan0
```

Don't be surprised if it doesn't work on the first try.  Please post all your output so we can try to figure out what went wrong.  Usually you have to play around with the wpa_supplicant.conf file for a while before you hit the right settings.

By the way, this is based on [kevdog's guide to command-line wireless]("http://ubuntuforums.org/showthread.php?t=571188").

---

### Post by Ozzy0sbourne on 2009-04-19
> **Jimmy9pints said:**
> This is a problem I come back to once every couple of weeks to try to solve. As yet I have had no luck. So I just put up with no wireless :(

I have an old laptop (Lenevo Sunrise 410L) with no built in wireless capability. You may not have heard of it as it was made and bought in China.

Here in China there is basically not a lot of choice when it comes to wireless cards. The choice boils down to TP-Link or D-Link usually. 

I ended up with a TP-Link TL-WN821N, it's a USB dongle. lsusb gives:
```
Bus 001 Device 002: ID 0cf3:9170 Atheros Communications, Inc. 

```
For this device. 

I checked on the supported [wireless cards wiki]("http://https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") (amongst other places) and couldn't find anything about my usb wireless card being supported. 

So I have gone down the ndiswrapper road. I set it up as per the usual instructions apart from I found that the XP drivers didn't work. All choices except the Vista drivers came up "invalid driver". So i went with the X86 Vista drivers. 

It didn't work still, so I started working through pytheas22's very wonderful and user-friendly C[omprehensive ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847") (thanks to him for that!!). Anyway, I won't run you through everything that happened there, but I complete steps 1&2 and then 3 gives me a problem. 

When I run ```
lshw -C Network
``` I get ```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 02
       serial: 00:16:36:ce:f3:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.100 latency=32 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:db:ab:fd:ec:ab
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
There seems to be no mention of my USB dongle here. According to the trouble shooting guide I have two options, but neither apply to my situation. 

Can somebody please help out at this point? I would LOVE to get this solved.


[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html](http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html)

---

### Post by excogitation on 2009-04-20
dmesg
```
[ 2042.917948] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 2043.145594] usb 1-2: configuration #1 chosen from 1 choice
[ 2043.206702] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[ 2043.408030] usb 1-2: reset high speed USB device using ehci_hcd and address 3
[ 2043.610666] ndiswrapper: driver arusb_xp (,02/04/2008,3.0.0.99) loaded
[ 2043.946441] wlan0: ethernet device 00:21:27:cf:05:21 using NDIS driver: arusb_xp, version: 0x40700, NDIS version: 0x501, vendor: 'Atheros OTUS Wireless Network Adapter', 0CF3:9170.F.conf
[ 2043.946599] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 2043.947319] usbcore: registered new interface driver ndiswrapper
[ 2044.008985] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[ 2044.009229] udev: renamed network interface wlan0 to wlan1
[ 2047.904362] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2053.124437] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2063.644010] wlan1: no IPv6 routers present

```

iwconfig
```
wlan1     IEEE 802.11g  ESSID:"exco"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1D:19:D8:4D:37   
          Bit Rate=300 Mb/s   Tx-Power:27 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:9562-A39E-CED3-D484-E927-A3C1-6D66-508E   Security mode:restricted
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scan
```
wlan1     Scan completed :
          Cell 01 - Address: 00:1D:19:D8:4D:37
                    ESSID:"exco"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

```

cat /etc/wpa_supplicant.conf
```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="exco"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="myultrastrongtestpassword"
        pairwise=TKIP
        group=TKIP
}

#network={
#        ssid="exco"
#        proto=RSN
#        key_mgmt=WPA-PSK
#        psk="myultrastrongtestpassword"
#        pairwise=CCMP
#}

```
sudo wpa_supplicant -Dwext -iwlan1 -c/etc/wpa_supplicant.conf -dd
```
[see pastebin]("http://pastebin.com/m7cb11311")
```


sudo dhclient wlan1
```

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:21:27:cf:05:21
Sending on   LPF/wlan1/00:21:27:cf:05:21
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11


```

---

### Post by pytheas22 on 2009-04-20
wpa_supplicant seems to associate with your router alright, but then it fails to authenticate.  I'm not sure why, but I think it might help if you tell it which AP to connect to.  Try changing the wpa_supplicant.conf file to:
```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="exco"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="myultrastrongtestpassword"
        pairwise=TKIP
        group=TKIP
        **bssid=00:1D:19:D8:4D:37**
}
```

It may also help if change the first line to read 'ap_scan=0'.  Please experiment with these settings and post the output (you should still use the same command as before to connect: 'sudo wpa_supplicant -Dwext -iwlan1 -c/etc/wpa_supplicant.conf -dd').

---

### Post by excogitation on 2009-04-22
I got it to work twice today with only WPA2 - can't replicate it atm.

I think it might have sth. to do with the state of "Hardware Drivers" -> "Atheros 802.11n Wireless LAN adapter".

When it worked - it did directly with network-manager.

I'll report back if I find out what does make it work.

---

### Post by pytheas22 on 2009-04-22
> I think it might have sth. to do with the state of "Hardware Drivers" -> "Atheros 802.11n Wireless LAN adapter".

Interesting...I wonder if switching between ndiswrapper and ath9k is what makes it work.  The next time you get it to work, please post the output of:
```

lshw -C Network
```

so we can see which module is driving it.

Also, if you want to enable ath9k manually, type:

```
sudo rmmod ndiswrapper
sudo rmmod ath9k
sudo modprobe ath9k
```

This is basically what the "Hardware Drivers" utility does when you enable "Atheros 802.11n Wireless LAN" support.

To switch back to ndiswrapper:
```

sudo rmmod ath9k
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

---

### Post by excogitation on 2009-04-22
Ok so here is how it ""works""

sudo wpa_supplicant -Dwext -iwlan3 -c/etc/wpa_supplicant.conf -dd
with:
```
network={
	ssid="exco"
	psk="myultrastrongtestpassword"
	key_mgmt=WPA-PSK
	proto=RSN
	pairwise=CCMP
	bssid=00:1D:19:D8:4D:37
}

```

then I need to click on the network in network-manager and it connects (not too stable)

lshw -C Network
```
*-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan3
       serial: 00:21:27:cf:05:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+arusb_xp driverversion=1.54+,02/04/2008,3.0.0.99 ip=192.168.3.105 multicast=yes wireless=IEEE 802.11g

```
iwconfig
```

wlan3     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:35 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

With wpa only I couldn't get it to work (haven't tried wpa&wpa2).

From what I read the ath9k driver doesn't support usb
so the interesting module for the TL-WN821N is arusb_lnx I think.

---

### Post by pytheas22 on 2009-04-22
> then I need to click on the network in network-manager and it connects (not too stable)

What do you mean when you say not too stable?  Does the connection drop, is it slow, or is it just unpredictable whether it will connect or not?
> 
From what I read the ath9k driver doesn't support usb
so the interesting module for the TL-WN821N is arusb_lnx I think. 

Yes, that's right--I forgot your card was USB.

---

### Post by excogitation on 2009-04-23
> **pytheas22 said:**
> What do you mean when you say not too stable?  Does the connection drop, is it slow, or is it just unpredictable whether it will connect or not?



It doesn't connect every time and the connection just drops after about 30s - [pastebin]("http://pastebin.com/m422f66b0")

---

### Post by pytheas22 on 2009-04-24
Unfortunately, I don't see anything in your wpa_supplicant output that looks like it explains why the connection drops.  The only thing I can conclude is that it's some kind of problem with the driver.  So I'm not really sure I have any more advice than to keep on recompiling the otus driver...

I wish I had a better answer, but I'm at a loss at this point.

---

### Post by flash63 on 2009-05-07
Hello,
i build a Package based on Compat-Wireless-230209 for this Chipset (Atheros Otus AR9170). Needed Firmware is included.
[http://www.linuxwireless.org/](http://www.linuxwireless.org/)

For Instructions follow this Link:
[http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

Supported Chipset-ID's:

0cf3:9170
0cf3:1001
0cf3:1002
07d1:3c10
0846:9010
0846:9001
0ace:1221
0cde:0023
0cde:0026
083a:f522
2019:5304
04bb:093f
0586:3417

Enjoy!

---

### Post by excogitation on 2009-05-07
> **flash63 said:**
> Hello,
i build a Package based on Compat-Wireless-230209 for this Chipset (Atheros Otus AR9170). Needed Firmware is included.
[http://www.linuxwireless.org/](http://www.linuxwireless.org/)

For Instructions follow this Link:
[http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

Enjoy!

I can confirm it's working on Jaunty. (you beat me to it providing these instructions - I stumbled on your post yesterday but only rebooted today ;-) )

---

### Post by flash63 on 2009-05-07
> can confirm it's working on Jaunty.
Nice :-) - and thank's for testing.

Good news from the git:
[http://git.kernel.org/?p=linux/kernel/git/jberg/ar9170.git;a=blob;f=README;h=3edc5a36d1f7d7a1e6ded30d40dd8193a507fca8;hb=1ac1aa6826ae02e4c1a466b7c15871204f61cc14](http://git.kernel.org/?p=linux/kernel/git/jberg/ar9170.git;a=blob;f=README;h=3edc5a36d1f7d7a1e6ded30d40dd8193a507fca8;hb=1ac1aa6826ae02e4c1a466b7c15871204f61cc14)

---

### Post by excogitation on 2009-05-07
> **flash63 said:**
> Nice :-) - and thank's for testing.

Good news from the git:
[http://git.kernel.org/?p=linux/kernel/git/jberg/ar9170.git;a=blob;f=README;h=3edc5a36d1f7d7a1e6ded30d40dd8193a507fca8;hb=1ac1aa6826ae02e4c1a466b7c15871204f61cc14](http://git.kernel.org/?p=linux/kernel/git/jberg/ar9170.git;a=blob;f=README;h=3edc5a36d1f7d7a1e6ded30d40dd8193a507fca8;hb=1ac1aa6826ae02e4c1a466b7c15871204f61cc14)

Thanks you, for providing the instructions ;-)

Do you now when it will hit mainline? (~2.6.31?)

---

### Post by flash63 on 2009-05-08
> Do you now when it will hit mainline? (~2.6.31?)
I have no more informations.

---

### Post by excogitation on 2009-05-10
Can you confirm that this driver breaks regular shutdown?

---

### Post by flash63 on 2009-05-11
> Can you confirm that this driver breaks regular shutdown?
No, i think it's a problem with the Network-Manager. Try Wicd V1.5.9-2 with ubuntu 9.04.
[http://nl.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb)

First download the deb-pakage, remove the NM and install Wicd. Reboot your System. Use driver **wext** for wpa_supplicant. 

Homepage [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by aloa on 2009-06-11
yes i can confirm that this driver breaks regular shutdown..
i test it on 9.04 server 2.6.28

---

