---
title: "Rhythmbox loses settings between session"
date: 2008-09-29
forum: Multimedia Software
---

### Post by belfasttim on 2008-09-29
Hi-- I'm using Rhythmbox on Hardy, and recently re-installed it after dumping it to try some other apps. After the re-install, it doesn't save the location of my DAAP share between sessions. Not a big deal, but it's annoying to have to add the location every time I open Rhythmbox. 

Any ideas where these settings should be stored?

Thanks

---

### Post by darkpaladin79 on 2008-10-23
Need the same thing here, although I could compromise if I could only find a way to launch rhythmbox from the command line, opening the server.  I found this (I've customized it with my server's IP and whatnot):

```
rhythmbox-client --play-uri "daap://server_ip:3689/databases/1/items/1.mp3?session-id=1"
```

It opens rhythmbox as if I had never issued the option.  I also get an error in the terminal, something like "The method called by loadURI returned FALSE but did not set an error code."

If anyone could get this working, I'd be incredible grateful.  Or, if anyone knows an alternate way to get any music player fired up on start with a daap server, I'd take that too.


Thanks much,
Ivan

---

