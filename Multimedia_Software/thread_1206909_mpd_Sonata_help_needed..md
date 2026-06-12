---
title: "mpd/ Sonata help needed."
date: 2009-07-07
forum: Multimedia Software
---

### Post by chris_andrew on 2009-07-07
Hi, guys.

I've installed mpd and Sonata.  I've followed the wiki and used the bits that I thought were relevant to my set-up.  When I start sonata, nothing happens.  Something that doesn't look right is that it says _Not connected_.
My config file points to port 6600.  

This is in the main mpd.conf and the one in my home directory, as I'm not sure which should be added, so I did both.

Can anyone point me in the right direction?

Cheers,

Chris.

---

### Post by chris_andrew on 2009-07-08
I think this could be my problem; when I restart mpd, I get:


```
sudo /etc/init.d/mpd restart
[sudo] password for chris: 
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                              * creating ~/.mpd/mpd.db... 
problem opening log file "/var/lib/mpd/.mpd/mpd.log" (config line 11) for writing
Aborted
```

I didn't have an .mpd/mpd.log, so I created an empty file and hoped that would work..it didn't :-(.

Any ideas?

Cheers,

Chris.

---

