---
title: "MPD: connection refused after using laptop with mobile broadband"
date: 2009-07-06
forum: Multimedia Software
---

### Post by Piraja on 2009-07-06
Dear all,

I keep getting 

```
problems connecting to "localhost" on port 6600: Connection refused
```

after I used my laptop with a mobile broadband connection for a week, instead of the usual wireless home network. Away from home, I listened to music with MPD (NCMPCPP frontend) from my local hard drive; I can still do that, but each time I try to update the database so that I could access my "remote" music collection on an NFS share residing on my desktop PC, I get the error above.

Any ideas?

---

### Post by Piraja on 2009-07-06
Looking at **mpd.log**, I realized that the database update gets interrupted at some point, with the following lines after the track names:
```
[flac @ 0xb7cc32f0]overread: 3532
```
and/or
```
[flac @ 0xb7cc32f0]overread: 2830
```

...

Follow-up at the [MPD Forums](http://www.musicpd.org/forum/index.php?topic=1932.msg7963#msg7963).

---

