---
title: "Ubuntu 8.10 fresh install, network stops responding"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by pico303 on 2008-12-13
I just did a fresh install of Ubuntu Intrepid 8.10 to get the fakeRAID support working.  Everything seems to be working fine, except that after installing KVM ([https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)), my bridge network br0 stops responding to requests after about 20 minutes.  SSH says "connection refused", HTTP requests return "host not found", everything.  

I can still access the internet from the machine itself, and I can talk to the two virtual machines hosted on the computer, I can even ssh to localhost.  Just nothing can connect to the computer from the outside.

No iptables or any other firewall software I know of is running. 

No log messages in syslog or messages.  I'm completely befuddled.

Here's my network interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface br0 inet static
address 10.0.0.100
netmask 255.255.255.0
gateway 10.0.0.2
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

Is there somewhere I can check the status of the bridge?  I confess I'm new to bridge-utils.

---

### Post by pico303 on 2008-12-14
Having fought with this thing all day, I think I'm just going to call it quits and go back to Hardy.  Too many people complaining about random Intrepid dorkiness for me to ever trust this thing.  

Hopefully KVM will still work for me under Hardy.  I'd tried doing the upgrade to Intrepid before wiping and going from scratch, and never had these problems, so maybe I should try that again when I'm feeling up to fighting with Linux some more.

If anyone is still interested in this problem, after 8 hours of fighting it, here's what appears to happen:

[LIST]
[*]Bridging starts up fine.  Can connect to the host server (10.0.0.100) and all the KVM instances (10.0.0.102-104) just fine.  Can HTTP (through Apache mod-proxy) to all the KVM instances as well.

[*]After anywhere from 15 minutes to a couple of hours, depending on usage, I can sporadically ssh to the host server.  Can still ssh to the KVM instances with no problem, though.

  ssh: connect to host 10.0.0.100 port 8150: Connection refused

Then the connection will pop back in.  Takes a progressively larger number of tries to connect.

[*]Eventually ssh fails to connect all together, returns nothing but "connection refused".

[*]HTTP/mod-proxy stops responding on 10.0.0.100 (host), but I can connect directly to the KVM instances (10.0.0.102-104).
[/LIST]

I'm at a loss.  Doesn't appear that the bridge-utils log any kind of messages to any of the log files, so it's a tad difficult to debug what the heck is going on.  

Have to say I'm a bit disappointed in Intrepid, but this seems to be pretty standard when it comes to upgrades these days.  Upgrading an existing system works great (Hardy -> Intrepid), because the left-over libraries improve the stability of the system, while fresh installs are a nightmare.

Oh well, hopefully I'll have better luck with Hardy.

---

### Post by pico303 on 2008-12-15
Went back to Hardy and everything works great.  Looks like I'll be waiting until the next LTS version of Ubuntu before I try upgrading again.

---

