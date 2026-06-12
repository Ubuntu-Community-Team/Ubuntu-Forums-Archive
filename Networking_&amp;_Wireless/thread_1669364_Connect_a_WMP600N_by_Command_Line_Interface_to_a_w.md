---
title: "Connect a WMP600N by Command Line Interface to a wireless network"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by gunnarflax on 2011-01-17
Hi again! Still having trouble with my HTPC project :) I'm trying to get the wireless network to connect to my router but it simply won't work. I will share the steps I've taken so far.

Some info about my system:
[LIST]
[*]I'm running XBMC Live and this is why I must do this by the command line.
[*]The network has a WPA-Personal encryption.
[*]Wireless channel = 1
[*]Wireless mode = managed
[*]Wireless network card = WMP600N with rt2800 chipset
[/LIST]

First I followed this tutorial:
[http://forum.xbmc.org/showpost.php?p=468527&postcount=7](http://forum.xbmc.org/showpost.php?p=468527&postcount=7)

... But it didn't work and it was also meant for a WEP encryption.

And then I followed this tutorial which even had a special section for ra based chipsets:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

... But when I ran iwpriv I got a message like this:
```
wlan0      no private ioctls.
```

Please help me with how I should do to be able to connect wirelessly to the network!

All help is appreciated!
Thank you!

---

### Post by chili555 on 2011-01-17
I assume we are solving one problem, not three or four. May I assume your wireless driver is working and scans, tries to connect, etc.? If so, and if your wireless interface is wlan0, amend /etc/netwotk/interfaces similar to this:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid myrouter
wpa-psk mysecretkeyI have made some assumptions here; that your WPA network is Pre-shared key, or PSK and that you want a static IP address so you can reach the HTPC by SSH or similar after it's up and running. Be sure to select an address outside the DHCP range used by the router. For example, if your router assigns addresses by DHCP from x.2 to x.51, use a static address above x.51. 

Restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```Check to see if you got the requested address and you are actually connected:```
ifconfig wlan0
ping -c3 192.168.1.1
```If the HTPC will access the internet, fill in /etc/resolv.conf:```
nameserver 192.168.1.1
```In all instances, substitute your details. Post back if you need further guidance.

---

### Post by gunnarflax on 2011-01-17
Thank you for your fast answer but I actually managed to fix the problem just before you I saw your post. I found this thread at the xbmc-forum: [http://forum.xbmc.org/showthread.php?t=81858](http://forum.xbmc.org/showthread.php?t=81858)

... Which describes how you can use wicd-curses to handle wireless connections through a CLI. I found it to be the easiest way. I also managed to get it working by following [XBMCFreaks]("http://www.xbmcfreak.nl/en/wifi-onder-linux-configureren/") guide but I chose to go with wicd-curses since it was much easier to manage.

The only problem I had with wicd-curses was that I got some errors when trying to access it in the terminal the first time. But after restarting the service it worked like a charm:
[HTML]sudo /etc/init.d/wicd restart[/HTML]

Hopefully will your post help someone else with a similar problem! Thank you for taking your time! :)

---

