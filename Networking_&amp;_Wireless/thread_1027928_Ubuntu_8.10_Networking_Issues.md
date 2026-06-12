---
title: "Ubuntu 8.10 Networking Issues"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Trithious on 2009-01-01
I'm running Ubuntu 8.10 on a Dell Inspiron 5100 Pentium 4 processor at 2.4GHz with 786MB of RAM. 

My problem is that the network manager doesn't even recognize my internet from the cable modem, but when I did this with Ubuntu on my iBook G4 Powerpc it recognized it perfectly so I could do updates and activate my wirless card. So when I go to System > Administration > Hardware Drivers it is blank, but when I say Try Ubuntu without installation and go to System > Administration > Hardware Drivers the driver I need is there which is a 

Broadcom B4legacy wireless driver

and the only way to activate it I'm assuming like I did for my iBook that I need to do for my Dell is connect through the wire update my drivers and then I'll have wireless internet, but how can I do that if that actual OS won't connect to the wired netowrk?

Help and yes I'm a newbie.

---

### Post by stderr on 2009-01-01
Does it help if you do System->Preferences->Network Configuration, and under Wired do Add, and click OK, then reboot?

Failing that, could you post the contents of your /etc/network/interfaces file?

---

### Post by stream303 on 2009-01-02
It almost sounds like your cable modem account is tied to the mac-address (hardware address) of your Apple's network card.  Did you initially set up your cable-modem account with the Apple with OSX?

This is more of a generic networking issue, that may be solved faster in the networking forum, and I'm no expert when it comes to cable modems.

What you might want to do if that is the case, is to see if your isp will allow you to use a router, and use the router's mac-address as the contact point for the account.  That way you can run whatever you like behind the router without being limited to a single machine.

In addition, most routers include a firewall.  I won't start the controversy over running a firewall with a linux setup that has no services to offer/exploit, but one thing about firewalls is usually never mentioned in this case:  Performance.  I run the router's firewall even though I don't have any services of importance just so that my system won't even respond to nefarious sweeps, rather than tying up my networking with "go away - there's nothing here of interest." :)  This may be especially true on a cable-modem setup where you share bandwidth with the other users from the get-go.  See the networking forum for the huge amount of pros/cons of firewalls.  I only run it for performance reasons - be it in the router itself or by setting up the linux firewall with firestarter or even the simple Lokkit.  In my case with no services of interest, a firewall is like putting up a "no solicitors allowed" sign.  My networking card never has to leave the couch. :)

This is also the easiest way for dsl-users with only a single machine to not have to hassle with pppoe or pppoa software - use a router between either the cable or dsl modem, and let it handle the pppoe stuff, and that lets you use just the basics of networking for any machine you decide to attach, even if it is just one machine.

---

