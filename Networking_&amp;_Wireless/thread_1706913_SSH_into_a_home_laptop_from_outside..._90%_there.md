---
title: "SSH into a home laptop from outside... 90% there"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by emmiesix on 2011-03-14
I have a home laptop running Mint 8.  I would like to ssh into it from the outside world.  My home network is first a DSL (2wire) router connected to a Belkin wireless router.  I have set up a dyndns account which points to the public IP which obviously I guess is talking to my DSL router first. 

Canyouseeme.com says that port 22 is open for the public IP (but strangely, not port 80).  I went into the DSL router and set up the firewall to allow port 22 traffic to the Belkin router (or rather, the only "device" listed which I assume is the Belkin router).

I went into the Belkin configuration page and also allowed forwarding of outside port 22 traffic to the internal IP that my laptop is on.

I enabled port 22 on the laptop (verified with nmap -p22 localhost).

But of course, when I try to SSH to the public IP, I'm not getting through (it just times out).  I'm having trouble figuring out where the break is.

Are there any other firewalls that could be acting to cause this?  Am I missing something obvious?  I feel like I'm almost there...

---

### Post by emmiesix on 2011-03-14
Ok, I'm a little slow with networking stuff, so it just occured to me to try:


```
nmap -p22 192.168.2.1
```

that IP being the gateway of the Belkin router.

I got 

```
Starting Nmap 4.76 ( http://nmap.org ) at 2011-03-14 14:48 CDT
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Illegal character(s) in hostname -- replacing with '*'
Interesting ports on ***************** (192.168.2.1):
PORT   STATE  SERVICE
22/tcp closed ssh

Nmap done: 1 IP address (1 host up) scanned in 0.21 seconds
```

I have gone back to the Belkin router and turned off the firewall completely.  Still not getting through?

---

### Post by kvarley on 2011-03-14
> But of course, when I try to SSH to the public IP, I'm not getting through (it just times out). I'm having trouble figuring out where the break is.

If you try to connect to the external IP address from within the network which your host is on it won't work. If you are on the same network as the host box then you must use the internal IP address of the box. When you are on a different network it should work when you use the external IP address.

---

### Post by kevdog on 2011-03-14
Can you ssh localhost from the server to itself? You can always do a tracert to see where its getting blocked. (up to a point).  And you can consult the ssh logs on the server itself to see if an authentication token was processed.

---

### Post by Perfect Storm on 2011-03-15
Hi emmiesix

There's a Linux Mint forum to get help with your distro.
You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---

