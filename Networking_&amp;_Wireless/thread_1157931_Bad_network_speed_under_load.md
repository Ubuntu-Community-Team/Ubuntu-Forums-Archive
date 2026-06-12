---
title: "Bad network speed under load"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by kripkenstein on 2009-05-13
I have two problems that seem related:

1. When I download a large file at max speed (like a CD image), it downloads at the max speed fine, but the internet connection becomes unusable for all other apps - everything else basically stalls, pages won't load in Firefox, etc. But when not downloading a large file at max speed, browsing the internet works ok. EDIT: This is **not** with bittorrent or anything like that - I'm talking about a normal HTTP download.

2. When playing an FPS (Sauerbraten), I get the following: I can ping the server before I connect to it, and I get something very decent like 100-200ms ping. Then I connect, and the ping gets worse and worse, up to 1000ms and 2000ms (note that I'm checking the ping here using 'ping' on the command line, just like I checked it before). Eventually - usually after 10-20 seconds or so - the ping is over 2000ms, and the server disconnects my game client. Once disconnected, I see the ping quickly go back down to 100-200ms, like before.

To me, it looks like the network doesn't do very well under load. In the first case it's a lot of download, in the second case I guess it might be doing a relatively lot of upload. Not sure though. Anyhow, this is very problematic as the computer is only partially usable like this...

Anybody have an idea, or see something similar?

---

### Post by kripkenstein on 2009-05-13
> **Ellen2 said:**
> For your first problem. Its natural that when you download a file (probably thru p2p networks) your downloading software is creating too many connections with other peers. And thats limiting your browsing speed. You have to set the throttle for your downloading software. Set it somewhat lower than maximum speed and your other software will start working.

Hi, sorry I wasn't clear before - this wasn't a bittorrent download, it's with normal HTTP downloads. That should be a single connection, I think?

---

### Post by Peter09 on 2009-05-13
The trouble is that this problem can lie in several areas

1. It could be your software on the PC
2 It could be your wireless card or wired card
3 It could be your router not being good at multi tasking
4. It could be a problem with your connection to the exchange
5 It could be your ISP (some ISP's actually limit your bandwidth when you are downloading something big).

Where do you start to test this - I suppose the first thing is to ask what happens on another machine connected to your router?

 Also what happens when you use someone else's installation with your machine?

---

### Post by kripkenstein on 2009-05-13
> **Peter09 said:**
> The trouble is that this problem can lie in several areas

1. It could be your software on the PC
2 It could be your wireless card or wired card
3 It could be your router not being good at multi tasking
4. It could be a problem with your connection to the exchange
5 It could be your ISP (some ISP's actually limit your bandwidth when you are downloading something big).

Where do you start to test this - I suppose the first thing is to ask what happens on another machine connected to your router?

 Also what happens when you use someone else's installation with your machine?
I don't have another machine handy to test with though... I was hoping there was some software stuff I could check first, on this machine, and maybe I'd get lucky, before I went out to get/borrow another machine somehow.

---

