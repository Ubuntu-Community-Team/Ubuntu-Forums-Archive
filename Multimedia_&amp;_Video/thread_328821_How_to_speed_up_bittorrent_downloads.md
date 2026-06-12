---
title: "How to speed up bittorrent downloads?"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by Ted_Smith on 2006-12-31
Hi

I am trying to download a few videos using Ubuntu's default BitTorrent app gnome-btdownloader. 

However, I seem to be getting very slow download rates even using high seeded files. Speeds of around 0.6Kb are about the average instead of the 50 or 60Kb+ one would expect. 

I have added a Port Forwarding rule in my router to port 6882 (also tried the default 6881). But speeds seem to tbe the same. It's a D-Link DSK-G604T router if that helps? How can I fix this? 

Also, I tried installing the [www.bittorrent.com](www.bittorrent.com) DPKG Linux package, but I got these errors : 

```

sudo dpkg -i bittorrent_5.0.3_python2.4.deb
Password :
(Reading database ... 175246 files and directories currently installed.)
Preparing to replace bittorrent 3.4.2-6ubuntu2 (using bittorrent_5.0.3_python2.4.deb) ...
Unpacking replacement bittorrent ...
dpkg: dependency problems prevent configuration of bittorrent:
 bittorrent depends on python-wxgtk2.6; however:
  Package python-wxgtk2.6 is not installed.
 bittorrent depends on python-twisted (>= 2.0); however:
  Package python-twisted is not installed.
 bittorrent depends on python-psyco; however:
  Package python-psyco is not installed.
 bittorrent depends on python-zopeinterface; however:
  Package python-zopeinterface is not installed.
dpkg: error processing bittorrent (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bittorrent
ted@mainunit:~/Downloads$

```

How do I fix the dependancy issues? Any help warmyl received

Thanks

Ted

---

### Post by skale on 2006-12-31
First, there is ( I believe) a btdownload<something> somewhere.  to eliminate the gnome-bittorrent as the problem, go to a terminal and type `btdownloadcurses /path/to/file.torrent`  Make sure the filename is right.  If the speed is better, then problem solved.  If not, try to set the IP address of your computer as the "DMZ host".  I have no idea how to do it with your router, though.  

Finally, maybe the download is just that slow.  I usually expect around 10Kb/sec.  It depeds more on the connection and settings of the other peers.  Just let it run for a few days.

---

### Post by Ted_Smith on 2007-01-01
Thanks for your help. I tried 'btdownloadcurses /path/to/file.torrent` but it said command not found. 

A few have speeded up since yesterday but only to about 2Kb for a file with about 60 seeders. I would have expected it to be much quicker in that intance . 

Can anyone help with the dependancy issue described in first post? I'd like to get that bit torrent client working if I can.

Thanks

Ted

---

### Post by nitrox027 on 2008-05-09
im only dling at about 23kbps which is really slow for me it is a high speed file and i don't know why its going so slow my usual dl speed is between 80-1000 kbps any ideas why?

---

### Post by Bölvaður on 2008-05-09
change the port your torrent program listens to. put the port number to much greater number like 45000.

*added*
And also choose to encrypt your data transfer so your isp is less likely to choke your p2p data transfers.

---

