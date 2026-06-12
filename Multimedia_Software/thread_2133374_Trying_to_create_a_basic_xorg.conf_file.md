---
title: "Trying to create a basic xorg.conf file"
date: 2013-04-08
forum: Multimedia Software
---

### Post by Sethun on 2013-04-08
So the only way I've heard to do is sudo Xorg -configure command, and when I do that I get:
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

---

### Post by Sethun on 2013-04-08
I figured it out. So I just had to stop the xorg session, by running sudo stop kdm and then logging in through the command session, and run sudo Xorg -configure, then sudo start kdm and the file was waiting there in my home folder

---

