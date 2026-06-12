---
title: "LAN Surfer to access Windows computers"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by sunnyengineeer on 2010-04-22
Hello,
         I was a Windows guy...but Im thinkng of completely switiching to Ubuntu,
But all of my friends are on Windows...We have a LAN of abt 100-150 ..

 [COLOR=Red]**Is there is any GUI software thru which I can see all the files which are being shared on the network by Windows PCs**
[/COLOR]
,I know abt Samba ...but that is only computer specific & also that is reverse way...& doing from command will be tiresome task for all PCs..

Thanks
Sunny Sharma

---

### Post by Iowan on 2010-04-22
Samba is still the primary interface for Linux-Windows. Offhand, I can't think of an alternative (not that there isn't one...)

---

### Post by capscrew on 2010-04-22
> **sunnyengineeer said:**
> ...Im thinkng of completely switiching to Ubuntu,
But all of my friends are on Windows...We have a LAN of abt 100-150 ..

 [COLOR=Red]**Is there is any GUI software thru which I can see all the files which are being shared on the network by Windows PCs**
[/COLOR]
,I know abt Samba ...but that is only computer specific & also that is reverse way...& doing from command will be tiresome task for all PCs..

Thanks
Sunny Sharma
If you are dealing with windows then you will always be using SMB to view what is available.

What makes you say that Samba.org has not dealt with being both a client and a server?  If set up properly the suite of tools from Samba.org will: Serve files :: Act as a client to request files :: Allow browsing of Network Neighborhood.  What else could you ask for?  Does it work?  Sure does.  I have both Windows and Ubuntu servers and clients.  All shares are visible and available on all hosts.

---

### Post by sunnyengineeer on 2010-04-22
Thanks for the reply & guidance...
        As u said,I searched a lot for SMB...& finally installed those packages which I was looking for..My problem is now solved..

Cheers for Ubuntu...

---

