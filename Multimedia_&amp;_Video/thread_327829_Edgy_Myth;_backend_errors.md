---
title: "Edgy Myth; backend errors"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2006-12-29
I'm close to getting myth bacdkend going but I have two errors when I check for error messages.

using:     tail -f /var/log/mythtv/mythbackend.log

I get the following error log:

[B]2006-12-29 17:17:47.631 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.[/B]
2006-12-29 17:17:47.865 Main::Starting HttpServer
2006-12-29 17:17:47.882 Main::Registering HttpStatus Extension
2006-12-29 17:17:47.975 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
[B]2006-12-29 17:17:47.979 Enabled verbose msgs:  important general
/video/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/video' exists and that both 
the directory and that file are writeable by this user.[/B]

So where do I start looking in order to attach localhost to the two card inputs? (HPG 150 and HPG 350)

The second error refers to my video LVM.  What is nfslockfile? 

 I have created the folowing directories in /video:
buffer, mythmusic, .mtyhtv, pictures, recordings, .tmp, and videos.  

Then I created the symlink from /home/mythtv/.mythtv to /video/.mythtv

The LVM, directories, and symlink were per "Linux toys 2"

---

