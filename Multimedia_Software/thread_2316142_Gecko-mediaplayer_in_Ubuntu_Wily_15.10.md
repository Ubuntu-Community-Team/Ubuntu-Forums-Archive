---
title: "Gecko-mediaplayer in Ubuntu Wily 15.10"
date: 2016-03-05
forum: Multimedia Software
---

### Post by cogset on 2016-03-05
Why there is no package gecko-mediaplayer in Wily and subsequent releases? it was  there in Vivid, then I've noted that it has been removed in Wily and there's currently no trace of it either in Wily updates/backports or Xenial.

Is this package actually not needed anymore? It used to provide some plugins in Firefox which I suspected were in fact all the same, but I I was never sure about this.

Is their functionality now provided by the VLC plugin alone or is something else going on?

---

### Post by mc4man on 2016-03-05
It was dropped from Debian last summer due to being buggy & no current upstream maintainer
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=797188](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=797188)

---

### Post by goofprog on 2016-03-05
I would just try another video player like smplayer or totem.  Some projects just die off and are truly missed.

---

### Post by cogset on 2016-03-07
@ goofprog, my question was about the gecko-mediaplayer set of plugins for Firefox, not standalone players like totem or smplayer.  

Reading the original Debian bug that mc4man has posted about the removal of this package (thanks for the link), it seems to suggest that  **browser-plugin-vlc** is the recommended alternative -which somehow seems to confirm my idea that the gecko-mediaplayer plugins were in fact redundant, provided you had the vlc plugin installed.

  Is  that correct, or is there maybe some strange kind of media that could actually* need* the gecko-mediaplayer plugins ?  

To put it in other words, once these are removed, could I eventually run into some video that the vlc plugin may not be able to play?

---

### Post by mc4man on 2016-03-07
> **cogset said:**
> @ goofprog, my question was about the gecko-mediaplayer set of plugins for Firefox, not standalone players like totem or smplayer.  

Reading the original Debian bug that mc4man has posted about the removal of this package (thanks for the link), it seems to suggest that  **browser-plugin-vlc** is the recommended alternative -which somehow seems to confirm my idea that the gecko-mediaplayer plugins were in fact redundant, provided you had the vlc plugin installed.

  Is  that correct, or is there maybe some strange kind of media that could actually* need* the gecko-mediaplayer plugins ?  

To put it in other words, once these are removed, could I eventually run into some video that the vlc plugin may not be able to play?

I haven't used that vlc plugin but possibly this would be relevant to your query? (plus that plugin seems to no longer be developed 
[http://arstechnica.com/information-technology/2015/10/firefox-dropping-npapi-plugins-by-the-end-of-2016except-for-flash/](http://arstechnica.com/information-technology/2015/10/firefox-dropping-npapi-plugins-by-the-end-of-2016except-for-flash/)

---

### Post by cogset on 2016-03-14
I did read a while ago that Mozilla was planning to remove support for plugins altogether (which is good news when thinking of flash and java) , however I wonder if this will in some way affect the ability to play mp4 files using the gstreamer backend.
Also, some greasemonkey scripts are relying on gecko-mediaplayer to play videos.

---

