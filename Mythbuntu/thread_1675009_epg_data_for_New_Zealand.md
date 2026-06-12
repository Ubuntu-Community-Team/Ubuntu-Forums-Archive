---
title: "epg data for New Zealand"
date: 2011-01-24
forum: Mythbuntu
---

### Post by blkbx on 2011-01-24
Hi 
I recently installed Mythbuntu and would like to get the epg going as well.
I've tried tv_grab_nz-py though I get no data at all, is their another or a different one completely.

---

### Post by nickrout on 2011-01-24
I am using tv_grab_nz-py and it works fine.

Please join the NZ mailing list:

[http://lists.ourshack.com/mailman/listinfo/mythtvnz](http://lists.ourshack.com/mailman/listinfo/mythtvnz)

What is the url that is getting downloaded by your version of tv_grab_nz-py? Look for this line:

```
SOURCES = (
    'http://nzepg.org/freeview.xml.gz',
)

```

if it is not as above, change it to that.

---

### Post by blkbx on 2011-01-25
Hey thanks for the reply. Didn't know where to look for your code.
My setup  is
video source setup,
Video source name: card 0
listings grabber: New Zealand (py) (xmltv)
channel frequency New Zealand

---

### Post by nickrout on 2011-01-25
```
less `which tv_grab_nz-py`
```

---

### Post by blkbx on 2011-01-27
the Source is the same as you posted.

---

### Post by nickrout on 2011-01-27
OK did you run the setup program for the grabber? It should have run in a terminal after you told myth to use it.

---

