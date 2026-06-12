---
title: "Plex Media Manager doesn't see any of my media"
date: 2014-01-26
forum: Multimedia Software
---

### Post by JClaxton on 2014-01-26
I'm trying to set up a Plex Media Server on my box running Ubuntu 12.04.  My media is stored on a "WD My Passport" external USB drive in a folder called "Media".  I cannot get Plex to see any of the files.  I try to add a section for movies, for example, and when I try to point it to the folder where the movies are stored, it sees the hard drive in /Media/My Passport but won't show any subfolders.  If I just point it to /Media/My Passport it doesn't populate any of the files within.
I've read other threads with people experiencing similar issues, and some suggested the hard drive being formatted for NTSF might be the issue or the mount point of the hard drive or there might not be appropriate permissions set up.  To rule out the external hd as a possible issue, I tried pointing it to my music folder on my primary internal hard drive where Ubuntu is installed and it won't populate that media either.  I tried adding the user "plex" to my group "Josh" thinking that might resolve any issues with permissions, but still can't populate any media.
Not sure where to go from here.  Any help would be appreciated.

---

### Post by JClaxton on 2014-01-26
UPDATE:  I was able to fix the issue with a program called psydm.

Using this program I was able to set plex as the owner of the drive, so it has permission to access now.  Works great!

---

