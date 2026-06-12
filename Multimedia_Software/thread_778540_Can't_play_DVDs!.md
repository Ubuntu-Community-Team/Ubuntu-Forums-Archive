---
title: "Can't play DVDs!"
date: 2008-05-02
forum: Multimedia Software
---

### Post by Dinchamion on 2008-05-02
I just upgraded to Hardy, from a fresh install of Gutsy (I couldn't do it straight from Hardy install, as the installer didn't work), have set up everything properly, but I can't play DVDs!

SMPlayer does nothing, VLC gives me this: ```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: NYOMAS_UTANA
libdvdnav: DVD Serial Number: 2ecb85b2
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/dinchamion/.dvdnav/NYOMAS_UTANA.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000300] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000303] vcd access error: no movie tracks found
[00000303] access_file access error: file /dev/scd0 is empty, aborting
[00000310] main private error: cannot pre fill buffer
[00000289] main playlist: nothing to play
```

The disc is fine, the device is fine (it mounts up, I can read it with Nautilus and other file managers, I can write CDs with it), I tried every possible thing I could think of but I ran out of ideas. :(

Any tips?

---

### Post by Saint Angeles on 2008-05-02
have you added the medibuntu repos?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Dinchamion on 2008-05-02
> **Saint Angeles said:**
> have you added the medibuntu repos?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Yes, I have all codecs and stuff: libdvdcss2, libdvdread, etc. I have vlc, smplayer, xine, gxine and elisa installed, none of them work with DVDs.

I did a forum search and tried many of the suggestions, but none of them worked.

---

