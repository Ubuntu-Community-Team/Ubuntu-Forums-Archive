---
title: "Can't stream from Stage 6"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by MrDiaz on 2007-10-07
Hi, when I go to [www.stage6.com](www.stage6.com) and try to stream a video. It'll say:

> For Linux support try Mplayer.

Thing is, I have MPlayer installed on my machine. Even went into Synaptec to make sure the package was installed and it is! 

Anyone having the same issue?

---

### Post by MrDiaz on 2007-10-07
I tried to install the MPlayer plugin for Firefox. But when building the source (./configure)

this is what it tells me
> 
configure: Determining mozilla/firefox packages to build against
checking for MOZPLUG... no
configure: WARNING: mozilla-plugin not found
checking for MOZPLUG... no
configure: WARNING: firefox-plugin not found
checking for MOZPLUG... no
configure: WARNING: seamonkey-plugin not found
checking for MOZPLUG... no
configure: WARNING: xulrunner-plugin not found
checking for MOZPLUG... no
configure: WARNING: iceape-plugin not found
configure: error: Unable to find mozilla or firefox development files

---

### Post by MrDiaz on 2007-10-07
bump

---

### Post by MrDiaz on 2007-10-08
come on folks, please a little help over here

---

### Post by HOLOGRAPHICpizza on 2007-10-15
I'm having this same problem, and can't seem to figure it out. Help anyone?

---

### Post by Namtabmai on 2007-10-15
Have you got mozilla-mplayer installed? This should provide the mozilla mplayer plugin without you having to compile it from the source.

---

### Post by HOLOGRAPHICpizza on 2007-10-15
I installed totem, totem-gstreamer, and totem-mozilla, and stage6 somewhat works, but the videos are super laggy. Why cant divx just make an official linux version?

---

### Post by Namtabmai on 2007-10-15
Right open up firefox and type
```

about:plugins

```
Into your location bar, this will display all the plugins that firefox recognises and which files they are associated with. Mine shows this for divx.
[IMG]http://www.keyboardcowboy.co.uk/images/firefoxmplayer.png[/IMG]
If you've got totem showing up there instead, try uninstalling it and checking again (maybe reinstall mozillamplayer), until you get mplayerplug-in as the registered plugin for divx.

Then try the videos again.

If you're still having trouble you could try specifying a buffersize for mplayer
open up .mplayer/config
and add a line like
```

cache=2048

```
This should give you a 2Mb buffer when streaming videos, so they'll take longer to load but you won't get stutter while streaming at it will have more video in the buffer to play while it's trying to download the rest.
Oh make sure to restart firefox after editing .mplayer/config otherwise it might not take notice of the changes.

---

