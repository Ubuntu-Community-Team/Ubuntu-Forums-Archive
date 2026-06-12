---
title: "Load balancing"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by yaru on 2012-01-23
Hi all!
My situation might sound a little bit funny but I'm behind a connection that's capped @ 33.3 KBps per IP/MAC address but I can get as many IPs as I want from the access point.
What I have been doing so far is that I had Backtrack (based on Ubuntu 10.04) installed in VMware and had created 10 ethernets and set them all in bridged mode and then set up split access as explained here:

```
http://lartc.org/howto/lartc.rpdb.multiple-links.html
```

Then I used aria2 to download a different file from each interface, getting 33.3 KBps from each ethernet and 333 KBps in total. Of course I would have preferred if I could use the instructions in the load balancing section of that guide so that I could use all of the ethernets for downloading one file and didn't have to download 10 files simultaneously but further research indicated that load balancing is impossible in my case because all of the ethernets are connected to the same gateway; thus I stopped looking further.

A few days ago I decided to ditch Backtrack for downloading (because all of its non-pentesting related packages are out of date) and downloaded and installed Kubuntu 11.10 and repeated all of the above. Yesterday I noticed that some of my downloads are going faster than the usual 33.3 KBps, thus I stopped all except one and noticed that the downloading speed of the remaining download went up to 100 KBps. Then I increased the number of connection from 3 to 5 and noticed that the download speed went even higher than that. Then I switched to axel with 20 connections and to all my surprise, the download speed went up to exactly 333.3 KBps!
What I thought at that time was that the new kernel must have been performing load balancing over the existing ethernets from the beginning but I hadn't noticed because I wasn't paying attention but since I had to go somewhere, I just made a screenshot from the routing table (why didn't I make a snapshot from the VM, just why?!) and shut down the VM. Needless to say, when I started the VM again today, I noticed that not only there was no load balancing anymore, I couldn't repeat the same situation as yesterday no matter what I tried either. The only thing I remember doing yesterday, apart from the usual stuff, was that since one of my ethernets was dropping all the ping packets, I changed its MAC address from inside the VM and then got a new IP from the DHCP server and reran the script I have made to automatically run the commands needed for split access based on the above mentioned guide and that was all.

Here is the screenshot I made from the routing table:

[IMG]http://photoserver.ws/images/am1k4f1dac756637b.jpg[/IMG]

I desperately tried to recreate the same routing table and I did, but it didn't result in automatic load balancing. Heck there is nothing specific in the routing table that would show why I was getting automatic load balancing anyway.

So, now I'm wondering what I had done yesterday that load balancing was automatically being performed without me even trying but now it doesn't? Funny thing is, I use aria2's "--interface" switch to force it use a different ethernet for each download but even with that switch, it was still simultaneously downloading from as many ethernets as it could make connections through. :confused:

---

