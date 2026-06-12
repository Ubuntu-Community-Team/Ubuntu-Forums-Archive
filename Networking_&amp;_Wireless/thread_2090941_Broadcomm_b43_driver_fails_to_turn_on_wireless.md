---
title: "Broadcomm b43 driver fails to turn on wireless"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by Jman012 on 2012-12-03
Fairly new install on my Macbookpro 6,2 laptop with Ubuntu 12.10 32bit(idk why I did 32 and not 64). My wireless would randomly drop internet (it would stay connected to my router, but lost internet connectivity). To fix this I tried using the b43 driver (sudo apt-get install firmware-b43-installer b43-fwcutter, and also I tried form the software center). At first I thought it was working from there but I never made sure that the OS used b43 and not brcmsmac.

So I added bcma and brcmsmac to the blacklist (/etc/modprobe.d/blacklist.conf) and adding b43 to /etc/modules. Next I ran 'sudo modprobe -r brcmsmac bcma' which successfully turned off my wireless card. After that 'sudo modprobe b43' failed to turn on my wireless card.

'lspci -vnn -d 14e4:'
Boradcomm Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
Subsystem: Apple Inc. Device [106b:0093]

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) says b43 works for my BCM43224 card as well. I might have messed something up when trying to uninstall and reinstall b43 before trying out the modprobe commands, but I don't know if something like that would be possible or not.

EDIT: And after running 'sudo modprobe b43' it does show up in lsmod.

---

### Post by Jman012 on 2012-12-04
Anyone have any idea at all? I'd rather not have my internet go out randomly during important sessions.

---

### Post by wildmanne39 on 2012-12-04
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Jman012 on 2012-12-04
Here you go. 'netinfo - b43.txt' is with the b43 driver loaded, and 'netinfo - brcmsmac.txt is with the brcmsmac driver loaded. Reading through other articles earlier trying to figure my problem out myself I noticed you always had people do it themselves, but this script is very nice!

Scratch that, problem with attaching the text files, here are the pastebins

b43 loaded - [http://pastebin.com/RibCteL9](http://pastebin.com/RibCteL9)
brcmsmac loaded - [http://pastebin.com/2nQsQF9A](http://pastebin.com/2nQsQF9A)

---

### Post by chili555 on 2012-12-05
The Wild Man will be away for a few days and I've been asked to help. Please temporarily hook up the ethernet and do:```
sudo apt-get install linux-headers-generic bcmwl-kernel-source
```Post back with your report.> this script is very nice!Wild Man worked hard on it and it's excellent.

---

### Post by Jman012 on 2012-12-05
Oh, I hope he isn't sick!

A few errors occurred: [http://pastebin.com/ZurwSr8S](http://pastebin.com/ZurwSr8S)

I hope those weren't caused by me trying to reinstall the drivers at all. Otherwise the wl driver seems to work, but the only problem I have with it is that it removes my wlan0, and replaces with an eth1. I guess I could open a new thread to see how to fix that.

And also here's a new dump of Wild Man's script, if you're interested: [http://pastebin.com/0KPkH9PY](http://pastebin.com/0KPkH9PY) (with wl driver working)

---

### Post by chili555 on 2012-12-05
>  Type:              802.11 WiFi
  Driver:            wl
  State:             [COLOR="Red"]connected[/COLOR]
  Default:           yes
  HW Address:        <MAC address removed>
 
  Capabilities:
    Speed:           130 Mb/s
 
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
 
  Wireless Access Points (* = current AP)
    Linnell_Extended:Infra, <MAC address removed>, Freq 2422 MHz, Rate 0 Mb/s, Strength 69 WPA2
    *Linnell1:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Xnet:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 0 Mb/s, Strength 20 WPA WPA2
 
  IPv4 Settings:
    [COLOR="Red"]Address:         192.168.0.99[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
 
    DNS:             209.18.47.61
    DNS:             209.18.47.62The part where you're connected and have an apparently working IP address, is that a problem for you?? Does it stay connected as expected?

The interface is supposed to be eth1 for the Broadcom STA driver. Not a problem.

---

### Post by Jman012 on 2012-12-05
Sorry for the delayed reply, homework and what-not.

wl has kept my connection well for the past few hours, so yes that's working quite well, so thank you for that. The reason I want wlan0 is because airmon-ng seems to like it better, it bugs out with eth1 now. But, that may be a bug with airmon-ng itself, so I can ask around their forums on that. Thank you though!

---

