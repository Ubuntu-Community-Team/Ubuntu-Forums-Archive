---
title: "Looking for a simple solution to connect to multiple networks"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by tsvim on 2006-04-17
Ok, I suppose this should't be to complicated although I can't seem to find something simple to do the job.

I use my laptop at multiple places:

Wireless at home and at campus.
Wired at my parents home.
Wired at my inlaws.
Sometimes wired at home (if i need a reliable connection for large downloads).
Wireless "On the go": searching for any free local hotspot.

At most when I turn my laptop on I don't want it to scan for networks: I'm usually not in range. To save battery I leave my wireless card outside (DWL650GM). 

Problem is as follows:
a. My laptop won't discover the wireless card if it is not plugged in at boot time ??? Meaning when I go from class to the library on campus (out of range to in range) I need to reboot the laptop if I wan't to hook up to the network.

b. I understand that the reason boot time takes so long on during the configuring network is because I'm not connected. 
What I would like is that whenever I plug in my wireless card the laptop automatically searches for a network or else with a simple command in the terminal something reading "wifi home", "wifi ac" etc... the wireless should automatically look for those networks defined by ssid.
When I plug in a ethernet cable, it should automatically try and self configure using dhcp.

c. I'm having trouble finding the "disconnect hardware safely" in linux. I'd like to disconnect my wireless card (save battery) and I'v got no clue how to do it without shutting down the laptop.

Thanks for your time and effort guys, you make the world a better place.

Tsvi

```
/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
gateway 10.200.1.1

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep

# The primary network interface



iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid lev

auto eth0

```

---

### Post by prizrak on 2006-04-17
a) I'm not too sure on this one, I *think* it might be in fstab, you might have to just restart that. Check [THIS]("http://doc.gwos.org/index.php/Main_Page") site out to find out how to use it. In fact it might have all the answers you need :)
b) Hit CTRL+C when it's trying to find your network at boot, it will skip it. There is no EXACT functionality AFAIK that you are looking for, I do hear that Network-manager can do what you want (never got it to work on my system). If you don't care about waiting I hear it will be included in the next version.
c) There is no GUI for it, but you basically just stop the device. See the above site, or just google for "Stopping devices in Linux". Command is something like (not an exact command, and might be completely wrong)
> sudo stop /dev/wifi

---

### Post by stuporglue on 2006-04-17
>  a) I'm not too sure on this one, I *think* it might be in fstab, you might have to just restart that. Check THIS site out to find out how to use it. In fact it might have all the answers you need

Mmm. fstab is for disks and mounting, not network devices and startup. 

To get the functionality you're looking for, you may have to play with some udev rules/scripts. Udev will notice when the card gets plugged in, and you can create rules for it, and tell it "when wireless card gets plugged in, connect to network".  I don't know how to do that, but maybe knowing what to look for will still help. 

> c. I'm having trouble finding the "disconnect hardware safely" in linux. I'd like to disconnect my wireless card (save battery) and I'v got no clue how to do it without shutting down the laptop.

It's a PCMCIA card I take it? You can probalby just unplug it -- have you tried? Worst case, you can open up the network manager, and disable the device before unplugging.

---

### Post by tsvim on 2006-04-18
> It's a PCMCIA card I take it? You can probably just unplug it -- have you tried? Worst case, you can open up the network manager, and disable the device before unplugging.
I tried unplugging it directly. But for some weird reason when I unplug it and plug it back in it will give me problems: only one led will stay on the other one stays off. (If LEDs are blinking simultaneously I'm connected, if they're blinking one after the other the card is looking for a connection)

---

### Post by stuporglue on 2006-04-18
A udev script will note when it's been removed and make the comptuer stop trying to talk to it. Then when you plug it in again, it'll recognise it again (and use the udev script again).

---

### Post by prizrak on 2006-04-18
stupor,
Thanks for correcting me, I was very unsure if fstab dealt with anything other than storage.

---

### Post by vinfred on 2006-04-20
have a look at [http://www.us.debian.org/doc/manuals/reference/reference.en.html](http://www.us.debian.org/doc/manuals/reference/reference.en.html)

see sections 10.9 and 10.10 as a start

vinfred

---

### Post by m0nstr42 on 2006-04-20
I don't have a hotpluggable wifi card, but I've had good luck being mobile with the following setup:  

[LIST]
[*]I don't have any auto interfaces in /etc/network/interfaces, so the kernel doesn't try to connect to any networks when I boot.  
[*]When I'm all booted up (or at a new location), I do a "sudo iwlist scan" to see if the network I want is actually there (still having some weird problems with this step).
[*]I have a collection of custom interface files, e.g.
```
# /etc/network/school.interfaces
# use: ifup -i school.interfaces wlan0

auto wlan0
iface wlan0 inet dhcp
wireless-essid myschoolsessid

```
and home.interfaces, panera.interfaces, etc... 
[*]To connect to the appropriate one i just do ifup -i school.interfaces wlan0
[/LIST]
I also wrote some super simple scripts to generate these files automatically and to generate a script file to run them, so I can just do a "sudo wifi-add somenet wlan0" to add a new network and a "sudo wifi-somenet" to connect to it every time after that.  I used to do it manually (e.g. iwconfig wlan0 essid somenet, ifconfig wlan0 up, dhclient wlan0) but that didn't seem to work very well.

There may be a better way... please enlighten me if there's something better that is simple and reliable.

---

