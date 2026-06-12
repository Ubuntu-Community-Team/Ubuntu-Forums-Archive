---
title: "No mic using esddsp"
date: 2006-02-12
forum: Multimedia &amp; Video
---

### Post by Kimm on 2006-02-12
Hi, I need to run TeamSpeak (or Skype) at the same time as playing a game, but when I run these programs the game get no sound.

When I run TeamSpeak and Skype along with the same through esddsp I get sound in both, but neighter TeamSpeak nor Skype can use my Mic, so I realy dont gain anything from doing that.

Could anyone help??!

---

### Post by Kimm on 2006-02-13
/bump

---

### Post by wncben on 2006-02-13
Howdy, I am still a noob here, but have found some interesting info about sound.  It seems that alsa, esd, and oss do not play nice together, and tend to hog the soundcard.  It seems like you need to set up your system to be a duplex system, so that system resources are shared, and you can capture and playback sound at the same time.  There are a couple of good howto's in the hoary forums which work well in breezy too.  I posted links to them, as well as my trouble shooting process on this thread. Post #56 includes my current setup.

  Hope this helps:-D 

[URL="http://ubuntuforums.org/showthread.php?t=126975&page=6"]
[/URL]

~Ol' Ben

---

