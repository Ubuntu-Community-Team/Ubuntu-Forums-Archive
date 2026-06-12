---
title: "Network Manager (Disconnected)"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by NiGhtMarEs0nWax on 2010-03-20
Hi, I'm running Ubuntu Karmic Server with Xfce desktop, the problem is the network manager, it says it is disconnected, even though i am connected to my network and getting an internet connection.


It wouldn't normally bother me, but I'm trying to setup a VPN using the network-manager-openvpn plugin. I put in the required details for the VPN connection, but as soon as I tick the "apply to all users" box, the information is lost.
the information will remain if I don't tick that box, but it will not connect. when I try to select the VPN connection I just setup, nothing happens.

is there a problem with the network manager?




EDIT: ok i've tried the exact same configuration on another desktop, running Ubuntu Karmic with Gnome desktop, the network manager works fine, my ethernet connection is showing as connected, and i can connect to the VPN no problem, the problem lies with the network manager in Xfce.

is there anyway i can get it to show as connected? it wont allow me to connect to the VPN otherwise, it's silly, because that adapter has a full working network connection.

---

### Post by NiGhtMarEs0nWax on 2010-03-20
Solved.

changed the config found in /etc/NetworkManager/nm-system-settings.conf


the default is:

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

changed this section:

[ifupdown]
managed=true

then reboot or reload config.

---

### Post by NiGhtMarEs0nWax on 2010-03-20
ok the problem still persists, it appears that even though i managed to get the vpn working, i can't get it working when the option "allow all users" is ticked. i get a message saying that the vpn service was unable to start.

any suggestions are welcome, thanks. :)

---

### Post by NiGhtMarEs0nWax on 2010-03-21
bump

---

### Post by Iowan on 2010-03-21
Does */etc/network/interfaces* contain more than two lines define "lo"?

---

### Post by NiGhtMarEs0nWax on 2010-03-21
this is what is in it,

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```


Thanks.

---

### Post by Iowan on 2010-03-21
Comment out the two "eth0" lines and restart/reboot - see if Network Manager recognizes eth0.

---

### Post by NiGhtMarEs0nWax on 2010-03-22
yeh it does. I'm connected to my subnet.

---

### Post by NiGhtMarEs0nWax on 2010-03-23
bump, sorry. :P

---

### Post by Iowan on 2010-03-23
> **NiGhtMarEs0nWax said:**
> yeh it does. I'm connected to my subnet.
What's next on the to-do list? Does VPN work better with NM in control of eth0?

---

### Post by NiGhtMarEs0nWax on 2010-03-23
Thanks, it works just the same.

could it be a permissions problem? a group issue maybe, i'm not sure, i'm still learning.


one of the accounts I have is a limited user.


this is my NM log when connecting with the "all users" option ticked. /var/log/daemon.log

```
Mar 24 00:36:23 GuestServer NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Mar 24 00:36:23 GuestServer NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 1804
Mar 24 00:36:23 GuestServer NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Mar 24 00:36:23 GuestServer NetworkManager: <info>  VPN plugin state changed: 3
Mar 24 00:36:23 GuestServer NetworkManager: <info>  VPN connection 'UltraVPN' (Connect) reply received.
Mar 24 00:36:23 GuestServer NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'UltraVPN' failed to connect: 'No VPN secrets!'.
Mar 24 00:36:23 GuestServer NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Mar 24 00:36:24 GuestServer NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 24 00:36:36 GuestServer NetworkManager: <debug> [1269390996.014026] ensure_killed(): waiting for vpn service pid 1804 to exit
Mar 24 00:36:36 GuestServer NetworkManager: <debug> [1269390996.015402] ensure_killed(): vpn service pid 1804 cleaned up
```



here is 'mesages,' not much.

```

Mar 24 00:36:23 GuestServer kernel: [  383.696075] tun: Universal TUN/TAP device driver, 1.6
Mar 24 00:36:23 GuestServer kernel: [  383.696730] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>

```


is there a way to log openvpn? i'll have a look tomorrow when i get time. i would post my config files if i could find them, they are not in /etc/openvpn.


Cheers.

---

### Post by NiGhtMarEs0nWax on 2010-03-24
on a second look it appears that my password is not persistently  stored in network manager. I have the VPN authentication type set to password.

---

### Post by Iowan on 2010-03-24
I recently learned that NM stores it's settings in */etc/NetworkManager/system-connections*. You might check the interface file(s) there to see if additional information needs to be saved.

---

### Post by NiGhtMarEs0nWax on 2010-03-24
Thanks for the reply man and your helpful input, but I've decided to just use the shell and openvpn directly to connect to the VPN service. 

It seems that there is a bug that has went unfixed for quite some time, it was present in jaunty and is still present in karmic, it is to do with the keyring, my authentication credentials are not being stored when the "all users" option is ticked. I've read a lot of rather complicated work arounds that I am not prepared to do when I can just connect through the shell.

Thanks again mate. :)

---

