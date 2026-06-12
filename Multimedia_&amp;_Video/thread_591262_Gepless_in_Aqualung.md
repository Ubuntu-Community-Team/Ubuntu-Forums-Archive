---
title: "Gepless in Aqualung?"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by vanadium on 2007-10-25
Aqualung is supposed to support gapless playback, even for lame mp3s. Unfortunately, the app is not in the repos and compiling is not a very apealing option from me. I did however find a *.deb from getdeb.org, which installed fine. However, the playback is all but gapless. Might this be due to the fact that it is an older version? (it says Build version R-718) or am I missing something out?

---

### Post by hardyn on 2007-10-25
that would be my guess... is there anything in the release notes about when gapless was implimented?

give compiling a try... it usually is made pretty straight-forward by the developers; and you will definately learn something.

---

### Post by VCSkier on 2007-10-25
A while ago, I think it was under Dapper, I compiled aqualung (it was the first and only time I've ever compiled anything) and it worked alright.  IIRC, it was quite difficult finding all the proper components though; it took quite some time, and in the end, I didn't really think it was worth it.  Other aspects of the player were rather lackluster, and didn't really suit my needs.

It's too bad there isn't more of an interest in audio things among OSS users.  There are several things that I could easily do in Windows that now are tedious or impossible.  I think GStreamer needs quite a bit of development before our audio tools can be considered powerful, or even comparable to the tools available on Windows.

---

### Post by vanadium on 2007-10-25
Thank you for your replies. I had some more time to test today, and ogg, flac, etc are fine. mp3 is not. The deb file I used is named aqualung_0.9beta8-1~getdeb1_i386.deb, which would correspond with the "current" release. In the "about" box, R-718 is reported as the version. 

In the bug reporting system, I see a message

"Gapless MP3 playback is achieved using LAME header info
since CVS 0.205.0. Thus I consider this issue resolved. "

This message is dated 25-08-2006. A release R-699 is dated 16 june 2007. Thus, my build R-718 should be more recent and include the playback using Lame header info. Could some other people using Aqualung report on lame gapless playback capabilities? Provide version info, please.

---

### Post by vanadium on 2007-12-04
Aqualung R-587

Still no gapless lame mp3 playback for me. Anyway, I found what seems to be the only lame mp3 gapless solution right now: music player daemon (mpd), a bit difficult to set up but once up and running with a frontend very nice. Added bonus: one of the few linux players that supports replay gain.

---

### Post by VCSkier on 2007-12-04
What frontend are you using?  I've had heard good things about MPD, and I took a look at it once a while ago, but I forwent it for one reason or another.  Maybe I should give it a second thought.  Is it dependent on playlists, or does it scan folders to create a library of files?  Thanks.

---

