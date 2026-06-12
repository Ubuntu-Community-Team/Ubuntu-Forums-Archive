---
title: "[SOLVED] Dark screen when trying to play videos"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by tntc1978 on 2007-10-19
I've installed the [Ubuntu restricted extras]("https://help.ubuntu.com/community/RestrictedFormats"), and I've installed the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") codecs, but I've also installed Mplayer and VLC player. Don't know if that ruins anything.

But I'm having problems playing videos on the internet:

[http://www.nba.com/allstar2007/video/](http://www.nba.com/allstar2007/video/)
Seldom starts, and when it does, it's to dark to see anything.

[http://www.youtube.com](http://www.youtube.com)
No problems at all.

[http://www.dr.dk/NETTV/Update/Forside.htm](http://www.dr.dk/NETTV/Update/Forside.htm) (Danish national TV)
Seldom starts, and if it starts it's choppy, and it always stops before it's finished :-)

Besides that, I simply love the new Ubuntu, it works like a charm, and is fast as lightning :-)

---

### Post by tntc1978 on 2007-10-19
I fixed the darkness-issue with this post: [http://ubuntuforums.org/showpost.php?p=3568419&postcount=2](http://ubuntuforums.org/showpost.php?p=3568419&postcount=2) 

But I'm still experiencing problems with the videos not starting or being choppy (I'm on a 8/1 Mbps line, and haven't experienced problems earlier). Alternatively starting very very very delayed.

---

### Post by tntc1978 on 2007-10-19
I figured it out. :guitar:

I removed totem-mozilla from Synaptic (and ensured that Mozilla-Mplayer was installed), this made my browsers default to MPlayer, which apparently has a easier time streaming proprietary formats.

---

