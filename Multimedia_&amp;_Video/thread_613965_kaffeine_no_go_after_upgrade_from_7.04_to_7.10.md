---
title: "kaffeine no go after upgrade from 7.04 to 7.10"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by lptr on 2007-11-15
Since upgrade to Gutsy I'm not able to play mpg videos anymore they did definitively play before upgrading. Kaffeine does nothing. No messages in /var/log when starting in starter pumping icon no message - when starting from shell window, also nothing, simply dead. Forced reinstall, no change.

Tried MPlayer instead. This tells me 

```
Fatal error! Error opening/initializing the selected video_out (-vo) device

```Any ideas?

rob*

:) Purging the complete package did it. It bound another lib (don't ask me what lib. I only saw it appearing very shortly.) Mumble... if all would be that easy...

---

