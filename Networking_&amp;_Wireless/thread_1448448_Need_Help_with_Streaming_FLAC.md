---
title: "Need Help with Streaming FLAC"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by Loves SSH on 2010-04-06
Hi folks,

OK, I have a Ubuntu Server (9.10, all current updates) on my home LAN with Samba installed and configured to share a few directories.  In particular, I configured a directory to share my FLAC collection. I usually access my music either on my Macbook (10.6.2), or my dual boot Win 7, Karmic desktop (both with all current updates applied) using Songbird (also current). Regardless of what OS I'm in, I'm still having the same problem.

When I start a track, the music sometimes plays for a few seconds flawlessly, but then it'll start getting choppy, and the client will become unresponsive. Or, if I start to create a playlist without any music playing, it'll hang or crash after adding some tracks. 

I've Googled around on how to speed up Samba and I've modified the smb.conf file and added SND/REVBUF, read size, read predict, etc. and added the noatime to my fstab, but obviously the modifications didn't help.

My server is attached to a Linksys WRT54GL (G router, 10/100), set as a switch, which is connected to my Netgear WNR3500L router (N-Draft, Gigabit). My Macbook is connected to my Netgear router wirelessly, and my desktop is connected also to the Netgear router via Ethernet. The N router is set to run as N, the G as G. My Mac has a built in N wireless, and my desktop's Ethernet is Gigabit.

I've set both routers QoS for SMB ports to the highest settings. On the server, I've opened ports 137-139, and 445 TCP/UDP using ufw, after Googling the SMB ports, as well as opening said ports on my desktop and laptop, and routers.

I've also played around with Songbird's buffer, increasing it from the default 128k buffer, to 512k.

Strangely enough, streaming video with VLC works rarely with hiccups... 

I'm completely out of ideas now, anyone care to take a stab at this?

---

### Post by Loves SSH on 2010-04-07
Bump.

---

### Post by Loves SSH on 2010-04-08
After some testing, I think the problem is with Samba. I've tried other FLAC players, and I'm still having the same problem. 

I've also noticed than when I transfer large files, or numerous small files, Samba drops out for a second, or drops out to the point where I need to "sudo service samba restart" it. Still, I still get faulty streams, and disconnects. 

When I try to backup my files in Windows, sometimes I'll get errors about the network drive becoming inaccessible. I'll check "My Computer", and the drive I assign for my backups goes from green to red. If I click on my other shares, it'll go from green to red, and give me the same error. But, as I've said, the disconnects happens sometimes, and it only when I transfer large amounts of data, or alot of small files. I haven't fully tested if it's Windows by trying to replicate the same errors on my Macbook, or from within Ubuntu, but considering I have to restart the service, I'm certain it's Samba.

Help would be gratefully appreciated!! :)

---

### Post by HarryZontal on 2011-08-06
Having the same problem over gygabit lan, i.e. the choppy flac files. No other files types are choppy. Think this is a codec issue. Any help greatly appreciated.

---

