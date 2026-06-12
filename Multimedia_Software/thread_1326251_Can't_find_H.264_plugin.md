---
title: "Can't find H.264 plugin"
date: 2009-11-14
forum: Multimedia Software
---

### Post by crazy dave on 2009-11-14
Having trouble with plugins in both Firefox and Chromium when trying to play Quictime embedded media.  Whilst this worked after a clean install, I have lost this functionality, probably due to installing other packages.

This problem has been around for a good while and I had the same issues with Jaunty.  I was hoping this would not be an issue with 9.10 but here it is again.  I know apple doesn't release a plugin for linux but there are plenty of players capaple of handling what is essentially integrated web content.

I have done the usual with Gstreamer, Medibuntu, Mplayer, to no avail.  The browsers keep looking for the H.264 codec which is already installed, go figure?

Any help most welcome.

---

### Post by andrew.46 on 2009-11-14
Hi crazy dave,

Can you give a specific stream that is giving you trouble? I usually have no trouble with the streams you mention by uninstalling the Totem mozilla plugin and running only with the gecko-mediaplayer, this might be worth a look on your setup...

Andrew

---

### Post by crazy dave on 2009-11-15
Hi Andrew, thanks for responding,  an example would be Apple movie trailers, or streams in quicktime.  I have gecko-mediaplayer installed, no difference with that.  I attach some screenshots FYI.  I'm also experiencing very staggered and jumpy shockwave flash playback through for example the BBC news website video clips, and I'm wondering what I could have done to mess it all up because it was working fine.

---

### Post by crazy dave on 2009-11-15
OK got it sorted out? it was a problem with gstreamer, just reinstalled it and Bingo!

Thanks

---

### Post by andrew.46 on 2009-11-15
Hi crazy,

> **crazy dave said:**
> Hi Andrew, thanks for responding,  an example would be Apple movie trailers, or streams in quicktime.  I have gecko-mediaplayer installed, no difference with that. 

I see you have sorted the issue out, great news :). Just bear in mind that those images appear to show the totem-mozilla plugin rather than the gecko-mediaplayer. Often if you wish to use gecko-mediaplayer exclusively the totem-mozilla plugin has to be uninstalled. But if your clips are now playing this is only a side issue :).

Andrew

---

### Post by crazy dave on 2009-11-16
Andrew,

Thanks for taking the time to help with this glitch, duly note re Totem Mozilla.

Regards,

Dave

---

### Post by crazy dave on 2009-11-16
Andrew,

Thanks for taking the time to help with this glitch, duly note re Totem Mozilla.

Regards,

Dave

---

