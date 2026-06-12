---
title: "map windows share"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by arturusch on 2011-11-24
Hi guys,

Newbie on Ubuntu and Linux but getting along. Nice OS.
I managed to connect to VPN server via network manager.

What is the best solution on maping my drives on windows machine at work?

Do I Need to mount, is Samba a solution, mapping? 
How can I approach this?

---

### Post by ptrakk on 2011-11-24
yeah you'll need samba.
'sudo apt-get install samba'
there are many ways to do this.
create the share.


port forward passed the firewalls (as well as with the routers). 

The following ports are associated with file sharing and server message block (SMB) communications:
Microsoft file sharing SMB: User Datagram Protocol (UDP) ports from 135 through 139 and Transmission Control Protocol (TCP) ports from 135 through 139.
Direct-hosted SMB traffic without a network basic input/output system (NetBIOS): port 445 (TCP and UPD).


google "what's my ip" to get the public ip address.
then connect via direct ip smb://ipaddresshere/

---

### Post by arturusch on 2011-11-25
Yeah,
 
I dont know if smbfs or samba was needed.
 
I managed after installing samba and smbfs to mount via -t cifs option.
 
Heh, as long as you go you encounter different issues that leads you to what you are really after.
I guess for my users using linux I need to have a script or something to automount when vpn is up and running.
 
The script need to check for vpn connection, when it is there it needs to mount my share. 
Then after log-out or maybe when ShutDown / REstart is in progress it needs to unmount the share so the system wont hang up.
 
I think that is pretty much that.
 
Do you think I need an automount shell script to be coded?
 
I mean, maybe I dont need any script and can do it allready with some client Ubuntu already has, but, me being newbie, I dont know that.

---

