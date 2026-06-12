---
title: "Still can't share an Internet connection with Windows XP client."
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-02-01
I have been trying off and on for weeks to share my Internet connection with a Windows XP client (netbook).  While I can ping back and forth between the two machines, in the form of a ping test, I can't get to the Internet from the client, no matter what I try.

My Ubuntu 9.10 desktop (host) has two NICs, eth0 and eth1.  eth0 connects to  the Internet.  eth1 goes to the Windows XP client.  Regardless of whether I use an Ethernet crossover cable or a standard cable, I can get the two machines to talk to each other, but no further.

Things I already tried:

-Tried setting eth1 to "shared" mode in NetworkManager on the host.  I set the Win XP machine to automatically acquire an address & DNS.  Didn't work.

-Manually configured the IP settings on both machines, like this:
client: 
address 10.0.0.2
subnetmask 255.255.255.0
gateway 10.0.0.1
DNS: OpenDNS servers

host (via eth1):
address 10.0.0.1
subnetmask 255.255.255.0
gateway 192.168.1.1 (address of my router)  
DNS: OpenDNS servers

This partially worked, in that the client detected a live connection to the host.  I was able to send pings back and forth, but still could not get to the Internet from the client.

-Combinations of the previous two items (e.g. manually configuring the client's IP while "sharing" eth1 in NetworkManager).  Also didn't work.

-Removed NetworkManager applet from the host, replaced it with Gnome Network Admin.  This didn't change anything.

-Turned on kernel IP forwarding at the command line, using the command:
```
sudo sysctl net.ipv4.ip_forward=1
```

This also made no difference.

Despite all of the above, I still cannot share the host's Internet connection with the client.  I don't understand where the client's traffic is going, and why I can't share the connection.  As far as I know, I am not doing any sort of firewalling or blocking on the host, so there is no obvious reason that the client's traffic simply disappears.  I just know that whenever I open a Web browser on the client, all I ever get is error messages.

I have had no issues setting up a shared connection when the host runs Windows XP, so I am pretty sure there is no broken hardware causing the problem.  Why can't I share the connection under Ubuntu?

---

### Post by Iowan on 2010-02-01
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for ICS.

---

