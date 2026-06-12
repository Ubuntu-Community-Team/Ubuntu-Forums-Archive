---
title: "New Mythbuntu install, how should I set up IP address?"
date: 2010-01-04
forum: Mythbuntu
---

### Post by Monona on 2010-01-04
How should I set the IP address for my primary backend?  Right now, it is 127.0.0.1 for Local Backend and Master Backend.

This is for the backend that will host all my media files.  I'll be using this primarily for accessing music over the network with an Ubuntu laptop & desktop and a Macbook.

Also, can I set up my main desktop to dual boot into Mythbuntu and regular Ubuntu, or is it better to just have a MythTV user account and run the frontend once I'm logged in?

For the record, here's my specs (not top of the line, but it's what i got):

Mythbuntu 9.10 Desktop i386
40 GB 1.66 GHz AMD Athlon XP 2000+ 
1 GB RAM
300 GB External Hard Drive (where files will be stored)
NVIDIA GeForce FX5200

---

### Post by radnor on 2010-01-04
Here is what I have...

BE FIXED ip @ X.X.X.100
RFE FIXED ip @ X.X.X.102
RFE DHCP is @ X.X.X.150+
PS/3 (I think is DHCP) at 150+

on the BE, I took out the 127.0.0.1 and put in the actual ip
On the RFE(s) I put in the BE address of X.X.X.100.  It will want to ping it to make sure it can be reached.

I dont know about the macbook...  But your Ubuntu system I can comment on.  My 1st RFE listed is running mythbuntu FE only.  I could see my songs but NOT play them.  If I recall on the BE the folder is: /var/lib/mythtv/music.  I made the folder the SAME on my RFE.  But, in my fstab file I did a NFS mount of the BE's folder to the RFE folder.  Now I can play music on my RFE.  Will look for a post where it was described.

---

### Post by radnor on 2010-01-04
Will look at the lappy tonight for more info (I did not do the NFS map on it).  On the other RFE, I did and that is where I listen to the music files.

Get you little  more info later.

---

### Post by radnor on 2010-01-04
OK, just pulled out the lappy.  I (last night) just installed mythtv-frontend.  On the config, I added my BE's ip of 192.168.0.100.

TV plays fine.

Tonight, no mythmusic.  Why?!?  Cause, I did not install it.  So I did along with mythvideo.  We'll talk about mythmusic from now on since that is what you want to do.

Music shows up fine.  Edited a playlist (selected an album). NO JOY!  Would NOT play.

Added NFS support.

Edit fstab to include: "192.168.0.100://var/lib/mythtv/music	/var/lib/mythtv/music	nfs	defaults	0	0"

Saved it.  Restarted FE.  Went into MUSIC from menu and it started playing.

So this should work for you too.

-----------------------------------------------

Now, to get this working, I would....  Install a FE on the BE until you get it working.  Then introduce the RFE and then the Macbook.  You do not have to run the FE that is with the BE after you get the RFE(s) working.  As far as the Macbook, I do not have one to test it out for you.  I could use my son's but....

Be advised when getting into your library from the RFE, it will be mounted as RO.  If you wish RW, that is a MINOR change.

Keep us posted please.

---

