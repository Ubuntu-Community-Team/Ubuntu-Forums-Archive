---
title: "Anyway to Kill Apache ...please....for network testing?"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-04-25
I'm trying to kill our apache server at work for some security testing and prevention method creation.  I'm not the system admin....technically I'm the web engineer.  But I'm playing the white hat against the network guy who's playing the black hat.  

We have both a testing network and a management network.  Somehow he's managed to take down the entire network using the test network with a simple syn flood.  But with Hulk and UDP he can't kill Apache.  I'm mildly questioning whether he's truly attacking the Apache Server like he says he is.  The other day I ran 'Kill Apache' but our Apache has the patch that fixed that vunerability.  So today I ran Tor's hammer on it, a slow DoS on about 4 bots with 5,000 threads a piece.  I noticed major lag on the graph I use that uses ajax calls to the network and then displays if the response is successful.  According to said graph, the server was basically down.  I used Firebug to take a look at the network calls and either they were '404' or they were delayed horribly.  But according to the graph that my partner is running (through ssh over the management network) there are spikes in the connectivity in between no connectivity (on average about every 5 seconds there's a little spike with the longest interval between connections being about 30 seconds).   So I'm mildly concerned this guy 'tuned' his monitoring graphs to die on his own attacks but when another attack is running the truth of it kind of is revealed.

So with all that in mind, I'm trying to find a sure fire way of bringing down the apache server.  As I said I've tried Kill Apache which didn't work.  Then I tried Torshammer which seems to work but my network guy is saying it doesn't.  Then I tried a combination of Torshammer with a UDP Flood and still nothing.  So does anyone have a sneaky way to effectively shut down an Apache server?

---

### Post by Warren Hill on 2013-04-25
One thing you could try on the local network is to put another machine on the same static IP address as the Apache server has.  Should confuse things enough.

However, this is not a real world attack as it could only be done by someone with physical access to your network; i.e. part of your organisation.  

If your network manager has not given you permission to do this however it may get you fired.

It will be easy to detect its local and find MAC-ID of computer with the duplicate IP address

---

### Post by psyllex on 2013-04-25
Well essentially both my partner and I have free reign over our network.  It was made by us strictly to run attack simulations on so we can do just about anything but we would like to keep it in the realm of a real world attack if possible.

---

