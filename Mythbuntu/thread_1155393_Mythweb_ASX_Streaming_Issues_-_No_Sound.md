---
title: "Mythweb ASX Streaming Issues - No Sound"
date: 2009-05-10
forum: Mythbuntu
---

### Post by mythms on 2009-05-10
I have been running my 8.04 install for about 8mo.  

I have just recently tried to playback recorded HD videos using the ASX stream on Mythweb.  If I click the ASX stream and choose to play with VLC I get video but no audio.  If I click the ASX stream and choose to play with WMP (V9.0) it just hangs up with no video and no audio.  

Since I have the recordings folder mounted with Samba I can browse to the directory and right-click and play.  When I right-click and play this way with WMP9.0 it plays back fine with audio and video.  When I right click and select 'Play with VLC media player' I get the same result as with the asx stream.  

BTW, this recording will playback fine on both my frontend/backend machine as well as on my mythbuntu frontend running on a AppleTV.

I am sure this is something simple.

Any ideas?

---

### Post by mythms on 2009-05-10
BTW - VLC plays SD recordings fine through mythweb.  WMP9.0 hangs up on SD recordings and HD recordings alike.

---

### Post by nerdzero on 2010-10-20
Did you ever find a solution?  I am experiencing the same issue.

---

### Post by mythms on 2010-10-20
I did get it working.  It's been a while since I messed with this.  I can barely decipher the notes I took regarding my solution.  Hope they help...

Here are my notes:

```
use SMPlayer

Since smplayer needs -playlist on the command line.

To set this up for all open the gui and:

Options->Preferences->Advanced->Options for Mplayer->Options = -playlist
```

---

### Post by nerdzero on 2010-10-21
Hey, that worked.  Thanks!

---

