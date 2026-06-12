---
title: "ubuntu 8.04 (dell inspiron) cannot connect"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by sebastian.dennen on 2009-06-07
New computer has a Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01), and connects using Network manager that came with Ubuntu 8.04. 

At first, NM quickly detected my netgear router but was not able to connect (kept prompting for WEP key over and over)

Now, NM doesn't detect anything, it just says 'device is unmanaged'

when I do 'iwlist scan' in the terminal it says that it detects my router under 'eth1':
 Cell 01 - Address: 00:1E:2A:79:D5:C2
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-42 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

SO, i know that my broadcom card is detecting the wiresless signal, but using commands

sudo iwconfig essid NETGEAR
sudo iwconfig ap 00:1E:2A:79:D5:C2
sudo dhclient eth1

does not work, it basically says no dhcp offers received essentially.

PLEASE HELP - i am new to linux but i feel like I've been trying the right things. 

i'm pretty sure i have the right drivers installed. when i first got the computer it would detect my router with the drop-down applet thingy (Network Manager) but failed to connect (after prompting me for the wpa key about 5 times). then i restarted, and the next day, this issue had taken its place. 


thank you very much

---

