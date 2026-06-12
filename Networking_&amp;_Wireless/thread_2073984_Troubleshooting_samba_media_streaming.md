---
title: "Troubleshooting samba media streaming"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by atconc on 2012-10-20
Hi

I have a box running 10.04 server x64 that I use as a central file server for my home network, it's main purpose is serving up media to various clients around the network.

The server is a core 2 duo, 4 gb ram, directly connected to the router (Asus RT-N66U) via a PC gigabit LAN card.  The machine has 2 raid 5's using mdadmn (6x 1TB and 3x500GB) + a couple of other drives for OS and backups.

The problem I'm having is when watching video streamed from a samba share I'm getting intermittent dropouts and freezes every few minutes.

I'm pretty sure the issue is on the server side as I'm getting similar issues with various clients - for example today I was watching a video using VLC on a windows 7 64 PC directly connected to the router via gigabit, the video froze and my bandwidth widget showed the data flow drop to zero for a few seconds.  It then recovered and carried on playing.

I have also been having issues with XBMC on ubuntu connected via 500mbit homeplugs - the log message is to the effect of "tried to get more data from the network but none was avaliable".  Similar issues on XBMC on apple tv2 over wifi too.

I've already tried updating the router firmware and reseting it's default settings but this doesn't seem to have cured it.


So onto my question - How can I go about troubleshooting this issue?  I've tried watching top, iotop and looking at /var/log/messages,  and dmesg but I can't see anything that looks relevant happening around the time the video freezes.  Any help with troubleshooting these glitches would be greatly appreciated as it's ruining my tv watching right now!

---

### Post by Charlie Freak on 2012-10-20
I've got the same issue. Same router as well - but I'm quite sure it's not related to the router, as the situation existed with my old router as well.
 
I've never been able to solve it, and just resorted to using a different machine with Windows 7 to stream all my video from.
 
I can stream 1080p for hours at a time from that machine (or this one with Win7 installed). But with Ubuntu, I can't even watch SD or 720p without constant hangups.
 
Sorry I can't help. Hopefully someone else can shed some light on this, as I'd love to get it fixed as well.

---

### Post by atconc on 2012-10-22
I seem to have made some progress here.  Not quite ready to say it's solved as it was an intermittent problem to start off with but since I made these changes I haven't had any more freezing so I'm living in hope...

What I noticed was that around the times of the freezes there were often errors in my /var/log/samba relating to CUPS (print server).  My linux box doesn't have a printer connected, nor does it do anything printer related, so I googled the error and followed through the solutions on on how to disable print related sharing.  To do this I added the following lines in  the [global] section of /etc/samba/smb.conf

```
load printers = no
printing = bsd
printcap name = /dev/null
disable spoolss = yes 
```

I also removed the [printers] and [$print] sections and tidied up some other duplicate entries I had in the file. 

Since making these changes everything seems to be working much better.  I was just able to watch several 720p blueray quality tv episodes that had previously been dropping every few seconds, whilst at the same time copy serveral GB of data to another machine over wifi.

if you don't need printing on your ubuntu box give this a try it might help!

---

