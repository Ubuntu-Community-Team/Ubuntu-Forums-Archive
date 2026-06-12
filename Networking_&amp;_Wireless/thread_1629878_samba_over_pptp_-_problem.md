---
title: "samba over pptp - problem"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2010-11-24
I have installed and configured pptp on my 10.04 box. After a lot of googling, I have amended sysctl.conf to allow ipv4 forwarding, and my firestarter firewall to allow VPN traffic.

Network adapter is wlan0


I have created a VPN user with a password, in chap-secrets.

I have port forwarded 1723 in my router

Connecting from my vista PC seems fine ... it connects, authenticates, and registers my machine on the network. Checking the network properties shows it has correctly picked up the desginated IP address, 10.1.2.3 

However it stops there. Although I can access samba shares by 192.168.1.20\MyShare via wlan0 (that is, as an internal LAN share) trying 10.1.2.3\MyShare pops up a Windows authentication box. When I use "guest" and blank password, I just get an authentication error.

Although I can access [http://localhost](http://localhost) from the machine, and [http://192.168.1.20](http://192.168.1.20) from the LAN, trying to access [http://10.1.2.3](http://10.1.2.3) just throws a "internet explorer could not access the site" error.

As far as I know, this isn't a firewall issue, now - the VPN is established, so there's something more subtle going on. If the samba share didn't work from the LAN, then obviously that would hint at a problem with samba. But the fact it does, and also the fact I can't access [http://10.1.2.3](http://10.1.2.3) implies a different issue.

From what I can tell, the user I created in chap-secrets, is unknown to the rest of my system. So is there a permissions issue ? However, when I connect to the samba share, I am prompted for credentials, so they should sit on top of the underlying VPN user ?

Can anyone help ?

---

### Post by endotherm on 2010-11-24
I think your issue is with more than samba, based on the HTTP 404 error. perhaps a traceroute from source to dest may help, since it is a vpn tunnel.

I believe the samba auth box is popping up, because the server cannot be connected to, but it doesn't know if the service is even there to connect to. 

as for samba accounts, on the server side, a samba user must be a unix user (or at least I've never seen anyone do otherwise) that has permissions on the linux filesystem that allow them to access the share. 
after creating and configuring the unix user, I add them to samba with a line like this:
```

sudo smbpasswd -a <username>

```that will add their unix password to the samba passwords database, and allow them login access to samba shares that are configured with permissions for that user.

---

### Post by Jethro_uk on 2010-11-24
> **endotherm said:**
> I think your issue is with more than samba, based on the HTTP 404 error. perhaps a traceroute from source to dest may help, since it is a vpn tunnel.


on the server side, a samba user must be a unix user (or at least I've never seen anyone do otherwise) that has permissions on the linux filesystem that allow them to access the share. 
after creating and configuring the unix user, I add them to samba with a line like this:
```

sudo smbpasswd -a <username>

```

that will add their unix password to the samba passwords database, and allow them login access to samba shares that are configured with permissions for that user.

No, you misunderstand. It's not a 404 error I get. It's "IE is unable to connect" implying there's no port 80 traffic either.

I have my samba share set up to allow read-only access to everyone. When I connect to \\192.168.1.20\MyShare from the LAN, it prompts for usename ("guest") and blank password and works fine. So I know samba is working OK. It's just accesing it via pptp that is failing.

---

### Post by endotherm on 2010-11-24
> **Jethro_uk said:**
> No, you misunderstand. It's not a 404 error I get. It's "IE is unable to connect" implying there's no port 80 traffic either.

I have my samba share set up to allow read-only access to everyone. When I connect to \\192.168.1.20\MyShare from the LAN, it prompts for usename ("guest") and blank password and works fine. So I know samba is working OK. It's just accesing it via pptp that is failing.
your right, server not found is bigger than page not found, but that reenforces my initial point: the problem is with IP, not with higher layer services.

---

### Post by Jethro_uk on 2010-11-24
MUPPET ALERT !!!
MUPPET ALERT !!!
MUPPET ALERT !!!

10.1.2.3 is MY IP address !!!!!!! Of course I can't access it (since I have no shares set up)

OMG, what a class A pillock.

So the question is, what is my SERVERS IP address on the pptp tunnel ?

---

### Post by Jethro_uk on 2010-11-24
More info

disabling firestarter gets everything working. Looks like a port forwarding issue ...

---

### Post by Jethro_uk on 2010-11-24
More info

disabling firestarter gets everything working. Looks like a port forwarding issue ...

---

### Post by Jethro_uk on 2010-11-24
More info

disabling firestarter gets everything working. Looks like a port forwarding issue ...

---

