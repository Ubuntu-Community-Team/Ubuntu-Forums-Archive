---
title: "Weird USB Specific Wireless Problem"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by dthomp325 on 2006-06-21
I have a weird problem with a USB wireless adaptor (D-Link DWL-G120) I installed via ndiswrapper. It works great if I boot the computer and then plug in the device once I have started a Gnome desktop. But, if the device is already plugged in before the computer boots, it will not work.

Here is how I setup my system. 

1. I used Automatix to install wifi packages including ndis-tools.
2. Downloaded drivers from the D-Link site labeled as version 1.12.
3. Extracted .inf file by using the command 'unshield x ' for both 'cab' files in from the download.
4. Installed .inf driver files with ndisgtk.
5. Deactivated Etherent card (eth1 on my system) with system->admin->networking tool.
6. Selected wireless network, entered WEP key and activated wireless card (wlan0 on my system) with system->admin->networking.
7. Ran ndiswrapper -m

Everything works

If I start my computer with the card unplugged, and then plug the wireless card into the usb port after I am in Gnome, everything works great and I connect to the network automatically. However, if I start the computer with the card already plugged in, it displays the wireless adaptor as 'eth1' instead of 'wlan0' and does not work correctly (none of the 4 broadcast SSIDs in my area even show up in the Gnome networking tool). Any suggestions?

---

### Post by noname101 on 2006-06-21
Its probably using a different driver when you have it plugged in at boot.
[http://www.prism54.org/newdrivers.html](http://www.prism54.org/newdrivers.html)
Your device is on that list. 
So try blacklisting islsm and p54u.
```
sudo gedit /etc/modprobe.d/blacklist
```
Add the following lines:
blacklist islsm
blacklist p54u
Also make sure you have ndiswrapper at the end of /etc/modules.

---

### Post by wislon on 2006-07-30
I have a similar problem, on a laptop, but I'm using WPA, not WEP. I am also using ndiswrapper, which identifies the driver as 'prisma02'. 

Dapper hangs on bootup if the USB adapter is plugged in. If I leave it for a couple of minutes, it does eventually come up, but won't associate with my access point until I launch wpa_supplicant. At which point, it works fine. 

I tried to use WiFi-Radar, but as soon as soon as I log in, and it's associated, it locks up so hard I have to pull the battery out of the laptop in order to get it to shut down. Even the mouse dies.

So I got it working without wifi-radar. It's flaky though. Within minutes, it loses the connection and I have to stop and restart the wlan0 device. It doesn't matter if I'm using the network or not, it goes down. I can't tell if it's a driver problem with the card, or if it's maybe some sort of power saving thing. 

But thanks for the heads-up, I saw this in passing. I am going to try blacklisting those modules (if they exist) and see if it makes any difference. If it does, I'll update here :)

(update)
Turns out those modules aren't present on my system, so I can't blacklist them. However I came across a post that indicated that network manager (and others) would have problems connecting me to a network if the device was present in the /etc/network/interfaces file.

I left the iwconfig etc. stuff alone, where I set my static IP address, gateway and blah, but commented out the 

auto wlan0 

line at the bottom of the file. Now all of a sudden wifi-radar no longer hardlocks, and the connection seems a hell of a lot more stable.

I also upgraded the firmware of the access point, and that seems to have helped too. I'll see how this flies for a while

(further update)
Since I removed the 'auto wlan0' at the bottom of the interfaces file, it's been rock solid. No crashes, no hanging, nothing. I now have wifi-radar loading as a service on bootup, and it all appears 100%! :)

The wireless still goes to sleep if I don't use it for an extended period, but I think thnt may be a power-saving thing, and I'm not too worried about it right now.

---

