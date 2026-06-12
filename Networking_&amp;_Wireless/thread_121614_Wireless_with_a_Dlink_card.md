---
title: "Wireless with a Dlink card"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by PauloStar on 2006-01-25
Hello I'm new here so if I'm talking rubbish don't flame me! :) 

Anyway, I installed Breezy on my laptop yesterday, everything works great apart from my wireless (currently using an ethernet cable). It's a DLink DWL-G650+ (note the +), I installed Ndiswrapper and it detects the card and installs the driver. I scanned with WiFi-Radar which finds my network (I've turned WPA off until I get this working) but when I click connect it just hangs on Please Wait. If I set it up in Ubuntu's Network Tools it just does nothing at all. How can I get this working coz I don't want to have to go back to Windows!!

Please help a semi-noobie!
Thanks! :smile:

---

### Post by FLeiXiuS on 2006-01-25
Have you checked to see if your NIC is affiliating it's self with the correct SSID.  

$ sudo iwconfig

This will give the output of wireless devices installed on your PC.

If you do see that your network is configured to the appropiate SSID check to see if your getting an IP address.  Take note of the device name, I will assume you know the device name.  Let DEV equal your devices name for the following commands. 

$ sudo ifconfig DEV

If an IP address is located, awesome you have connectivity.  Try pinging google and some others before you go ahead and configure your WPA keys.  Now if you don't have an IP address, find out why.  Perhaps your WAP (Wireless Access Point) has MAC filtering enabled?  Neverless try probing for a DHCP lease.  

$ sudo pump -i DEV

This should give us a slight bit of clue of where the problem is occuring.

---

### Post by PauloStar on 2006-01-25
"$sudo iwconfig wlan0" gives

> 
paul@ANGEL:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"PRIVITENETWORK"
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr=4096 B   Fragment thr=4096 B
          Encryption key:off
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


How do I set the ESSID?

btw My network uses static IPs not DHCP.

---

### Post by PauloStar on 2006-01-25
UPDATE: I entered "sudo iwconfig wlan0 essid PRIVATENETWORK" and connected thorugh wifi-radar and now it works! Still doesn't through Network Tools though. How do I set my WPA key?

---

### Post by FLeiXiuS on 2006-01-25
You will need to take a look at wpa_supplicant which is available in the repo's.  Search the forums for more answers, there's tons of links on how to enable WPA.

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

---

### Post by PauloStar on 2006-01-26
All working now with glorious WPA encryption! Thanks!! :p

---

