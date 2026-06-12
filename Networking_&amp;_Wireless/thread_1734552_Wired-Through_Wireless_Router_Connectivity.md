---
title: "Wired-Through Wireless Router Connectivity"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by nfoglesbee on 2011-04-20
[IMG]file:///F:/nfoglesbee.png[/IMG]I've been fumbling around for a few days now trying to solve this.

My setup is a cable modem (ISP=DCHP) directly linked into my DLink Wireless Router that I run everything in the house off of except for my Desktop.

Desktop runs Ubuntu 10.10 and plugs into the back of the DLink into a LAN Ethernet port.  I have never had issues with it operating prior, but this is my first installation of Ubuntu on this tower.

When I first installed, I could only run in Safe Mode and had to change the kernal to nomodeset.  The network didn't work before or after.  Checked all the cables and tested them with my laptop (worked fine).

The network wouldn't connect to anything.

I went into my router, and set a DHCP reservation for a static IP for the tower, and now I am "connected" ...but it seems only to the router - I can't reach out.  I can't even ping Google.

I attached a picture of my "ifconfg" and my "lswh" in addition to "connection information" and the "IPv4 Settings" on that connection. Hopefully this will help...

I'm sure it's something simple I am consistently overlooking.  Any help I would greatly appreciate.  I'll be online again in a few hours.

---

### Post by prankstar008 on 2011-04-20
Can you actually ping the router?

---

### Post by nfoglesbee on 2011-04-20
Yes, I've been able to ping my wireless router (haven't tried to ping the cable provided one yet).  That seems like the logical next step, will try when I get off work.  I haven't been able to ping google.com or anything beyond though... and the wireless is connected - I haven't had any issues with my wireless devices around the house, they still have internet.

---

### Post by perspectoff on 2011-04-20
Try adding the router's own address as a DNS server: 192.168.0.1

If that takes care of your problem then the problem is accessing the DNS servers.

If your router is assigned an IP (for the router/LAN) by DHCP from your ISP, it should be given the DNS for your ISP as well. 

Sometimes routers hiccough when trying to access 3rd party DNS servers.

Might not be your problem, but it has been for me in the past and that solved it.

---

### Post by nfoglesbee on 2011-04-20
Thanks!  I will try that first.  Come to think of it when I was rooting around in that Dlink I noticed there was an option on forwarding DNS...  I have it listed as the primary gateway - that won't affect anything will it?  Can you have your DNS and your gw be the same?
 
I'll get back with you all as soon as I get the chance to try this stuff out.
 
I appreciate the help.

---

### Post by nfoglesbee on 2011-04-20
Okay, changed the DNS to the router (see attached) and it's still not working...  Websites just time out, can't connect to anything on FF.

---

### Post by brpylko on 2011-04-20
I may be mistaken, but it looks like you have the Dlink and Machine address set to the same thing.

---

### Post by nfoglesbee on 2011-04-20
Nah, I've got my machine's addy set static at (ending) .199 and the router's addy ends with .1
They're different - the router is tracking my address as a static reservation (the rest of my network is dynamic).

---

### Post by BertN45 on 2011-04-20
You said you could not ping Google, did you use the IP address or the WWW address, else try 8.8.8.8.

If it is a DNS issue, I had the same occasionally. For a longer period of time my DNS service would not be available due to a hick-up in DSL modem or router. Switching those off for 10 seconds helped. But nowadays I use the following DNS servers from Google, bypassing all intermediate stations. I use for DNS server 8.8.8.8, 8.8.4.4, and as third the address of my router.

I hope it helps, since you network settings seem OK to me, they are the same as mine.

---

### Post by nfoglesbee on 2011-04-20
Shouldn't be a DSL issue, I'm running off cable.

Just tried the DNS advice... didn't work either.  Thanks for the help anyways.  I can't seem to go beyond my router - I'm going to triple-check my Dlink settings tomorrow.

---

### Post by perspectoff on 2011-04-21
No firewalls in the way, right?

---

### Post by nfoglesbee on 2011-04-21
I went back into my wireless and looked over some settings (attached).  I placed an exemption for the desktop on the Dlink firewall ("Capture3" attached), and added all of the DNS addresses suggested (plus some).

Still nothing.

If there is some information I'm not providing that would be beneficial in pin-pointing the problem please let me know.

Thanks for all the help guys - not quitting yet.

---

### Post by nfoglesbee on 2011-04-21
Okay, this might be important.  It seems I lied to you in Post#3 or something has changed.  I'm not able to ping the router.

Additionally, under the Network Connections I added the MAC address of the router to "Auto eth0" and it popped up *another* wired connection "Auto Ethernet".

I can't seem to delete Auto Ethernet from the Network Connections - it won't go away, and it doesn't even show that a connection is established (cf. Auto eth0).

Auto eth0 will show an established connection (only when assigned a static IP), but still won't connect to anything and I can't ping the router - which I'm assuming is what it's supposed to be connected to.

I can ping the router from my laptop, but not the desktop.  The desktop won't ping anything "Destination Host Unreachable".

I'm afraid I may have misrepresented the problem earlier by stating that I could ping the router.  I'm unsure myself what happened... not getting the right amount of sleep I guess.

---

### Post by nfoglesbee on 2011-04-25
Okay, back from the Easter break...

I've still got no new ideas.  I tried fooling around some more with it this afternoon - no luck.  I'm wondering if maybe it's some kind of a driver issue.  How would I go about checking on that?  Or updating for that matter (without a network connection)?

Also, here are some more shots to show where we're at:

Screenshot 1 shows my network hardware(lshw), ifconfig, and connection information.
Screenshot 2 & 3 show my connection settings (ethn0 & Auto Ethernet are the same).

---

### Post by nfoglesbee on 2011-04-27
Found an application that will allow me to download updates & software:
[http://keryxproject.org/](http://keryxproject.org/)
It's really cool - I'm in the process of downloading all the updates to 10.10 if that doesn't solve the issue... I suppose then I will just install the new version (Ubuntu 11), reset the router, and hope for the best.

---

### Post by nfoglesbee on 2011-04-28
No solution, moving on.

---

