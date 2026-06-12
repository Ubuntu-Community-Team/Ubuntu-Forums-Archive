---
title: "VPNC Certificate based authentication"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by DiGiTGOD on 2011-03-24
So, my company has a couple of locations that have Cisco firewalls with VPN access (think they are all PIX ones).

The first is a simple username/password based authentication, which is fine in ubuntu, using the network manager (network-manager-vpnc).

The issue is the secured datacentres use something a method I've not seen documented anywhere, and I'm wondering if there is any software out there that will allow me to connect using ubuntu.

There is no "Group name" or "Group secret/password".  We each have a personal certificate that is installed on the machine, then a personal username and password to connect.

The windows client that Cisco supply does work fine (Version 5.0.x.x), but they don't supply a linux client.

So, can anyone either point me in the direction of a tutorial on configuring this with vpnc (commandline or network manager).  Alternatively, can anyone point me in the direction of some linux software that will do the job (preferably FOSS).

Thanks in advance...

Martin

---

### Post by sriniramesh@hotmail.com on 2011-08-01
Hello DiGiTGOD, did you make any head way in your attempt. I am in a simillar situation cisco certificate authentication without group id/pw. 
 
Actually, my company did provide a linux based cisco any client, but encountering certificate validation error with that. I tried various ideas from different forums, but no luck. Thinking of abondoning cisco any client and try to use VPNC with KVPNC.
 
Any assistance will be appreciated!
 
Thanks!
Sri.

---

