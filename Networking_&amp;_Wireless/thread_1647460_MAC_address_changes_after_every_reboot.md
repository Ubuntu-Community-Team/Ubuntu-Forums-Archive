---
title: "MAC address changes after every reboot"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by PlanetT on 2010-12-17
Hi there,

I have a problem w/ the LAN connection: the MAC address appears to be different after every reboot. I checked it w/ the ifconf command and looked for the eth0 hardware address. I am using Ubuntu 10.10 on ASUS K51AE laptop. The Fax/Modem/LAN/WLAN interface is integrated 802.11 b/g/n (I only have problem with the LAN connection).

Does anyone have any idea how this problem could be resolved? Currently I cannot use my modem internet connection, it is really annoying. I would like to keep on using Ubuntu, but if I cannot find a solution I will have to return to windows...

Thanks in advance,
PlanetT

---

### Post by PlanetT on 2010-12-18
With lspci I could find out that my ethernet comntroller is

02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)

I have found some references on the internet that suggests that the comntroller is not supported in Hardy

[https://lists.ubuntu.com/archives/kernel-team/2009-March/004795.html](https://lists.ubuntu.com/archives/kernel-team/2009-March/004795.html)

but I am not sure if this shortcome still exist in 10.10. 
Any idea how to activate the controller?

PlanetT

---

### Post by Ubunterrific on 2011-02-10
> **PlanetT said:**
> With lspci I could find out that my ethernet comntroller is

02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)

I have found some references on the internet that suggests that the comntroller is not supported in Hardy

[https://lists.ubuntu.com/archives/kernel-team/2009-March/004795.html](https://lists.ubuntu.com/archives/kernel-team/2009-March/004795.html)

but I am not sure if this shortcome still exist in 10.10. 
Any idea how to activate the controller?

PlanetT

I'm having the same trouble with Maverick 64bit. Never had any issues up until now, but the ethernet connection changes MAC address every time the laptop is switched off :( 

Did you find a solution? A fresh install maybe? A new kernel wouldn't solve it, would it?

---

### Post by Ubunterrific on 2011-02-10
[http://ubuntuforums.org/showthread.php?t=94891](http://ubuntuforums.org/showthread.php?t=94891)

There's a post on here which solved my problem :) It involves adding a few lines to "/etc/network/interfaces" :

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp
hwaddress ether 00:a0:WH:AT:EV:ER  
auto eth0 			 		

et viola! New MAC address which YOU specified. Obviously you need to change "00:a0:WH:AT:EV:ER". Type "sudo ifdown eth0" to disconnect the connection and "sudo ifup eth0" to reconnect with these new settings. (Substitute "eth0" for the name of your connection of course") :D Wooohoooo!

---

