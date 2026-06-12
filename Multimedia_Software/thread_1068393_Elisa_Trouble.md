---
title: "Elisa Trouble"
date: 2009-02-12
forum: Multimedia Software
---

### Post by PJFinega on 2009-02-12
I read in an article today about Elisa a cool media program, tried to load it, but when I run it I get these errors.

$ elisa
Launcher core version: 0.5.27
Current core version: 0.5.27
/usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
WARN  MainThread      plugin_registry             Feb 12 21:36:19  plugin Louie has the following unmet dependencies: nose>=0.8.3 (elisa/core/plugin_registry.py:343)
WARN  MainThread      plugin_registry             Feb 12 21:36:19  plugin Coherence has the following unmet dependencies: nose>=0.8.3 (elisa/core/plugin_registry.py:343)
WARN  MainThread      plugin_registry             Feb 12 21:36:19  plugin elisa-plugin-coherence has the following unmet dependencies: coherence>=0.5.7 (elisa/core/plugin_registry.py:343)
ERROR: couldn't create the window, exiting...

I poked around online, but couldn't find any solutions. Can you help me Ubuntu forums?

Sorry it's Ubuntu not Kubuntu.

---

### Post by kr4zyc1d on 2009-02-17
I also ran the installer to see if I could mimic the errors.  I had similar issues.  It installed fine, however, when it was run, I saw the splash logo and my screen turned black and I received flashing images of what appeared to be a failed attempt to load a menu page.  My errors are as follows:

WARN  MainThread      plugin_registry             Feb 17 23:01:04  plugin conflict elisa-plugin-weather 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      plugin_registry             Feb 17 23:01:04  plugin conflict elisa-plugin-coherence 0.1 (elisa/core/plugin_registry.py:220)
WARN  MainThread      resource_manager            Feb 17 23:01:04  Creating discogs.discogs_resource:DiscogsResource failed. A full traceback can be found at /tmp/elisa_z6L5SC.txt (elisa/core/manager.py:83)
WARN  MainThread      gst_metadata_slave_process_protocol Feb 17 23:01:05  Starting Slave-2 on unix:/tmp/elisa-metadata-iP3LXz.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-2 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Feb 17 23:01:05  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-2 stderr) (elisa/plugins/amp/master.py:57)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating weather.report_provider:WeatherReportProvider failed. A full traceback can be found at /tmp/elisa_3VQD_P.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating youtube.resource_provider:YoutubeResourceProvider failed. A full traceback can be found at /tmp/elisa_Xu3_60.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating shoutcast.shoutcast_resource:ShoutcastResource failed. A full traceback can be found at /tmp/elisa_aqSX0l.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating flickr.resource_provider:FlickrResourceProvider failed. A full traceback can be found at /tmp/elisa_T2Uhml.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating wmd.wmd_resource:WMDResource failed. A full traceback can be found at /tmp/elisa_tHw6jD.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating coherence.coherence_resource:CoherenceResource failed. A full traceback can be found at /tmp/elisa_MOdzap.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating coherence.upnp_resource:UpnpResource failed. A full traceback can be found at /tmp/elisa_ota-YO.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:05  Creating smbwin32.smbwin32_resource:SmbWin32Resource failed. A full traceback can be found at /tmp/elisa_fHpRM8.txt (elisa/core/manager.py:83)
WARN  MainThread      resource_manager            Feb 17 23:01:06  Creating yesfm.yesfm_resource:YesfmResource failed. A full traceback can be found at /tmp/elisa_-oNc4D.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Feb 17 23:01:06  Creating coherence.coherence_service:CoherenceService failed. A full traceback can be found at /tmp/elisa_0nag6g.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Feb 17 23:01:06  Creating osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_N0GEh0.txt (elisa/core/manager.py:83)
WARN  MainThread      service_manager             Feb 17 23:01:06  Creating gnome.gnome_screensaver_service:GnomeScreensaverService failed. A full traceback can be found at /tmp/elisa_R3DpLI.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Feb 17 23:01:06  Creating winremote.streamzap_input:StreamzapInput failed. A full traceback can be found at /tmp/elisa_sWscYh.txt (elisa/core/manager.py:83)
WARN  MainThread      input_manager               Feb 17 23:01:06  Creating lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_sKimkO.txt (elisa/core/manager.py:83)
WARNING:root:Cannot find resource file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/widgets/resources.conf
WARN  MainThread      gst_metadata_slave_process_protocol Feb 17 23:01:07  Starting Slave-6 on unix:/tmp/elisa-metadata-4LrF_p.socket launching elisa.plugins.gstreamer.amp_slave.run_slave
(Slave-6 stdout) (elisa/plugins/amp/master.py:54)
WARN  MainThread      gst_metadata_slave_process_protocol Feb 17 23:01:08  /usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
(Slave-6 stderr) (elisa/plugins/amp/master.py:57)
WARN  MainThread      twisted                     Feb 17 23:01:08  A twisted traceback occurred. (twisted/internet/defer.py:415)

Twisted traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 195, in addCallback
    callbackKeywords=kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 186, in addCallbacks
    self._runCallbacks()
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 328, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/application.py", line 479, in interface_controller_stopped
    manager_deferreds.append(defer.maybeDeferred(manager.stop))
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 106, in maybeDeferred
    result = f(*args, **kw)
  File "/usr/lib/python2.5/site-packages/elisa/core/input_manager.py", line 77, in stop
    self._poll_call.stop()
  File "/usr/lib/python2.5/site-packages/twisted/internet/task.py", line 91, in stop
    assert self.running, ("Tried to stop a LoopingCall that was "
exceptions.AssertionError: Tried to stop a LoopingCall that was not running.


No such luck yet, will check back soon.  Thanks.

---

### Post by PJFinega on 2009-02-17
Okay, navigate to the Elisa install web page and scroll down to the part below the install button where it talks about PPA, install the sources, the key and then click on the coherence arrow and install then update it with the links at the bottom. After that I still get this however:

~$ elisa
Launcher core version: 0.5.27
Current core version: 0.5.27
/usr/lib/python2.5/site-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
ERROR: couldn't create the window, exiting...

---

