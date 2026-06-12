---
title: "Update to isc-dhcp server broke network"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by AndrewWalker on 2013-04-22
I recently did an update of isc-dhcp-server on my 12.10 box and it's killed my network. The update was the following
isc-dhcp-server:amd64 (4.2.4-1ubuntu10.1, 4.2.4-1ubuntu10.2),

I'm using a bridged network with wireless wlan0 and eth1 interface with eth0 being my incoming connection.The message I'm getting is

[ 1916.189836] type=1400 audit(1366669021.452:45): apparmor="DENIED" operation="create" parent=1 profile="/usr/sbin/dhcpd" pid=5702 comm="dhcpd" family="packet" sock_type="raw" protocol=768
[ 1916.192514] init: isc-dhcp-server main process (5702) terminated with status 1
[ 1916.192582] init: isc-dhcp-server main process ended, respawning

what does  apparmor="DENIED" mean and is this the problem? I'm basically using it as a router/server but I'm no expert is setting it up though up until now it has been working fine. The eth0 port is working fine by the way.

Any suggestions?

---

### Post by nickswift on 2013-04-23
The latest update broke the apparmor profile. This prevents dhcpd from binding to the network port and means none of your client devices will get an IP address.

I added network packet raw to the usr.sbin.dhcpd apparmor profile in /etc/apparmor.d

You then need to reload the profile using service apparmor reload and restart the service isc-dhcp-server as it will have stopped.

Et voila.

This update appears to have regressed a previous fix - see [https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1107686](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1107686)

---

### Post by AndrewWalker on 2013-04-23
Nice one, I'm forever in your debt! Seriously, I could of spent months trying to work that one out, you've saved me from a living hell with the wife's Nexus 7 not connecting to the web!

---

### Post by MickelJohn on 2013-04-24
Well this worked for me last night but this morning it was broken again. I've checked everything I've found to fix it but no joy. The apparmor profile is the correct on as far as I can see and it has the added information but isc-dhcp-server will not start. Same error

---

### Post by AndrewWalker on 2013-04-24
I did apt-get update an hour or so ago and there was an update for isc-dhcp-server which I assume is a fix, have you checked you're up to date?

---

### Post by MickelJohn on 2013-04-24
I did that last night and found the update. It fixed it then but this morning (8 hours later) the problem is back. I did another check for updates but none are available.

---

