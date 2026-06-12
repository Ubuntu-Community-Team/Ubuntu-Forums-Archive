---
title: "Can't Play Files from Samba Share?"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by trmentry on 2007-04-27
I just finished installing Fiesty and using Automatix2 to get a lot more goodies on.

I mounted some Samba shares to my server and attempted to play a divx video (avi).

Totem comes up with the following error:

```

There is no input plugin to handle the location of this movie

```

I'm at a loss as to why.  I've been Googling to see and I'm currently working on getting NFS working on my server to try it that way.  If I copy the file to my local machine it plays fine but kinda defeats the purpose of a server. :)

Thanks

---

### Post by trmentry on 2007-04-27
Fixed. 

Uninstalled totem-xine and installed totem-gtstreamer.  Works like a charm now.

---

### Post by jared85 on 2007-05-02
Thanks for advice. I had the same problem trying to stream media from some samba shares. Swapped out xine for gtstreamer and now it works fine :)

cheers

---

