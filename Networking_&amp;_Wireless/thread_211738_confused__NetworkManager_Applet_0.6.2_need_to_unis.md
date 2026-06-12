---
title: ":confused:  NetworkManager Applet 0.6.2 need to unistall"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by orb9220 on 2006-07-08
This applet called NetworkManager Applet 0.6.2

Which I don't know why it is not showing in add/remove or synaptic

I need to uninstall because it isn't working. shows no networks when the other one shows me connected.

It shows up in tray on boot up and is not in startup of sessions.

How do I find it and rip it's throat out?

Thanks

---

### Post by reacocard on 2006-07-08
sudo apt-get remove network-manager-gnome

---

### Post by orb9220 on 2006-07-08
Thanks that work like a charm

Now does anyone know if it is broken?
It was working it was just like the one below except it had alot more SSID's showing with signal strenght bars.
Is this the one that does that. I am kind of confused since I have been installing and trying different ones.

Or is it just broken  with my D-Ling DWL-G510 B1 card?

I am using KWiFiManger for real-time montoring of connection speeds.


And another that handles connectionss right now in the tray is:

 it has a left click popup 

Network conections "at the top with the following below it"
Wireless: ATH0 (Active)
Ethernet: sit0
Disconnect
------------------
Wireless Networks
[www.personaltelco.net](www.personaltelco.net) "with a strengh bar here"
Other
------------------
Connection Information
Configure Network connections
-------------------
Remove from Panel

This one has no About so what is the name of this one?

---

### Post by reacocard on 2006-07-09
I use network-manager all the time. it requires an edit to your /etc/network/interfaces for it to work though. All entries for interfaces to be controled by network-manager have to be either commented out or look like this:

```
auto eth0
iface eth0 inet dhcp
```

---

### Post by orb9220 on 2006-07-09
Nope just reinstalled and edited my /ect/network/interfaces to:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid [www.personaltelco.net](www.personaltelco.net)

auto wlan0
iface wlan0 inet dhcp

I commented out ethernet because I don't use.
But what about that first entry is it required and what does it do?

I know mine doesn't use the wlan0 because of resricted mode drivers?
But runs fine on ath0.

Would like to get gnome-manger to work but since upgrade a couple days ago 
this has stopped working and all I get is red slash circle for it,

the one that is working is described above and has no about so I don't know if it is an older version of wireless gnome-manger or where it is coming from.

Any help to resolve this is greatlly appreciated.

---

### Post by reacocard on 2006-07-09
the first entry is the loopback interface. lets your computer see itself. idk if its nessecary, but i always leave it anyway. no idea what's causing your problems, nm has always worked perfectly for me.

---

