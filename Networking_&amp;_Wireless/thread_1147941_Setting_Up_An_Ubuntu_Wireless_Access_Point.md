---
title: "Setting Up An Ubuntu Wireless Access Point"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by jlacroix on 2009-05-03
I am sick of my wireless router, it barely works and I don't have the money to replace it right now. I have an Ubuntu desktop machine with a wireless card, and I figured I would just set that up as a wireless access point. 

I followed this guide, which didn't work at all:
[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

In fact, an hour on Google proved futile. I'm still no further than I was when I started.

Basically here is what I want to do. I want to share the wireless connection on this computer with three other devices, each of them Linux. I want to create a WPA2 (or similar) encrypted network for all the wireless machines to use to connect to the internet. 

My Ubuntu Jaunty desktop computer (my spare) has a wireless card on it and connects to the internet via a wired connection to the router. I would like to share this some how.

In addition, I am going to be installing Ubuntu server, so I would prefer a method that didn't require GNOME or a GUI.

Has anyone been able to do this? I'm hoping so because I don't have the cash for a new router, and I figure my Ubuntu box should be able to take care of a wireless connection no problem.

---

### Post by pytheas22 on 2009-05-03
It's possible to do this, but only certain wireless cards support master mode, which is what you need to create a real access point.  If you post the output of these commands, I'll know which wireless chipset you have and can look up which modes it currently supports:
```

lspci -nn
lsusb
lshw -C Network
```

You can also try doing [this using ad-hoc mode]("https://help.ubuntu.com/community/WifiDocs/Adhoc#Supported%20Cards"), which will basically give you the same thing and is supported on more wireless cards.

---

### Post by jlacroix on 2009-05-04
Thanks! Sorry it took so long, I had a long day. Attached are files containing the output requested.

---

### Post by pytheas22 on 2009-05-04
It looks like your device (which uses the rtl8180 driver) should support master mode, according to [this page]("https://help.ubuntu.com/community/WifiDocs/MasterMode#Realtek%20RTL8180%20cards%20(rtl8180-sa2400%20project)").  So in principle, all you should have to do is bridge your wireless and ethernet interfaces together (which it looks like you've already done), install a dhcp server and tell it to listen on the wireless interface, then put the wireless card in master mode by typing:
```

sudo iwconfig wlan0 mode master channel 6 essid "Some Network Name"
```

Encrypting the network would involve extra steps, but if I were you, I'd focus for the time being just on getting things working with securing anything.

---

### Post by jlacroix on 2009-05-04
> **pytheas22 said:**
> It looks like your device (which uses the rtl8180 driver) should support master mode, according to [this page]("https://help.ubuntu.com/community/WifiDocs/MasterMode#Realtek%20RTL8180%20cards%20(rtl8180-sa2400%20project)").  So in principle, all you should have to do is bridge your wireless and ethernet interfaces together (which it looks like you've already done), install a dhcp server and tell it to listen on the wireless interface, then put the wireless card in master mode by typing:
```

sudo iwconfig wlan0 mode master channel 6 essid "Some Network Name"
```

Encrypting the network would involve extra steps, but if I were you, I'd focus for the time being just on getting things working with securing anything.

When I run that command, it keeps telling me "invalid argument".

---

### Post by pytheas22 on 2009-05-05
It might work better if you bring the interface down before putting it in master mode; in other words, type:
```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode master channel 6 essid "Some Network Name"
sudo ifconfig wlan0 up
```

Do you still get an error?

It's possible that the rtl8180 driver that ships with Ubuntu doesn't support master mode for some reason, but if that's the case it should be easy enough to patch it.

---

