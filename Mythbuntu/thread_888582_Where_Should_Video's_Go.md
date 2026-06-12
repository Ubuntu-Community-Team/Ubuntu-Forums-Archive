---
title: "Where Should Video's Go"
date: 2008-08-13
forum: Mythbuntu
---

### Post by jlp_engineer on 2008-08-13
Hello,

I have a combination Front-End/Back-End running just fine.  I have attached another Front-End to the Back-End, and it is working with the exception of pulling up Videos (imported DVD's).  The DVD's were imported using the original Front-End.  When I import a DVD on the remote Front-End, the file ends up on that system.  However, when I enter the Video Manager option on this Front-End, it complains about missing files - basically all the imported DVD's that are on the other combination Back-End/Front-End.  

Question: Since the remote Front-End can in some sense "see" that the files are missing, is the only thing that needs to be corrected is the path to Back-End from the remote system?

Question: Does the fact that there are videos out there somewhere come from UPnP or the connection to the database via the remote Front-End?

Question: Will I have to sync all the paths from all my other Front-Ends I connect and create shares on the Back-End in order to get all the Videos, MP3's, etc., accessible from the same location?

Thanks.

---

### Post by freymann on 2008-08-13
> **jlp_engineer said:**
> Hello,

I have a combination Front-End/Back-End running just fine.  I have attached another Front-End to the Back-End, and it is working with the exception of pulling up Videos (imported DVD's).  The DVD's were imported using the original Front-End.  When I import a DVD on the remote Front-End, the file ends up on that system.  However, when I enter the Video Manager option on this Front-End, it complains about missing files - basically all the imported DVD's that are on the other combination Back-End/Front-End.  


This is a common issue on new setups. The following link should help you:

[http://www.mythtv.org/wiki/index.php/Mediashares](http://www.mythtv.org/wiki/index.php/Mediashares)

Basically, you are better off to put your videos (and music and pictures) all in one place (on the master backend for instance) and then export those paths and mount them in the same directory structure via NFS on your frontends.

Then the files will appear to be in the same location on every machine.

I also export the folder that contains the cover art for movies, so the cover art appears on all boxes.

---

