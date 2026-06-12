---
title: "Torrent client with port range selection"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by arcull on 2011-11-08
Hi everyone. I'm searching for a torrent client which has the capability to specify the incoming and outgoing port ranges and DOESN'T use any additional random ports. It should run in ubuntu, if it has also windows version even better. A fixed port range would allow me to limit traffic on router via QOS without L7 filters. Till now I found Deluge would quite fit my needs, but it has a major drawback, this is, that it auto adjusts down speed accordingly to your specified up speed. I have a ADSL line, whose upload capability compared to download is very very small, therefore I can not afford to allow the torrents to use a lot of upload. Any suggestions welcome thanks.

---

### Post by satanselbow on 2011-11-08
> **arcull said:**
> but it has a major drawback, this is, that it auto adjusts down speed accordingly to your specified up speed. I have a ADSL line, whose upload capability compared to download is very very small, therefore I can not afford to allow the torrents to use a lot of upload. Any suggestions welcome thanks.

We (nearly) all suffer that :( But that is not how deluge behaves - ie shaping down traffic with regards to up traffic. Your torrents may appear to slow down with a very low up speed but this is more due to seed availability/# of connections and the fact that the handshaking takes that much longer with little up speed and so you lose downward peer traffic (ie they look elsewhere for someone more willing to accept the traffic)

What percentage of your available upload speed are you making available to deluge. Somewhere between 50 - 60% is about right (regardless of torrent client) for example:

If your tot avail up speed = 50kbps
Set torrent client max up = 25kbps

Setting the available up speed any higher will "choke" your connection - you will also have a reasonable bit of bw left for surfing / email etc ;)

I don't know of any torrent clients that offer you a range of ports to connect on. This is by design as you only ever need 1 (per client).

There is nothing stopping you using 2 clients to download with port forwarding set to 1 port each which needs to be set up on your router admin panel eg:he net if you  

deluge: 50505
qbitorrent: 50506

Using something in the 50000+ port range is usually good as they are largely free of other uses and unlikely to be blocked by your ISP.

Google your particular brand of router on how to set up port forwardiung correctly ;)

---

### Post by arcull on 2011-11-08
> What percentage of your available upload speed are you making available  to deluge. Somewhere between 50 - 60% is about right (regardless of  torrent client) for example:

If your tot avail up speed = 50kbps
Set torrent client max up = 25kbps Thanks for reply. My up speed is about 500kbps, currently with two computers each assigned cca 100kbps of upload, together resulting about 40% of upload speed.> I don't know of any torrent clients that offer you a range of ports to  connect on. This is by design as you only ever need 1 (per client).
 Well infact Deluge has the ability to define out/in ip ranges. Maybe to establish the connection you need just one, don't know, but for instance when using microtorrent I noticed on the router a bunch of connections on other ports different from the one specified in settings```
cat /proc/net/ip_conntrack
```, that's why Deluge seems a better choice, but has the problem with auto assigning down speed :(

---

### Post by satanselbow on 2011-11-08
> **arcull said:**
> Well infact Deluge has the ability to define out/in ip ranges.(

You are correct - I haven't used deluge in a while ;) It will only use one inbound port from your range per session.

I can't see anything in the settings that would cap your download speed however - some torrents just don't run at full throttle... if you've got 100 peers sharing at 1kbps each - you've only got 100kbps which is not quick by todays standards :(

---

### Post by arcull on 2011-11-09
satanselbow thanks, I'll try to tweak the settings of deluge (wider, narower port range) and monitor traffic on my router.

---

