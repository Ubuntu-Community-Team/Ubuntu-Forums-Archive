---
title: "OpenVPN help needed"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by Derek Karpinski on 2011-08-02
I'm in over my head here.  I want to set up openvpn, but haven't a clue how.
 
Details:
-Ubuntu 11.04 'server'
-Windows 7 laptop
-laptop documents and folders are mapped to the Ubuntu box's samba shares
-Cable internet
-dyndns account
-Wireless router (dlink 615)
 
What I want to do:
-Use openvpn to connect to our home network with all our pictures and files when are out of our wireless range.
-Use our home wireless network when we are at home.
-use my dyndns account to handle changing ip addresses.
 
What I've done so far:
-installed openvpn on both computers:KS
-created keys (maybe not correctly):confused:
-spent hours reading threads](*,)
-neglected my wife for days while trying to figure this out [-X:mad:
 
I have not messed with the routers IP addresses, port forwarding, firewall setttings, and the config files.  I just do not understand it.
 
Be a friend, save my marriage, and help me set up openvpn. :D

---

### Post by Derek Karpinski on 2011-08-03
I've reinstalled everything, and regenerated the keys.  The ubuntu openvpn server starts fine, and when I start the windows openvpn client, the keys seem to authenticate, but I get a message:
 
```
 
TCP/UDP: Incoming packet rejected from xxx.xxx.xxx.xxx:1194, expected peer address: xxx.xxx.xxx.xxx:1194 (allow this incoming source address/port by removing --remote or adding --float)

```
 
I'm connecting to the internet on the laptop via the wireless router.  Do I need to get off my local network before this can work?:confused:

---

### Post by Derek Karpinski on 2011-08-05
Solved:
 
It is seemingly impossible to connect to the VPN server from within your own network.  I had to take the laptop to Starbucks and the VPN works, and I can ping 10.8.0.1!:D

---

