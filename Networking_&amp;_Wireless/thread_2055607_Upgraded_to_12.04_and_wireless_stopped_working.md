---
title: "Upgraded to 12.04 and wireless stopped working"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by p1s1thack on 2012-09-09
Hey, 
I have tried to follow directions on other threads but still can't mange to get anywhere.
Very very new and unfamiliar with Linux so please bear with me. Here is code when I do lusb: Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 005: ID 0bc2:2300 Seagate RSS LLC 
guitar1@guitar1-PS519AA-ABA-A805N:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2070L]
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 005: ID 0bc2:2300 Seagate RSS LLC 

Here is what I get after lspci -nnk | grep -iA2
 net02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2a0b]
    Kernel driver in use: 8139too

Here is other dmesg | grep -e wlan -e 813
[    0.090917] pci 0000:02:02.0: [10ec:8139] type 0 class 0x000200
[    1.292944] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.292975] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.293623] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.293677] 8139too 0000:02:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.294873] 8139too 0000:02:02.0: eth0: RealTek RTL8139 at 0xe800, 00:11:d8:38:d1:44, IRQ 21
[   14.538892] 8139too 0000:02:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   15.867861] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.876167] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19842.353011] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19842.353816] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Thanks for any help!

---

### Post by p1s1thack on 2012-09-10
Anyone?

---

### Post by chili555 on 2012-09-10
It looks like the ethernet is connected and working. Network Manager is designed to disallow wireless if wired, usually faster and more secure, is available. Please detach the ethernet, reboot so we have a clean slate and then run:```
dmesg | grep -i rt2 > info.txt
dmesg | grep wlan >> info.txt
```Now you can attach the ethernet, connect, find the file info.txt in your user directory and copy and paste it in your reply.

---

### Post by p1s1thack on 2012-09-10
Thank you for your help! Here is the output:
[   15.377606] Registered led device: rt2800usb-phy0::radio
[   15.377676] Registered led device: rt2800usb-phy0::assoc
[   15.380253] Registered led device: rt2800usb-phy0::quality
[   15.380346] usbcore: registered new interface driver rt2800usb
[   16.028974] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.029385] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by chili555 on 2012-09-10
Nothing alarming there. What are its symptoms? Does it see networks?```
sudo iwlist wlan0 scan
rfkill list all
```Can you click on a network and try to connect? Are you asked for the WPA key?

---

### Post by p1s1thack on 2012-09-10
Yes, it asks for  key and connects then disconnects after 10 seconds.
Here is first command 
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:90:F9:BC:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"SV4N3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001af2ef0d181
                    Extra: Last beacon: 452ms ago
                    IE: Unknown: 00055356344E33
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000


Here is 
rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



Thanks!

---

### Post by chili555 on 2012-09-10
Please try a temporary driver parameter:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb nohwcrypt=1
```What firmware are you using now?```
md5sum /lib/firmware/rt2870.bin
```For reference, mine is:> $ md5sum /lib/firmware/rt2870.bin
[COLOR="Red"]36c944c3138125605d28c0a3a1338be9[/COLOR]  /lib/firmware/rt2870.binI have another version or two laying around here.

---

### Post by p1s1thack on 2012-09-10
Tried those first codes and computer got stuck, unable to move mouse or type.

Firmware is 
36c944c3138125605d28c0a3a1338be9  /lib/firmware/rt2870.bin

---

### Post by chili555 on 2012-09-10
> computer got stuck, unable to move mouse or type.That's completely unexpected. You might check for clues as to why in:```
sudo cat /var/log/syslog | grep rt2
```Look at the timestamp and try to see what happened just before it froze.

Weird.

---

### Post by p1s1thack on 2012-09-10
Yeah, this is getting really frustrating, thanks again for the help. I have no idea what is going on. Here is the log

device: rt2800usb-phy0::radio
Sep 10 09:38:29 guitar1-PS519AA-ABA-A805N kernel: [   15.377676] Registered led device: rt2800usb-phy0::assoc
Sep 10 09:38:29 guitar1-PS519AA-ABA-A805N kernel: [   15.380253] Registered led device: rt2800usb-phy0::quality
Sep 10 09:38:29 guitar1-PS519AA-ABA-A805N kernel: [   15.380346] usbcore: registered new interface driver rt2800usb
Sep 10 09:38:30 guitar1-PS519AA-ABA-A805N NetworkManager[815]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 3)
Sep 10 12:28:03 guitar1-PS519AA-ABA-A805N kernel: [   19.919934] Registered led device: rt2800usb-phy0::radio
Sep 10 12:28:03 guitar1-PS519AA-ABA-A805N kernel: [   19.920222] Registered led device: rt2800usb-phy0::assoc
Sep 10 12:28:03 guitar1-PS519AA-ABA-A805N kernel: [   19.920302] Registered led device: rt2800usb-phy0::quality
Sep 10 12:28:03 guitar1-PS519AA-ABA-A805N kernel: [   19.920377] usbcore: registered new interface driver rt2800usb
Sep 10 12:28:03 guitar1-PS519AA-ABA-A805N NetworkManager[879]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 3)
Sep 10 12:33:09 guitar1-PS519AA-ABA-A805N kernel: [   19.187914] Registered led device: rt2800usb-phy0::radio
Sep 10 12:33:09 guitar1-PS519AA-ABA-A805N kernel: [   19.187950] Registered led device: rt2800usb-phy0::assoc
Sep 10 12:33:09 guitar1-PS519AA-ABA-A805N kernel: [   19.187984] Registered led device: rt2800usb-phy0::quality
Sep 10 12:33:09 guitar1-PS519AA-ABA-A805N kernel: [   19.190172] usbcore: registered new interface driver rt2800usb
Sep 10 12:33:09 guitar1-PS519AA-ABA-A805N NetworkManager[871]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 3)
Sep 10 15:06:55 guitar1-PS519AA-ABA-A805N kernel: [   15.171584] Registered led device: rt2800usb-phy0::radio
Sep 10 15:06:55 guitar1-PS519AA-ABA-A805N kernel: [   15.171858] Registered led device: rt2800usb-phy0::assoc
Sep 10 15:06:55 guitar1-PS519AA-ABA-A805N kernel: [   15.173130] Registered led device: rt2800usb-phy0::quality
Sep 10 15:06:55 guitar1-PS519AA-ABA-A805N kernel: [   15.173313] usbcore: registered new interface driver rt2800usb
Sep 10 15:06:55 guitar1-PS519AA-ABA-A805N NetworkManager[865]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 3)

---

### Post by chili555 on 2012-09-10
There is no evidence whatever that rt2800usb had anything to do with the freeze. You could try the commands again or we could load the parameter in a conf file that loads as you boot. Which do you prefer?

---

### Post by p1s1thack on 2012-09-10
I tried again and froze immediately, maybe this computer is not worth reviving!

Or I could go back to Ocelot?? Thanks again! 
I could try conf file to give it one more shot.

---

### Post by chili555 on 2012-09-10
Please do:```
sudo gedit /etc/modprobe.d/rt2800usb.conf
```Add one line:```
options rt2800usb nohwcrypt=[COLOR="Red"]Y[/COLOR]
```Oops, I might have made a mistake!

Proofread better than I did, save and close gedit.

Reboot. Any improvements?

---

### Post by p1s1thack on 2012-09-10
Unfortunately, the problem is still there.

---

### Post by chili555 on 2012-09-11
> **p1s1thack said:**
> Unfortunately, the problem is still there.The problem...does the computer freeze or does the wireless not connect? Or does it connect and then drop?

Did you put the key in the wireless section of Network Manager or is it asking for the key for you to enter each time? Can you double-check the key?

---

### Post by p1s1thack on 2012-09-11
It is working! thank you so much for all your help!

I had tried both in pop up window and in network manager but when I looked at network manager a little closer it had "Auto SV4N3" and was unable to save setting in that window!?! 
So I deleted connection, unplugged usb adapter and plugged back in, in network manger, connection came up as just "SV4N3." I inputted key again and was able to save  and it started working. Rebooted and it is still working!

Thank you so much for all the help Chili555!!!!!

---

### Post by chili555 on 2012-09-11
Awesome! Glad it's working. Have fun!

---

