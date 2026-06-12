---
title: "Upgrade to Precise, Rygel renderer stop working"
date: 2012-05-23
forum: Multimedia Software
---

### Post by mren on 2012-05-23
I've got an Ubuntu headless (KVM) running Rygel/Playbin as UPnP renderer, it was working fine before upgrade. The UPnP renderer was set up in Natty from Chris S. ppa (Rygel 0.10), then upgraded to Precise (Rygel 0.14).

After upgraded to Precise, the rygel renderer stop working. Rygel process will start without problem, but it will give out error message whenever trying to play music to it:

Here is log:

```
GstLaunch-Message: rygel-gst-launch-plugin.vala:28: Plugin 'GstLaunch' disabled by user, ignoring..
Rygel-Message: New plugin 'Playbin' available
Tracker-Message: rygel-tracker-plugin-factory.vala:32: Plugin 'Tracker' disabled by user, ignoring..
Mediathek-Message: rygel-mediathek-plugin.vala:33: Plugin 'ZDFMediathek' disabled by user, ignoring..
MediaExport-Message: rygel-media-export-plugin.vala:32: Plugin 'MediaExport' disabled by user, ignoring..

(rygel:10804): Playbin-WARNING **: rygel-playbin-player.vala:210: Error from GStreamer element playbin20: gstsouphttpsrc.c(924): gst_soup_http_src_finished_cb (): /GstPlayBin2:playbin20/GstURIDecodeBin:uridecodebin0/GstSoupHTTPSrc:source:
libsoup status code 3

(rygel:10804): Playbin-WARNING **: rygel-playbin-player.vala:213: Going to STOPPED state

(rygel:10804): Playbin-WARNING **: rygel-playbin-player.vala:210: Error from GStreamer element playbin20: gstsouphttpsrc.c(924): gst_soup_http_src_finished_cb (): /GstPlayBin2:playbin20/GstURIDecodeBin:uridecodebin1/GstSoupHTTPSrc:source:
libsoup status code 3

(rygel:10804): Playbin-WARNING **: rygel-playbin-player.vala:213: Going to STOPPED state

(rygel:10804): Playbin-WARNING **: rygel-playbin-player.vala:210: Error from GStreamer element playbin20: gstsouphttpsrc.c(924): gst_soup_http_src_finished_cb (): /GstPlayBin2:playbin20/GstURIDecodeBin:uridecodebin2/GstSoupHTTPSrc:source:
libsoup status code 3

(rygel:10804): Playbin-WARNING **: rygel-playbin-player.vala:213: Going to STOPPED state
```

Tried on another machine, almost the same setup but fresh installed Precise, everything just work.

Can anybody help me to solve the problem, thanks!

---

### Post by jensgeorg on 2012-06-20
> **mren said:**
> 

Tried on another machine, almost the same setup but fresh installed Precise, everything just work.

Can anybody help me to solve the problem, thanks!

Can you try to run with G_MESSAGES_DEBUG=all ?

Probably something missing in the GStreamer world.

---

