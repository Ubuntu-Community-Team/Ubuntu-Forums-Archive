---
title: "Uninstall totem, install gxine or xine-ui"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by snl on 2007-04-12
I would like to use either gxine or xine-ui instead of totem.
 
I did a search and found that totem, totem-gstreamer, totem-mozilla, and libtotem-plparser1 are installed. Which of these can I remove without removing ubuntu-desktop?

Do gxine and xine-ui give the same quality video and audio playback, are they just different gui?

Is libxine-extracodecs the only codec I need to install, is it enough? Do I need w32codecs and all the gstreamer codecs?

How to use gxine and xine-ui in firefox? For gxine, do I need to install gxineplugin? How about xine-ui?

Sorry for stupid question but does mplayer plug-in for firefox requires mplayer to be installed?

Thank you.

---

### Post by nabla on 2007-04-21
What I did was get rid of totem-gstreamer backend with :
[B]
sudo aptitude purge totem-gstreamer[/B] 

this will give a recommendation to install totem-xine (which is what I wanted) to resolve dependencies issues, so I chose yes.

Then I installed gxine with 

**sudo aptitude install gxine**

this should install libxine1 and libxine-extracodecs but just in case install those with aptitude also.

Can't comment on xine-ui since I tried it a few iterations of Ubuntu ago and didn't like it.

Hope this helps.

---

