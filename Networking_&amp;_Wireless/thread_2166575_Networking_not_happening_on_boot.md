---
title: "Networking not happening on boot"
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by scbingham on 2013-08-10
Hello All

I have quite a new install of 12.04 server & it seems that since it upgraded to 3.5.0-37-generic, networking no longer happens on boot. This might be pure coincidence.

I do see a message 'waiting on networking' & see 2 or 3 FAILs among the boot messages.

Ideally I want to connect it to my network wirelessly, I do have a very long ethernet cable for emergencies.

I did try following some articles the other day & tried things which I now can't remember, so take nothing for granted. So before I start stumbling in the dark again, I thought I better ask here.

The only way I can get info off the server to here is via usb stick.

Here is my /etc/network/interfaces:

auto lo
iface lo inet loopback


# The primary network interface
auto wlan0
iface wlan0 inet static
    address     192.168.0.51
    netmask     255.255.255.0
    network  192.168.0.0
    broadcast 192.168.0.255
    gateway  192.168.0.1
    wpa-ssid xxxxxxxx
    wpa-psk  xxxxxxxx


iface eth0 inet static
    address    192.168.0.50
    netmask    255.255.255.0
    network    192.168.0.0
    broadcast 192.168.0.255
    gateway    192.168.0.1


dns-nameservers 8.8.8.8
dns-nameservers 8.8.4.4

Here is my resolv.conf:

nameserver 8.8.8.8
nameserver 8.8.4.4 

I'm open to all & any suggestions & requests for more info.

Thanking you all in advance.

Mods, if this doesn't belong here, feel free to move it.

PS I don't know why 64 bits is in the tags. It's a 32bit system.

---

### Post by Irihapeti on 2013-08-10
*Thread moved to **Networking & Wireless**.*

---

### Post by scbingham on 2013-08-11
Irihapet, thanks for pointing me to the NewDocs. That has mostly helped me restore the basic networking.
Not sure a backup would have helped in this scenario as the damage was caused by the upgrading to 3.5.0-**37**. Even falling back to [COLOR=#000000]3.5.0-**23** didn't help, as it seems my config files had been altered. I didn't expect an upgrade to cause that. (3.5.0-23 is what's on my install cd)

I didn't get the wpa_supplicant bit to work, the commands added to /etc/network/interfaces are not found, not sure if that bit is required though.

It looks like I'm back to where I was, where I'm unable to connect to security.ubuntu.com when doing sudo apt-get update. Adding it to /etc/hosts doesn't help.

BTW, there might be a typo in the wiki in the "[/COLOR]Disable network managers and/or wicd" section:

# Or remove the wicd package.
sudo aptitude purge **network-manager**
# Reverse: sudo aptitude install [B]network-manager

[/B]Might want to read wicd ?

---

### Post by scbingham on 2013-08-11
Looks as though my problems are caused because I set a static ip address. As soon as I change eth0 to dhcp, all routing works, albeit only through eth0, not wlan0. Unfortunately I want a static ip address, as it's a server.

After much reading I still can't make this work. Anyone have any ideas or point me to another how-to or article to read? :confused:

---

