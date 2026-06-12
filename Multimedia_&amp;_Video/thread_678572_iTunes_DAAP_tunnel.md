---
title: "iTunes DAAP tunnel"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by trbabb on 2008-01-26
Hi--

I have a situation where I'm going back and forth between two houses, and I want my music to be accessible from both places. I have an Ubuntu server in house #1 with all my music and mt-daap running on it. This part is up and running and works fine. Ideally, I want to have some sort of secure tunnel to house #2 that will allow all the computers there to see my mt-daap server via iTunes. I have another (crappier) Ubuntu server at house #2 that I can use for this purpose.

I've found this tutorial:
[http://wiki.mt-daapd.org/wiki/SSH_Tunnel](http://wiki.mt-daapd.org/wiki/SSH_Tunnel)
and this thread:
[http://ubuntuforums.org/showthread.php?t=492293](http://ubuntuforums.org/showthread.php?t=492293)
but it seems like (?) neither of them are talking about having OTHER computers at the end of the tunnel see the source music collection. 

I have tried installing SSHTunnelClient and RendezvousProxy on my windows laptop, and I can indeed stream music from house#1 to my lappy at house#2. Other machines can see the proxied DAAP beacon, but cannot connect to it, even when my firewall is off. Ideally I want to avoid having to install those pieces of software on every machine in house#2, as 1) it's a pain and 2) there are people here who aren't tech savvy and won't want to deal with that.

I've also followed the "hard" instructions in that first tutorial on house#2's ubuntu server. The beacon is visible from other machines, but iTunes will not connect to it.

Is it possible to do what I'm describing? How?

 On top of it all, I'd like to permanently plug house #2 server's sound card into the main sound system and offer up some sort web interface for controlling playback. I've looked into Music Player Daemon, which looks like exactly what I need, except it apparently has no support for DAAP.  I think VLC offers the web controls too  (and I've tested this successfully on my windows machine. I will probably want to use the "no x" flavor of VLC, though, for the Ubuntu server). I've heard that VLC also offers DAAP support, but I am not sure how to set this up, especially for the "no x" version. Can anyone offer tips on this? 

Sorry for the gi-normous post, and thanks in advance!
-t

---

### Post by trbabb on 2008-01-29
bump?

---

