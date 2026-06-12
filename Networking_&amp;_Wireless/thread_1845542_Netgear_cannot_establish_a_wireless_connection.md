---
title: "Netgear cannot establish a wireless connection"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by Grisogonus on 2011-09-17
Cheers,

I am a new user of ubuntu, few days ago I have installed the latest version (1104 I think), on a second sata disc on my system (the first one contains functioning Win XP).

The installation went fine, and os itself works flawlessly, however it cannot establish a connection to the internet. I am using **netgear wireless usb wg111v3**, which works well with windows on my other disc. Ubuntu reads the connection, but keeps prompting for the password, failing to connect. When I create a new network (I tried different encryptions), I get the same result: unable to connect. I do get a connection with ad-hoc method, but it's non-existant (says speed unknown) and firefox can't load homepage, so I would guess it's not really connected.

Lsusb identifies netgear, so I assume drivers are not a problem. I have read the net through and through, but netgear mostly has problems with drivers. I have found solutions with ndiswrapper, but that is mostly for older versions of ubuntu. Besides, my system reads netgear, so it's not that.

I have read that people with linux mint have better experiences with netgear, so I burnt iso and booted from disc. The same result.

Take note though, I am a complete noob in linux, and have a very limited knowledge of windows, is there something I do not see?

Any help is welcome, since I seem to have hit a dead end.

---

### Post by walt.smith1960 on 2011-09-17
You do not want to use Ad Hoc if you're connecting via a wireless router, you want to use infrastructure mode.  What does Network Manager show? The "lsusb" command would show the device information even if drivers required by the device are missing or improperly configured. Your Netgear appears to use a RealTek 8187B chip.  I have a Trendnet device using the same chipset and it has been plug & play on every Ubuntu distro I've tried. 

You could open a  terminal, type "lsmod" and make sure "rtl8187" is present. That is the "driver" or module that drives the 8187B chipset.  You do need to select the proper encryption;  you cannot mix & match.  Using the improper encryption would certain cause "cannot connect" messages.  If you're not sure which to use, you could look at your functional Windows connection information.

---

### Post by bkratz on 2011-09-17
Also, you may want to make sure the router or AP is not using the mixed mode (wpa and also wpa2) of transmission. Ubuntu (with some wifi cards) sometimes has problems with that mode. Please select either but not both modes.

---

### Post by Grisogonus on 2011-09-17
> **bkratz said:**
> Also, you may want to make sure the router or AP is not using the mixed mode (wpa and also wpa2) of transmission. Ubuntu (with some wifi cards) sometimes has problems with that mode. Please select either but not both modes.


These are specs of wap in question:

Wireless Access Point - Zadar

Configuration
 
[IMG]http://192.168.1.1/images/spacer.gif[/IMG]Interface Enabled:Yes
Physical Address:00:1D:68D:3B:AC
Network Name (SSID):Zadar
Interface Type:802.11b/g
Actual Speed:54 Mbps
Channel Selection:Auto
Region:Europe
Channel:11
Allow multicast from Broadband Network:Yes
WMM:enabled   

Security
 Broadcast Network Name:Yes
Allow New Devices:New stations are allowed (automatically)
Security Mode:WPA-PSK
WPA-PSK Preshared Key:abcd8765
WPA-PSK Encryption:AES
WPA-PSK Version:WPA2


Maybe I can change it to wep and then create a new connection on ubuntu. Will try that and report back.

---

### Post by wildmanne39 on 2011-09-17
Hi, it would be best to set it to wpa2 and also make sure the speed is set to b,g,n, not just n speed.

Please pose the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Grisogonus on 2011-09-17
[SIZE=2]
I set it to wep encryption and did the same thing in router as bkratz and walt.smith1960 suggested, it works like a charm. Had some naggings while I did the same thing on winxp, but it's done and now both systems have internet connection at full speed. Thank you guys, I lost quite a time searching the intenet with no results before I asked for help here.

@wildmanne39 - I do not know why wpa2 did not work, but I will not insist on it, first I have an ubuntu to explore lol, very friendly community

cheers
[/SIZE]

---

### Post by bkratz on 2011-09-17
Glad to hear you found something that works for you. As wildmanne says, the next step would be to get WPA2 working since wep is not very secure.

---

