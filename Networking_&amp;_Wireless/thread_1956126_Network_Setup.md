---
title: "Network Setup"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by LMPHOENIX on 2012-04-10
Ok guys im new to the forum and a relative beginner when it comes to the world of unix, I have searched both around the forum and google and cant quite find the information im looking for so I thought i'd ask.

Right here it is below is a simple sketch of my network setup at present

What i want is to have all the traffic routed through the ubuntu box 
but i only have the one nic available 
so i cant connect the modem to the server instead of the netgear 
Is it possible to do this without another nic

[IMG]http://img826.imageshack.us/img826/4396/sketchv.jpg[/IMG]

---

### Post by roelforg on 2012-04-10
If the server has a spare pci-slot,
you can go to your local tech-store and pick an ethernet card up for ~20 bucks.
That should solve it.

EDIT:
Didn't read the entire post...
What does the server do that makes it need all the traffic routed to it?
If it's only one service, just setup an dns-server and make it the default for all clients.
Put in a good dns name (mine is server.local but .local usually interferes with some apps).
And address it with the new dns name.

---

### Post by LMPHOENIX on 2012-04-10
the server is running a multitude of service like
appache mysql torrent server samba ushare all working fine at the moment 
i want to eventually have the server doing some qos and firewalling me at the moment the router is doing most of the filtering but doesnt have qos support

---

### Post by roelforg on 2012-04-10
> **LMPHOENIX said:**
> the server is running a multitude of service like
appache mysql torrent server samba ushare all working fine at the moment 
i want to eventually have the server doing some qos and firewalling me at the moment the router is doing most of the filtering but doesnt have qos support
Like i said, go to your local tech-store and get yourself an extra nic for ~20 bucks,
the only other option is a rather complex setup involving a local VPN from the clients (except the Xbox) to the ubuntu server, bridge the vpn with the nic and have the firewall and other stuff work on the bridge.

---

### Post by LMPHOENIX on 2012-04-10
ok i new the second nic was probably the way to go just wanted to see if it was possible with just the one and how complicated

---

### Post by CharlesA on 2012-04-10
> **roelforg said:**
> Like i said, go to your local tech-store and get yourself an extra nic for ~20 bucks,
the only other option is a rather complex setup involving a local VPN from the clients (except the Xbox) to the ubuntu server, bridge the vpn with the nic and have the firewall and other stuff work on the bridge.
+1. The best way to do it would by to grab another NIC and set the ubuntu box as the gateway and run with it like that.

That being said, however, I prefer having the box I'm using as a gateway running only a minimal amount of services. That way, if it gets owned, I'm not totally screwed.

---

### Post by roelforg on 2012-04-10
> **CharlesA said:**
> +1. The best way to do it would by to grab another NIC and set the ubuntu box as the gateway and run with it like that.

That being said, however, I prefer having the box I'm using as a gateway running only a minimal amount of services. That way, if it gets owned, I'm not totally screwed.
Yeah.

Though, with a tight firewall config and snort with thorough monitoring and a big alert (i read somewhere you can configure snort to fire a script on big alert, hook up a speaker to the server and have it play a really loud sirene when the script execs and add another one for critical threats that kills eth0 (the public one) and plays the sirene.)
That's overkill for most home-server situations but should work.

You can always go to some friends,family,local recycling shop,dump,yard sale,etc. and pick up an old pc, replace the nic with 2 good ones and have it dedicated to firewalling and snort.

---

