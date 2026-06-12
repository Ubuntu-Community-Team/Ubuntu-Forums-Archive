---
title: "Decoder?"
date: 2009-02-17
forum: Multimedia Software
---

### Post by Bofur on 2009-02-17
I'm trying to play a steam online with Swiftfox but it says I need an html/text decoder. I've installed the ubuntu-restricted-extras and I have gstreamer and totem installed but I get this error message: ```
** Message: Not expecting a new stream; aborting stream
** Message: don't know how to handle text/html
** Message: Error: A text/html decoder plugin is required to play this stream, but not installed.
gstdecodebin.c(904): close_pad_link (): /GstPlayBin:play/GstDecodeBin:decodebin0:
No decoder to handle media type 'text/html'

** Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|text/html decoder|decoder-text/html (text/html decoder)
no application found
** Message: No installation candidate for missing plugins found.
** Message: don't know how to handle text/html
** Message: Error: A text/html decoder plugin is required to play this stream, but not installed.
gstdecodebin.c(904): close_pad_link (): /GstPlayBin:play/GstDecodeBin:decodebin1:
No decoder to handle media type 'text/html'

** Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|text/html decoder|decoder-text/html (ignoring)
** Message: All missing plugins are blacklisted, doing nothing
TotemEmbedded-Message: Viewer state: STOPPED
TotemEmbedded-Message: totem_embedded_set_error: 'The playback of this movie requires a text/html decoder plugin which is not installed.'
TotemEmbedded-Message: totem_embedded_set_error_logo called by browser plugin



```
Any help would be appreciated!

---

### Post by xc3RnbFO8P on 2009-02-17
Check this:
[http://ubuntuforums.org/showthread.php?t=880738]("http://ubuntuforums.org/showthread.php?t=880738")

---

### Post by Bofur on 2009-02-17
All that stuff is installed unfortunately. Here is the website I'm trying to access: [http://www.tv-life.com/shows/sliders/](http://www.tv-life.com/shows/sliders/)

---

### Post by Bofur on 2009-02-17
Bump

---

### Post by hansdown on 2009-02-17
Hi Bofur.

I can't find one in synaptic.

Maybe a browser plugin?

Your output says  ```
Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|text/html decoder
```

I searched synaptic, but no go.

If you enter gstreamer 0.10 in synaptic, you get alot of plugins.

---

