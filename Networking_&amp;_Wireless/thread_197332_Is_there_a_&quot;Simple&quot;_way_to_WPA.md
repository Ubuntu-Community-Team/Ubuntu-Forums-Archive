---
title: "Is there a &quot;Simple&quot; way to WPA"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by Rollotamasi on 2006-06-15
My work network uses WPA and I would really like to get this running.  I found a guide at [http://www.ubuntuforums.org/showthread.php?t=125150&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=wpa) but honestly it seems very complicated to a linux newbie like me.  Is there a simplier way to configure so that I can use WPA or is the process listed in that guide the only way to do it?

Thanks all

---

### Post by Slicedbread on 2006-06-15
Is your card installed and working already? If it is you can just download network-manager-gnome from synaptic and it will manage wpa connections automatically.

If you dont have your card installed and working you can post it here and someone will help you.

---

### Post by Rollotamasi on 2006-06-15
[QUOTE=Slicedbread]Is your card installed and working already? If it is you can just download network-manager-gnome from synaptic and it will manage wpa connections automatically.

If you dont have your card installed and working you can post it here and someone will help you.[/QUOTE]

Funny little story about that... It was installed and working fine (Just couldnt use WPA) and then I installed "Network manager gonome with the denbian thingy" And now it doesnt show up at all :(

---

### Post by Slicedbread on 2006-06-15
What doesnt show up? the applet will be there if you installed it and reboot. Try going to the terminal and typing "nm-applet" to see if its starts or add nm-applet--sm-disable to your startup programs in system>preferences>sessions.

---

### Post by Rollotamasi on 2006-06-15
Sorry, What I meant was that the wireless network adapter itself doesnt show up anymore under the "Networking" options.  It used to showup along with my standard ethernet adapter.

---

### Post by Slicedbread on 2006-06-15
Do you AIM, if not post your "/etc/network/interfaces" file. Gnome network manager takes control of your network connections when you install it, but it shouldnt remove any thing.

---

### Post by Rollotamasi on 2006-06-15
[QUOTE=Slicedbread]Do you AIM, if not post your "/etc/network/interfaces" file.[/QUOTE]
Aim is in istant messenger?  Yes, I do.  Username is Rollotamasi

---

### Post by Rollotamasi on 2006-06-15
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Airport Extreme
wireless-key 0k1cu812

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

---

### Post by Rollotamasi on 2006-06-15
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Airport Extreme
wireless-key 0k1cu812

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

---

### Post by Slicedbread on 2006-06-15
It will be easier if you sign on to your aim account.
Delete 
"wireless-essid Airport Extreme"
"wireless-key 0k1cu812"

and try it again, network-manager-gnome only works with the first two things enabled.

---

### Post by Rollotamasi on 2006-06-15
[QUOTE=Slicedbread]It will be easier if you sign on to your aim account.[/QUOTE]

Sorry, had to log off to come home from work.  Booting it up in a sec

---

### Post by Rollotamasi on 2006-06-15
Sorry, I need to use my other account.  Name is jmcleinpixel

---

