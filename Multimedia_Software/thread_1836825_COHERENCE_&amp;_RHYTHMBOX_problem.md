---
title: "COHERENCE &amp; RHYTHMBOX problem"
date: 2011-08-31
forum: Multimedia Software
---

### Post by erresse on 2011-08-31
Good day to all;

Running Rhthmbox , here is what i have:


(rhythmbox:8310): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(rhythmbox:8310): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
WARN  coherence                   août 31 22:41:56  Coherence UPnP framework version 0.6.6.2 starting... (coherence/base.py:283)
WARN  webserver                   août 31 22:41:56  WebServer on port 34331 ready (coherence/base.py:124)
WARN  rb_coherence_plugin         août 31 22:41:56  Media Store available with UUID uuid:9ec698a9-a4f7-496c-a656-f070464fb980 (coherence/__init__.py:131)
WARN  rb_coherence_plugin         août 31 22:41:56  Media Renderer available with UUID uuid:36a1b9ad-83de-4086-9df4-818f9088bdec (coherence/__init__.py:165)
WARN  rb_coherence_plugin         août 31 22:41:56  start looking for media servers (coherence/__init__.py:168)

(rhythmbox:8310): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
WARN  rb_media_store              août 31 22:41:57  __init__ MediaStore {'urlbase': 'http://192.168.0.14:34331/9ec698a9-a4f7-496c-a656-f070464fb980', 'no_thread_needed': True, 'uuid': 'uuid:9ec698a9-a4f7-496c-a656-f070464fb980', 'plugin': <CoherencePlugin object at 0x9aa8f2c (RBPlugin at 0x8d37c80)>, 'db': <__main__.RhythmDBTree object at 0x95103ec (RhythmDBTree at 0x8d69010)>, 'version': 2} (coherence/MediaStore.py:345)
WARN  rb_media_renderer           août 31 22:41:57  __init__ RhythmboxPlayer {'shell': <rb.Shell object at 0x92dab94 (RBShell at 0x8d30078)>, 'no_thread_needed': True, 'uuid': 'uuid:36a1b9ad-83de-4086-9df4-818f9088bdec', 'urlbase': 'http://192.168.0.14:34331/36a1b9ad-83de-4086-9df4-818f9088bdec', 'version': 2, 'rb_mediaserver': <coherence.upnp.devices.media_server.MediaServer object at 0xa1147cc>} (coherence/MediaPlayer.py:40)
/usr/lib/pymodules/python2.7/coherence/extern/louie.py:44: UserWarning: extern.louie will soon be deprecated in favor of coherence.dispatcher.
  warnings.warn("extern.louie will soon be deprecated in favor of coherence.dispatcher.")



I am under Ubuntu 11.04, Rhythmbox 0.13.3, with coherence plugin installed.

The DLNA function client is not working anymore while was OK in previous Ubuntu 10.x.....
Impossible to see my DLNA server (a QNAP server).

How can i solve this ???? Any suggestion is welcome

Regards and thanks for help

---

