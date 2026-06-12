---
title: "vlc loses sound after upgrade"
date: 2010-11-06
forum: Multimedia Software
---

### Post by matrooswolf on 2010-11-06
Hi,
I recently upgraded to 10.10 and since then I have problems with vlc.
When playing dvd's from disk (I haven't tested other ones) vlc starts normaly, but after a couple of minutes suddenly there is no sound anymore.

Other players (smplayer, kaffeine, totem) give sound, so it is not the file. (But they do not give subtitels, so I prefer vlc.
Vlc played perfectly ever before.

Any ideas what is wrong with vlc (1.1.4)?

Or is there an alternative that will play sound + subtitles that I do not know about ( I really need those subtitles for my children)?

---

### Post by lidex on 2010-11-06
I've used Mplayer with subtitles, so I don't understand why SMplayer, which is based on that, doesn't.

You really should try playing some other formats to see if it's just dvds giving the issue.

---

### Post by matrooswolf on 2010-11-07
I read on the videolan site that vlc-plugin-pulse should be installed. It wasn't, maybe that will do the trick...

---

### Post by Yellow Pasque on 2010-11-07
Make sure you set VLC to use pulse then.

As for Totem, you need gstreamer-plugins-ugly package to get the subtitle plugin.

---

### Post by matrooswolf on 2010-11-10
Apparently installing vlc-plugin-pulse solved the problem.
I have no idea why it wasn't installed. On my laptop it was, on my desktop not.
Well, moving on to new adventures!

---

