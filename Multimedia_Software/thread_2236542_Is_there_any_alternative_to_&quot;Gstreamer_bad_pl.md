---
title: "Is there any alternative to &quot;Gstreamer bad plug-ins&quot;?"
date: 2014-07-27
forum: Multimedia Software
---

### Post by arroy_0209 on 2014-07-27
While trying to play an audio file I received this message: "Need to install Gstreamer plugins for mms, wavpack, quicktimes, musepack". However I found a comment regarding these: > GStreamer Bad Plug-ins is a set of plug-ins that aren't up to par  compared to the rest. They might be close to being good quality, but  they're missing something - be it a good code review, some  documentation, a set of tests, a real live maintainer, or some actual  wide use. If this is the case, should I try some better and safer alternative in case it exists? Can anybody please guide me? 
I should also mention that in another occasion I received this message: "need to install libmodplug1" which I have not yet installed.

---

### Post by bapoumba on 2014-07-27
Have you installed ubuntu-restricted-extras (or its flavor equivalent) ?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mc4man on 2014-07-27
If you want the codec support for gstreamer based apps that the plugin provides then installing the bad plugin is your only alternative.
The description is what they choose, there is no real issue on the user side.

Otherwise use media players that don't use gstreamer like vlc, smplayer/mplayer, mpv, audacious to name a few.

---

### Post by arroy_0209 on 2014-07-27
Thanks for your replies. However since my knowledge is limited, I need a little more help. 

To bapoumba:  [[COLOR=#990303]****[/COLOR]]("http://ubuntuforums.org/member.php?u=171805")I have not installed "ubuntu-restricted-extras" and I am not sure what you mean by its flavor equivalent. Perhaps you mean installing ubuntu-restricted-extras will be a better alternative as I asked. Am I correct?

To mc4man: In case I install the gstreamer bad plug-ins, will I receive the updates or not?

---

### Post by Yellow Pasque on 2014-07-27
ubuntu-restricted-extras (also flavors specific, such as kubuntu-restriced-extra, xubuntu-r-e, etc.) just pulls in the gstreamer-bad package. It is not an alternative.

You're making it way too complicated. Just install the needed package(s) and be done with it, or use a different program as mc4man suggests.

---

### Post by bapoumba on 2014-07-27
@arroy_0209 : if you are running ubuntu, just install ubuntu-restricted-extras. Have a look at the link for the flavors derivatives (ex : lubuntu-restricted-extras for lubuntu). You need to enable the multiverse repositories. I does install the bad- plugin, along with a lot of others : [http://packages.ubuntu.com/trusty/ubuntu-restricted-extras](http://packages.ubuntu.com/trusty/ubuntu-restricted-extras)

---

