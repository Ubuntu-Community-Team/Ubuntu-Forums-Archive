---
title: "WMP54Gv4.1 Linksys Not working (Fresh Ubuntu Install)"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by Stephen304 on 2011-06-07
I have this wireless card installed with 10.04 LTS server
[http://i290.photobucket.com/albums/ll257/bond304/IMG_2245.jpg](http://i290.photobucket.com/albums/ll257/bond304/IMG_2245.jpg)

I installed Ubuntu using ethernet, but I have had to move my router for my tv.

Wireless-tools are installed, the wireless interface is named wlan0, and I tried nearly everything in this guide:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

I'm not sure what to do. I really want to have wireless working so my Minecraft server will be able to run in my closet while I'm away for several weeks.

Following the guide:
sudo apt-get install wireless-tools
[INDENT]Already installed[/INDENT]
lspci | grep Network
[INDENT]02:08.0 [COLOR="Red"]Network[/COLOR] controller: RaLink RT2561/RT61 802.11g PCI[/INDENT]
iwconfig
[INDENT]lo [INDENT]no wireless extensions.[/INDENT]
eth0 [INDENT]no wireless extensions.[/INDENT]
wlan 0 [INDENT]IEEE 802.11bg ESSID:off/any[/INDENT]
[INDENT]Mode:Managed Access Point:Not Associated Tx-Power=0 dBm[/INDENT]
[INDENT]Retry long limit:7 RTS thr:off Fragment thr:off[/INDENT][INDENT]Power Managment:off[/INDENT][/INDENT]

Down in the next section: using the command line:
ip link set [INDENT]Not enough information: "dev" argument is required.[/INDENT]
sudo ifdown eth0 [INDENT]ifdown: interface eth0 not configured[/INDENT]
sudo ifup wlan0 [INDENT]ignoring unknown interface wlan0=wlan0.[/INDENT]
iwconfig wlan0 mode managed
[INDENT]SET failed on device wlan0 ; operation not permitted.[/INDENT]
iwconfig wlan0 channel 11
[INDENT]SET failed on device wlan0 ; operation not permitted.[/INDENT]
iwconfig wlan0 essid networkname
[INDENT]SET failed on device wlan0 ; operation not permitted.[/INDENT]

If I try adding sudo to these last 3 it doesn't say anything at all.

Any help would be greatly appreciated!

EDIT: Also, "ip addr" gives this output: (minus the first 2 interfaces)
[INDENT]3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisk noopstate DOWN qlen 1000
link/ether 00:10:39:14:4a:c0 brd ff:ff:ff:ff:ff:ff[/INDENT]
The "DOWN" part might indicate a problem with enabling the card, but idk where to start to fix it.

---

