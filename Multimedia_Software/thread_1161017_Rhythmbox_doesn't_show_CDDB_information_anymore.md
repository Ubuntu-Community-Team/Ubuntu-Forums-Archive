---
title: "Rhythmbox doesn't show CDDB information anymore"
date: 2009-05-16
forum: Multimedia Software
---

### Post by perce on 2009-05-16
After upgrading to Jaunty (clean install in fact) Rhythmbox doesn't show CDDB information anymore, it seems to miss a plug in it was present in Intrepid

---

### Post by jsubl2 on 2009-05-17
I had this behavior also.  try installing cddb and tools.
sudo aptitude install cddb python-cddb

---

### Post by perce on 2009-05-18
Thank you,

unfortunately I have them both already installed, but CDDB data still don't work.

---

### Post by perce on 2009-05-19
Bump

---

### Post by lorebett on 2010-10-25
Unfortunately this is true also in Maverik... any idea please?

---

### Post by Cavsfan on 2010-10-29
> **lorebett said:**
> Unfortunately this is true also in Maverik... any idea please?

Have you tried installing the rhythmbox-plugins from Synaptic?

I know some of my older CDs that I have ripped do not pull up CDDB info.
But, I found that Ripoff (available through Synaptic) can lookup the CDDB info over the internet while you rip a CD.

Hopefully this will help.

---

### Post by Cavsfan on 2010-10-29
Also, I was looking for a way to pull the CDDB info after a CD has been ripped to MP3 files and went into Synaptic and entered CDDB in 
the search bar and installed these packages **cddb python-cddb libcddb-get-perl libcddb2 libaudio-cd-perl libcddb-perl **

I was playing a song with Rhythmbox and there was no album art. I installed the stuff mentioned above and while I was looking around for 
something to pull CDDB info and posting the previos post, I started up the same song and it displays with the album cover displayed in Rhythmbox.

So, this should solve your problem. It solved my problem. :)

---

### Post by brewzka on 2011-05-25
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/787475](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/787475)

Yeah it doesn't work. I posted that bug.


May 24th, 2011
  On my two Ubuntu machines Rhythmbox is not fetching album tagging   information from MusicBrainz even though the information exists on the   MusicBrainz database. I checked with the picard program I had on the   machines. The CD lookup revealed the tagging information in picard.
  Here are my machines:
 

> Pentium D
Memory 2.9 GiB
 9.10 [kernel 2.6.31-23-generic]
Rythmbox 0.12.5
 libdiscid0   [Version: 0.1.0-1]
libmusicbrainz4c2a   [Version: 2.1.5-2ubuntu1]
picard   [Version: 0.11-2ubuntu3]
 ||||||
 Core 2 Duo
Memory: 2.0 GiB
 10.04 [kernel 2.6.32-31-generic]
Rythmbox 0.12.8
 libdiscid0   [Version: 0.2.2-1]
picard   [Version: 0.12.1-0ubuntu1]
libmusicbrainz4c2a   [Version: 2.1.5-4]
Just ran the --debug command and here is the output.
>                   This CD could not be queried: Cannot find  musicbrainz pages on server. Check your server name and port settings.
(03:33:31) [0x87eb028] [metadata_cb] rb-audiocd-source.c:767: ignoring CD metadata from fallback source

        
To reproduce follow these steps:
> 
1. Insert a well known cd into the tray
 2. Run rhythmbox --debug
 3. Go to the CD section under the area titled "Devices"
 4. Hit the "Reload Album Information" button.
 5. Look at debug information.
Additionally banshee is having the same problem according to many users.

---

