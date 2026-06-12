---
title: "Including mplayer run options when using Kmplayer, Gmplayer"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by lodp on 2006-11-07
Hi there,

I'm trying to get kmplayer to stream audio to a remote host (an audio output dongle/speakers directly on my router). 
In mplayer on the command line, I can do this simply by adding the option "-ao esd:192.168.1.1" to the command, which then looks like this:

mplayer -ao esd:192.168.1.1 <file>

this successfully streams audio to the Esound daemon running on my router. But how do I include that option (or indeed any option) when using the kmplayer or gmplayer frontend? I couldn't find anything in the preferences...

---

