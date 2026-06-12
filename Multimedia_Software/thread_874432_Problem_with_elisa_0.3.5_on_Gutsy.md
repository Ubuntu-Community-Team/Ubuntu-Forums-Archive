---
title: "Problem with elisa 0.3.5 on Gutsy"
date: 2008-07-29
forum: Multimedia Software
---

### Post by the guitarist on 2008-07-29
hello everyone ...

i installed elisa media center 0.3.2 and then added the elisa rep. to the source.list and upgraded it to 0.3.5 but now whenever i run the app i see the splash screen and that's it..any ideas?...

whenever i try to run from the terminal i get this error :

the-guitarist@the-guitarist:~$ elisa
WARN  MainThread      media_manager               Jul 30 06:38:08  Creating provider media_ugly:shoutcast_media failed. A full traceback can be found at /tmp/elisa_fukGEn.txt (elisa/core/manager.py:103)
WARN  MainThread      service_manager             Jul 30 06:38:08  Creating provider coherence_plugin:coherence_service failed. A full traceback can be found at /tmp/elisa_eGkWrX.txt (elisa/core/manager.py:103)
WARN  MainThread      metadata_manager            Jul 30 06:38:08  Creating provider media_good:gst_metadata failed. A full traceback can be found at /tmp/elisa_NLoKWR.txt (elisa/core/manager.py:103)
WARN  MainThread      media_manager               Jul 30 06:38:08  Initializing fspot:fspot_media failed: Component fspot_media failed to initialize: FSpot DB not found at '/home/the-guitarist/.gnome2/f-spot/photos.db'. (elisa/core/manager.py:95)
WARN  MainThread      media_manager               Jul 30 06:38:08  Creating provider coherence_plugin:upnp_media failed. A full traceback can be found at /tmp/elisa_NTaCS2.txt (elisa/core/manager.py:103)
WARN  MainThread      media_manager               Jul 30 06:38:08  Creating provider media_bad:ipod_media failed. A full traceback can be found at /tmp/elisa_nDtpjC.txt (elisa/core/manager.py:103)
WARN  MainThread      metadata_manager            Jul 30 06:38:08  Creating provider media_good:taglib_metadata failed. A full traceback can be found at /tmp/elisa_NSoE19.txt (elisa/core/manager.py:103)
WARN  MainThread      metadata_manager            Jul 30 06:38:08  Creating provider media_good:cover_in_dir failed. A full traceback can be found at /tmp/elisa_qoRe7i.txt (elisa/core/manager.py:103)
WARN  MainThread      media_manager               Jul 30 06:38:08  Creating provider media_good:elisa_media failed. A full traceback can be found at /tmp/elisa_0DSiP8.txt (elisa/core/manager.py:103)
WARN  MainThread      metadata_manager            Jul 30 06:38:08  Creating provider media_good:cover_cache failed. A full traceback can be found at /tmp/elisa_fhTyoZ.txt (elisa/core/manager.py:103)
WARN  MainThread      metadata_manager            Jul 30 06:38:08  Creating provider media_good:amazon_covers failed. A full traceback can be found at /tmp/elisa_quyMBb.txt (elisa/core/manager.py:103)
WARN  MainThread      media_manager               Jul 30 06:38:08  Creating provider media_good:gnomevfs_media failed. A full traceback can be found at /tmp/elisa_T6jlXm.txt (elisa/core/manager.py:103)
WARN  MainThread      interface_controller        Jul 30 06:38:08  Cannot create activity 'base:elisa_activity' for backend 'backend1' (elisa/core/interface_controller.py:180)
WARN  MainThread      interface_controller        Jul 30 06:38:08  An error occured causing backend 'backend1' creation to fail. A full traceback can be found here: /tmp/elisa_Jc_E23.txt (elisa/core/interface_controller.py:136)
WARN  MainThread      interface_controller        Jul 30 06:38:08  Backend 'backend1' not existing for frontend 'frontend1' (elisa/core/interface_controller.py:233)
WARN  MainThread      interface_controller        Jul 30 06:38:08  An error occured causing frontend 'frontend1' creation to fail. A full traceback can be found here: /tmp/elisa_wiogHn.txt (elisa/core/interface_controller.py:148)
WARN  MainThread      twisted                     Jul 30 06:38:08  A twisted traceback occurred. (twisted/internet/defer.py:402)

Twisted traceback:
Traceback (most recent call last):
Failure: twisted.internet.error.ConnectError: An error occurred while connecting: 113: No route to host.

WARN  MainThread      twisted                     Jul 30 06:38:21  A twisted traceback occurred. (twisted/internet/defer.py:402)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 343, in stop
    self.fireSystemEvent("shutdown")
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 400, in fireSystemEvent
    DeferredList(defrList).addBoth(self._cbContinueSystemEvent, eventType)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 210, in addBoth
    callbackKeywords=kw, errbackKeywords=kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 182, in addCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 317, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 406, in _cbContinueSystemEvent
    self._continueSystemEvent(eventType)
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 411, in _continueSystemEvent
    for callList in sysEvtTriggers[1], sysEvtTriggers[2]:
exceptions.TypeError: 'NoneType' object is unsubscriptable

plz help i really need a media center at the moment..thanx alot in advance

---

