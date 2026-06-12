---
title: "Multiple Sound/ Software Mixing under Dapper"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by LordMau on 2006-07-24
On my fresh install of dapper I was pleasantly surprised that sound software mixing is already enable by default. As such I did'nt need to go thru the process described here [<link>]("https://help.ubuntu.com/community/EnableSoftwareMixing?action=fullsearch&value=linkto%3A%22EnableSoftwareMixing%22&context=180")

Initially I tested this by playing simultaneous mp3s on xmms and mplayer, then playing a game under wine with no issues. But after installing quod libet, which is depends on gstreamer-0.10, I noticed that quodlibet/ gstreamer doesn't share the sound card. As default the audiosink was already set for alsasink.

Any suggestions on how to make gstreamer/ quodlibet play nice and share? Or this normal behaviour?

---

### Post by LordRaiden on 2006-07-24
Make sure all your applications are using ALSA. That would include xmms, mplayer, wine, and gstreamer.

---

### Post by LordMau on 2006-07-24
> **LordRaiden said:**
> Make sure all your applications are using ALSA. That would include xmms, mplayer, wine, and gstreamer.

As noted above all of them are using alsa already. Still gstreamer (via quod libet) hogs the sound card when it runs first, or doesnt run when something else runs. But xmms, mplayer and wine runs fine altogether mising sounds.

gstreamer is alreadyset using alsasink as audio source.

---

### Post by LordMau on 2006-07-24
Just reviewed my system and fixed this issue. Since I ran my fresh install as minimal as possible I didn't have the file gstreamer-properties installed. I used instead gconf-editor to check that value alsasink was already in the audio source for gstreamer. Since quod libet runs fine i assumed it was ok.

But whats nice with  gstreamer-properties is that little button called "Test". So when I finally installed  gstreamer-properties and pressed test I got the message of missing elements. It seems that quod libet (ang gstreamer 0.10) did not pull in the dependency for the gstreamer-alsa plugin on my system, and I wasn't aware of this. Installing that plugin solved it for me.

---

### Post by LordRaiden on 2006-07-25
Nice to know your problem is fixed: it's almost always usually a alsa vs. oss issue when something like this happens. I usually exclusively download alsa versions of packages in advance.

---

