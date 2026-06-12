---
title: "MP3 sound is &quot;poppy&quot;"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by CSMatt on 2007-02-02
Has anyone noticed that when MP3 decoding support is added to the Totem player, the MP3s played have faint popping noises in them?  I haven't checked other players, but this happens for both gstreamer 0.8 and xine 1.1.2.  I'm using Edgy, if that makes a difference.

---

### Post by teaker1s on 2007-02-02
I have similar in streamtuner on some stations

---

### Post by CSMatt on 2007-02-02
I think the culprit is the gstreamer0.10-fluendo-mp3 package, considering that that is the only gstreamer package that I installed that actually provided MP3 support, dispite the descriptions of other gstreamer plugins.

It's not happening in VLC, so it's not the system.

---

