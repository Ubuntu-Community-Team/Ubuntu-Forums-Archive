---
title: "Limit internet use, but not network"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by untenops on 2009-10-01
Ok I got kind of a strange problem I need help to fix, please.  Here is my setup.  I have a router that is my DSL modem as well, and it has no provisions for limiting speeds.  Connected to it is my desktop, (XP sorry), a ubuntu 9.04 box that I use as a server, and a Linksys PAP, (this is a VOIP adapter.)  Usually things work fine, except when I'm using my VOIP, (calling home from work) and streaming music over the internet from my ubuntu server.  When this happens I get static on my VOIP when ever there is a streaming burst.  Today I thought I fixed this when I installed wondershaper and limited my ubuntu boxes upload speed.  Kewl, I was all happy, until I got home a tried to connect to my sever from my desktop, on the same network.  My upload speed was limited to 128kbs, great for jinzora2 re-sampled streaming music, but totally sux for a home network.  Is there anyway I can limits my ubuntu 9.04 on internet uploads but not on local network connections. 

Please help.

---

### Post by Littleweseth on 2009-10-01
It sounds like some of your VoIP packets are getting held up in the queue behind the burst activity of whatever else is on your network.

You may want to implement QoS (quality of service). QoS prioritises certain kinds of traffic (i.e. VoIP) so that it can 'jump the queue' ahead of everything else. QoS is commonly implemented using a Linux machine as a router.

It works thusly : set up your linux router, which has exclusive access to the internet. Your other computers then talk to your router whenever they want internet, and important packets (VoIP) jump the queue ahead of unimportant packets (mp3's.)

Network traffic continues to work as usual, because it doesn't go out over the internet and thus the router doesn't apply QoS.

Here's a list of router/firewall distributions that should all have QoS :
[http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions) . A crappy old computer (Pentium 133...) will do as a router.

I've heard good things about IPCop. If you don't have any old, crappy computers lying around, you can use your existing Linux box as the router... but that gets a bit ugly.

Hope this helps;
- L.

---

### Post by untenops on 2009-10-01
Thank you for the quick reply.  This is probably exactly what I need to do, but I was hoping for something a bit easier.  Something I could setup on my Linux box.  I would think there must be some way to limit speeds only over the Internet.  _Is there anyway to limit upload speeds to all ip addresses except the one or two ip addressed of my home computers?  _

---

### Post by badger_fruit on 2009-10-01
If you install an application onto a PC, it will restrict the traffic from that Network card to the router, not from the router to the internet.  The QOS has to be installed and configured from the router.

if you had a spare PC lying around, Smoothwall is a great little distro which will do all this for you in a nice easy to use GUI.

I suppose you could VM it on the linux box but it's not something I've ever tried.
My SW runs on a really low spec PC I had built out of bits I found around the house lol!

It works wonders, I have 20mb cable and with QOS can make sure my torrents are low priority and web-browsing is always "king" so to speak.



Oh as an afterthought, you could use Squid (proxy) software on the Linux PC but I'm far from experienced in that (plus, it comes on Smoothwall and is all configured through the same GUI!)

---

### Post by untenops on 2009-10-01
Ok after doing a little more googling and thinking, Ive come up with limiting bandwidth on just some of my linux box's ports, Namely 80 and 443.  Or maybe just one of those if I could remember which is used for uploading.  What is the best way to do this?  I read something about using squid and delay pools.  Is there any easy way to setup squid and put my web server behind it?  And then whats a delay pool?  How do I set them up?  Again please help.  Thank you.

---

### Post by badger_fruit on 2009-10-01
> **untenops said:**
>  Or maybe just one of those if I could remember which is used for uploading

You don't exactly upload via any particular port; say you're using Filezilla to drop a file onto a remote FTP site, you'd be transmitting via port 21.  If you were uploading a file through SSH, it would be port 22.

If you're uploading using a web-browser, say at imageshack,us, then it would fire up thorough port 80. If you're doing a secure upload via web-browser, then it would be port number 443.

> **untenops said:**
> Is there any easy way to setup squid and put my web server behind it? 

Squid would typically sit between your local network and the internet. All requests for any internet resource would be made through squid. Squid would cache those pages so you can load them in future quicker.

There is no really easy way to work with squid but they have a website so suggest you start there.
[http://www.squid-cache.org/](http://www.squid-cache.org/)

YOUR webserver would be on you local network, it would not need local users to go through it to reach it.
Visitors to the webserver would also not go through squid, it would hit your firewall and be directed there. Any data served from it would also not go though squid.

Wow, how many times have I said squid?!

---

### Post by untenops on 2009-11-05
ok new idea.  Maybe I can leave my VOIP adapter hooked directly to my router, also connected to my router my Linux server.  Now can I install a second Ethernet card in my server and hook this up to a second router, that my local network is hooked to.  Then my home network can still have full bandwidth but I can limit the bandwidth on the first Ethernet card that goes out to the internet.  My question is then, can I, and how do I get internet access to pass thru the Linux server, to my local network?

---

