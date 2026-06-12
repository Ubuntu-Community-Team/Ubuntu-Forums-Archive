---
title: "rtorrent killing network whether downloading or not"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by tbridges42 on 2011-07-08
Technically this isn't a Ubuntu issue, but I'm hoping to find more knowledgeable, friendly people here.

Here's the deal: I use Ubuntu 10.04 server as a base for my media center, with rtorrent as my download program. I've had to move into a smaller place where I don't have direct control over the network, and where we have a vanishingly poor DSL connection. When I start up rtorrent, every computer on the network starts having dramatic slowdowns of internet speed, even when both my downloads and uploads are throttled to 1KBps, which is as low as rtorrent will go.

Unfortunately, as I said, I don't have direct access to the router. The IT guy says my media center "is sending requests to all the computers on the network like crazy". How he knows that, I don't know, nor do I know exactly what he means. But it is only when I have rtorrent running, even when it's only running 1k each way.

It was my intention to test whether or not running utorrent on my Windows box had the same effect, but it's telling me "an attempt was made to access a socket in a way forbidden by its access permissions" on all trackers, which I've also been unable to resolve.

It may or may not be symptomatic of the same issue, but the UI of rtorrent is painfully slow. As in, I push the down arrow, go make myself a sandwich and watch some telly, and maybe when I'm done it's selected the next torrent.

I used to use Transmission, but it used more resources and interfered with watching shows. I had network problems with it also, but I don't think they were as bad.

---

### Post by tbridges42 on 2011-07-09
Updates: I used to use deluge, not transmission.

On my Windows box, same network, I got utorrent working, the solution turned out to be reducing my number of half-open connections. With half-opens at 8, utorrent downloads beautifully at 60KBps without interfering with my network at all, so it is definitely some problem with rtorrent/ubuntu/my settings on my media center.

Any ideas at all? From changing random settings to changing CLI clients, I'm willing to hear it.

---

