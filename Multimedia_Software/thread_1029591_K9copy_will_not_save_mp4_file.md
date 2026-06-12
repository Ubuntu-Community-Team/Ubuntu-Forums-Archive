---
title: "K9copy will not save mp4 file"
date: 2009-01-03
forum: Multimedia Software
---

### Post by codejammer on 2009-01-03
I'm trying to use k9copy to rip a DVD to MP4 format and it goes through the motions but then fails to save the file at the end.  The only error messages I get are:

[Option lavfopts: Unknown suboption i_certify_that_my_video_stream_does_not_use_b_frames
Error parsing option on the command line: -lavfopts
]

and...

QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty

and...

[libdvdnav: Unable to find map file '/home/andy/.dvdnav/PEARL_HARBOR.map'
]

I've checked various forums and have found that the lavfopts option is nolonger supported by mplayer but I can't see how to turn it off in the settings in k9copy.  Any help would be appreciated.

---

### Post by ender4 on 2009-01-19
> **codejammer said:**
> 

QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty



others do not have read access to /etc/qt3/qt_plugins_3.3rc (at least on intrepid) by default.  as far as i know this is a bug.  

to fix this just type 
```

sudo chmod a+r /etc/qt3/qt_plugins_3.3rc

```
 in the terminal

as for "QSettings::sync: filename is null/empty" i get the same error when i run celestia, but i haven't figured out how to fix it yet.

---

### Post by Brian96 on 2009-01-24
Ever figure this out?

---

### Post by codejammer on 2009-08-06
No I didn't.  I'm using OGMRip which seems to work fine.

---

