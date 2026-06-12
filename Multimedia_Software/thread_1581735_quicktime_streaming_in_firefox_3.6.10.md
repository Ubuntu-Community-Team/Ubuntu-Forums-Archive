---
title: "quicktime streaming in firefox 3.6.10"
date: 2010-09-25
forum: Multimedia Software
---

### Post by jpc2879 on 2010-09-25
Hi all,

I'm trying to open a webpage which contains a quicktime stream in firefox 3.6.0

Some of my friends are viewing the stream correctly in ubuntu, but I'm getting this error:

```
TotemEmbedded-Message: Viewer state: STOPPED
** (firefox-bin:2302): DEBUG: SetWindow reply
** (firefox-bin:2302): DEBUG: 0xaea95680: "ViewerReady"
** (firefox-bin:2302): DEBUG: 0xaea95680: "Stream requested (force viewer: 0)"
TotemEmbedded-Message: totem_embedded_open_uri: uri rtsp://samarina.no-ip.info:8080/live/mpeg4 base_uri: empty.mov
TotemEmbedded-Message: totem_embedded_clear_playlist
Emptying current_uri
totem_embedded_set_uri uri rtsp://samarina.no-ip.info:8080/live/mpeg4 base empty.mov => resolved rtsp://samarina.no-ip.info:8080/live/mpeg4 (subtitle (null) => resolved (null))
TotemEmbedded-Message: totem_embedded_open_internal 'rtsp://samarina.no-ip.info:8080/live/mpeg4' subtitle '(null)' is-browser-stream 0 start-play 1
** (firefox-bin:2302): DEBUG: 0xaea95680: "NewStream mimetype 'video/quicktime' URL 'http://samarina.no-ip.info:8080/empty.mov'"
** (firefox-bin:2302): DEBUG: 0xaea95680: "Not expecting a new stream; aborting stream"
TotemEmbedded-Message: Viewer state: PLAYING
** (firefox-bin:2302): DEBUG: OpenURI reply
** (firefox-bin:2302): DEBUG: 0xaea95680: "Command 'Play'"
TotemEmbedded-Message: totem_embedded_do_command: Play
** Message: Error: No se pudo leer del recurso.
gstrtspsrc.c(3998): gst_rtspsrc_send (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstRTSPSrc:source:
Got error response: 454 (Session Not Found).


(totem-plugin-viewer:2330): GStreamer-CRITICAL **: 
Trying to dispose element udpsrc1, but it is in PAUSED instead of the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.
This problem may also be caused by a refcounting bug in the
application or some element.


GThread-ERROR **: file /build/buildd/glib2.0-2.24.1/gthread/gthread-posix.c: line 171 (g_mutex_free_posix_impl): error 'Dispositivo ó recurso ocupado' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'
aborting...
** (firefox-bin:2302): DEBUG: 0xaea95680: "NameOwnerChanged old-owner ':1.195' new-owner ''"
** (firefox-bin:2302): DEBUG: 0xaea95680: "Viewer lost connection!"

```

This is what my friends get when playing stream normally (no errors):

```
TotemEmbedded-Message: Viewer state: STOPPED
** (firefox-bin:6070): DEBUG: SetWindow reply
** (firefox-bin:6070): DEBUG: 0xa49eae00: "ViewerReady"
** (firefox-bin:6070): DEBUG: 0xa49eae00: "Stream requested (force viewer: 0)"
TotemEmbedded-Message: totem_embedded_open_uri: uri rtsp://samarina.no-ip.info:8080/live/mpeg4 base_uri: empty.mov
TotemEmbedded-Message: totem_embedded_clear_playlist
Emptying current_uri
totem_embedded_set_uri uri rtsp://samarina.no-ip.info:8080/live/mpeg4 base empty.mov => resolved rtsp://samarina.no-ip.info:8080/live/mpeg4 (subtitle (null) => resolved (null))
TotemEmbedded-Message: totem_embedded_open_internal 'rtsp://samarina.no-ip.info:8080/live/mpeg4' subtitle '(null)' is-browser-stream 0 start-play 1
TotemEmbedded-Message: Viewer state: PLAYING
** (firefox-bin:6070): DEBUG: OpenURI reply
** (firefox-bin:6070): DEBUG: 0xa49eae00: "Command 'Play'"
TotemEmbedded-Message: totem_embedded_do_command: Play
```

We're using same plugins, and same firefox version. 

Could anyone help with this issue?

Best regards,
jpc

---

### Post by Yellow Pasque on 2010-09-25
Not sure about the error, but you might want to try gecko-mediaplayer instead of the totem-mozilla plugin.

---

### Post by jpc2879 on 2010-09-25
> **Temüjin said:**
> Not sure about the error, but you might want to try gecko-mediaplayer instead of the totem-mozilla plugin.

I've tried this before, but it doesn't work either.

---

### Post by lovinglinux on 2010-09-25
See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by jpc2879 on 2010-09-25
> **lovinglinux said:**
> See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

This tutorial is very old. I've installed medibuntu as well, but same thing happens.

---

### Post by lovinglinux on 2010-09-25
> **jpc2879 said:**
> This tutorial is very old.

It doesn't mean it's outdated. The author updates it. Besides, is a sticky.

> **jpc2879 said:**
>  I've installed medibuntu as well, but same thing happens.

Have you followed the tutorial or simply ignored it because of the date?

---

### Post by jpc2879 on 2010-09-26
> **lovinglinux said:**
> It doesn't mean it's outdated. The author updates it. Besides, is a sticky.

Latest revision: 28TH NOVEMBER, 2009


> **lovinglinux said:**
> Have you followed the tutorial or simply ignored it because of the date?

Yes, but it didn't work for me. I'm still getting same error.

---

