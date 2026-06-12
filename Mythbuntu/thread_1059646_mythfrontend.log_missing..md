---
title: "mythfrontend.log missing."
date: 2009-02-04
forum: Mythbuntu
---

### Post by jtpiano on 2009-02-04
Hi Everyone!
Since my last post I built a new machine for use as a backend.  I am running Hardy as a VM guest inside ESXi.  My "server" is a Dell GX280.  The system has been very stable for me.  Since my new build I have not been able to play my recorded content on my frontend.  My frontend connects successfully.  I am  able to browse my recorded shows.  I thought ok, time to look at the logs.  Low and behold, there is no frontend log, just the backend ones.  Any ideas why this may be?  My first thought was a permissions issue.  My permissions on /var/log/mythtv are drwxrwsr-x mythtv:mythtv.  What is "s"?  (Right, not a typo.)  Is this correct?  "S" seems odd to me, at least not anything I learned in school.  I did try to delete the directory and recreate the permissions with x instead of s.  It seems the permissions have changed back.  Am I even going down the right path?  Your input is appreciated!  Many thanks in advance.:)

---

### Post by jtpiano on 2009-03-17
Ok, I solved my own problem.  It turns out my persmissions were set wrong for my Samba share.  Once I fixed this I was able to connect and view all my shows.  I still can't expain the wierd permissions on the mythtv directory though.  Oh well.... :)

---

