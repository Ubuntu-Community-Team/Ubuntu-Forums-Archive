---
title: "Very poor bittorrent speed"
date: 2008-12-25
forum: Multimedia Software
---

### Post by puzzlefreak on 2008-12-25
Hi,

My laptop has recently been having ridiculously slow speed downloads when it comes to bittorrent. At this point I have no idea what the problem is. I've tried changing the port forwarding, and Transmission is telling me "Port is open". I've tried several different clients, all to no avail. Everything I try to download experiences the same problem, so I don't think it's a matter of seeds/peers. Earlier I was getting download speeds from 200-400kB/s, and now I'm hovering around 0.5/1 kB/s.

Anyone have any idea what my problem is? Any help would be very much appreciated.

-Puzzlefreak

---

### Post by puzzlefreak on 2008-12-26
Help would be very much appreciated.

---

### Post by ugm6hr on 2008-12-26
> **puzzlefreak said:**
> Earlier I was getting download speeds from 200-400kB/s, and now I'm hovering around 0.5/1 kB/s.

If your ports / firewalls are configured correctly, and all clients report the same behaviour, the most likely reason is that your ISP is throttling your download speeds.

Try asking them.

---

### Post by mb_webguy on 2008-12-26
Several things can affect bittorrent download speeds, and since I don't know your knowledge level, I'll start with the basics.

First, when you select a torrent to download, look for one with a high seed-to-leech ratio.  A high number of seeds assures that the files will be available for downloads, but not that you'll get a good download speed if the number of leeches is even higher.  So if you have a choice between a torrent with 1000 seeds and 2000 leeches and another with 250 seeds and 50 leeches, the latter, with a lower number of seeds but a higher seed-to-leech ratio, will likely download faster.

Second, if you're behind a router, your downloads will be slower if you don't have port forwarding set up correctly.  Some routers call this setting up a "virtual server".  Since you mentioned that you checked to make sure that the ports are open, I probably don't need to go into any more detail on this point.

Third, slow download speeds could be due to your router being overwhelmed by the traffic being placed upon it by your bittorrent client.  If your web browsing slows to a crawl after you've been downloading a few torrents for a while, this might be the case.  The solution is to adjust your client's settings (such as max download speed, max upload speed, max connections, max connection attempts per second, and max half-open connections) downward until you start getting better performance.

Fourth, it could be your ISP throttling the download.  You can do a few things that might help, such as changing the ports used by your client and enabling encryption (if your client supports it).  Particularly nasty ISPs will block or place limits on all but a few "approved" ports, and others simply reduce your download and/or upload speeds for a while (usually 12 or 24 hours) if they exceed a certain level over a certain period.  Unfortunately there's not much you can do about these two situations except to switch to a more customer-friendly ISP.

Finally, there are a few things that can contribute to a slower download speed but aren't likely to be the major culprit.  A few trackers are modified to only seed members and leech from everyone else.  Also, some of the anti-pirating organizations (e.g. MPAA, RIAA, etc.) set up "trackers" that do the same but for information-gathering purposes.  The latter can be avoided by using blocklists (if your client supports them).  For the former, blocklists may also help, and users of torrent search sites will often alert others to the presence of greedy trackers in the comments for the torrent .  If you see such comments, edit the trackers for the torrent and remove the suspicious entry.

---

### Post by puzzlefreak on 2008-12-26
> **ugm6hr said:**
> If your ports / firewalls are configured correctly, and all clients report the same behaviour, the most likely reason is that your ISP is throttling your download speeds.

Try asking them.

I'm absolutely sure that the ports are configured correctly, and I'm fairly sure that my firewall is not the cause. I will look in to the ISP issue.

> **mb_webguy said:**
> 
First, when you select a torrent to download, look for one with a high seed-to-leech ratio.


I've tried several different files, all exhibit very slow downloads.

> 
Second, if you're behind a router, your downloads will be slower if you don't have port forwarding set up correctly.

This is set up correctly.

> 
Third, slow download speeds could be due to your router being overwhelmed by the traffic being placed upon it by your bittorrent client.  If your web browsing slows to a crawl after you've been downloading a few torrents for a while, this might be the case.  The solution is to adjust your client's settings (such as max download speed, max upload speed, max connections, max connection attempts per second, and max half-open connections) downward until you start getting better performance.

My internet browsing remains unaffected, and I can directly download files fairly quickly. It's only bittorrent that has the problem.

> 
Fourth, it could be your ISP throttling the download.  You can do a few things that might help, such as changing the ports used by your client and enabling encryption (if your client supports it).  Particularly nasty ISPs will block or place limits on all but a few "approved" ports, and others simply reduce your download and/or upload speeds for a while (usually 12 or 24 hours) if they exceed a certain level over a certain period.  Unfortunately there's not much you can do about these two situations except to switch to a more customer-friendly ISP.


[From what I found,]("http://azureuswiki.com/index.php/Bad_ISPs#United_States_of_America") My ISP (Cablevision's Optimum online US) "Prevents seeding". While I'm not entirely sure, I doubt this could limit download speeds.

> 
Finally, there are a few things that can contribute to a slower download speed but aren't likely to be the major culprit.  A few trackers are modified to only seed members and leech from everyone else.  Also, some of the anti-pirating organizations (e.g. MPAA, RIAA, etc.) set up "trackers" that do the same but for information-gathering purposes.  The latter can be avoided by using blocklists (if your client supports them).  For the former, blocklists may also help, and users of torrent search sites will often alert others to the presence of greedy trackers in the comments for the torrent .  If you see such comments, edit the trackers for the torrent and remove the suspicious entry.

I will look into this as well, thank you.

---

