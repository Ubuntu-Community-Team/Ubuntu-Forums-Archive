---
title: "VPN only under specified conditions"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by goblinlord on 2009-07-28
Hello,
  I have set up a VPN for use with my laptop when I am out and about.  What I want to do is have it detect if I am on my home network and if not then automaticly attempt to use my VPN.  Otherwise, I would like it to not use it and just use the normal connection.  Is there a simple way of doing this?  Both my main computer at home running the VPN server and my laptop are running linux.

  I was thinking a script could do the job... but I am not exactly sure where to put it so that it does this after the initial network connection is made but before it makes any attempt to connect to the VPN.  Also, not exactly sure how to check which network the network manager is using.

---

### Post by goblinlord on 2009-08-07
I came up with a method and now need only to implement it (considering it seems nobody can help me =/).  I will make a set of scripts for making/modifying a list of "safe" networks.  I will ID the network by getting the MAC address of the gateway.  On the post-ifup script for network manager I will make it start my script to check the current network against the list of safe networks.  If on a network that is not marked as "safe" then I will have it attempt to connect to a VPN.

---

### Post by kg84 on 2009-08-07
> **goblinlord said:**
> I came up with a method and now need only to implement it (considering it seems nobody can help me =/).  I will make a set of scripts for making/modifying a list of "safe" networks.  I will ID the network by getting the MAC address of the gateway.  On the post-ifup script for network manager I will make it start my script to check the current network against the list of safe networks.  If on a network that is not marked as "safe" then I will have it attempt to connect to a VPN.

Exactly what I was thinking when I read your first post, but I dont have the understanding of scripting to be able to compose it.

Please post back with your result. I and others (no doubt) will be interested to see what you come up with :)

---

