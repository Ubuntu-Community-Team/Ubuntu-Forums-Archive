---
title: "Elisa Plugin Help"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Vaelrith on 2008-04-30
I installed Elisa from the 8.04 repositories.  Whenever I click on the plugin icon (the gear) in Elisa, nothing happens.  Am I doing something wrong?  I was under the assumption that installing from the repositories came with some plugins.  Do I have to install them myself?

Thanks

---

### Post by fenrir12 on 2008-04-30
I am having the same issues. It seems like a bugged program in general. Does anyone know whether, with the correct plugins, my xbox 360 will treat Elisa as it would Windows Media Center?

---

### Post by Rever75 on 2008-05-06
I am having the same issue on Hardy too. I can go to config but I only see themes. I thought there would be more. I also click on the gear and it does nothing. This is what I am getting when I run it from CLI.

```
(elisa:12685): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstcdio.so': libcdio.so.6: cannot open shared object file: No such file or directory

(elisa:12685): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': libx264.so.54: cannot open shared object file: No such file or directory
WARN  MainThread      service_manager             May 06 13:20:15  Missing dependency Un-met dependency for coherence: coherence to create coherence:coherence_service (elisa/core/manager.py:98)
WARN  MainThread      media_manager               May 06 13:20:15  Missing dependency Un-met dependency for coherence: coherence to create coherence:upnp_media (elisa/core/manager.py:98)
WARN  MainThread      service_manager             May 06 13:20:15  Initializing osso:osso_service failed: Component osso_service failed to initialize: hildon not running. (elisa/core/manager.py:95)
elisa: could not connect to socket
elisa: No such file or directory
WARN  MainThread      interface_controller        May 06 13:20:17  Component lirc_input failed to initialize: Unable to initialize lirc! (elisa/core/interface_controller.py:326)
WARN  MainThread      comp_service_activity       May 06 13:20:17  Plugin 'service' not found (elisa/plugins/base/activities/service_activity.py:54)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      db_backend                  May 06 13:20:19  column uri is not unique (elisa/core/db_backend.py:240)
WARN  MainThread      twisted                     May 06 13:20:19  A twisted traceback occurred. (twisted/internet/base.py:535)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 175, in run
    self.__run()
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 114, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 207, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 216, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 533, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/bus/bus.py", line 178, in _dispatch
    callback(message, sender)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/media_db/media_scanner.py", line 206, in _bus_media_location_message_cb
    self.add_source(uri, message.media_types)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/media_db/media_scanner.py", line 227, in add_source
    requested_media_types=media_types)
  File "/usr/lib/python2.5/site-packages/elisa/plugins/media_db/media_scanner.py", line 266, in _schedule_source_update
    if not self._media_manager.is_scannable(source_uri):
  File "/usr/lib/python2.5/site-packages/elisa/core/media_manager.py", line 248, in is_scannable
    provider = self._get_media_provider(uri)
  File "/usr/lib/python2.5/site-packages/elisa/core/media_manager.py", line 234, in _get_media_provider
    raise MediaProviderNotFound(uri)
elisa.core.media_manager.MediaProviderNotFound: No MediaProvider found for dvd:// URI

[]
WARN  MainThread      config                      May 06 13:20:24  [Errno 13] Permission denied: u'/usr/lib/python2.5/site-packages/elisa/plugins/raval_frontend/tango_theme/tango_theme.conf' (elisa/core/config.py:195)
WARN  MainThread      twisted                     May 06 13:20:24  A twisted traceback occurred. (twisted/internet/defer.py:402)

Twisted traceback:
Traceback (most recent call last):
Failure: twisted.spread.pb.PBConnectionLost: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ProcessDone'>: A process has ended without apparent errors: process finished with exit code 0.
]

```

---

### Post by Ekeluo on 2008-05-12
There are no plugins setup shipping with the repo versions yet, they're expected for the next release (a little bit more patience:popcorn:).

---

