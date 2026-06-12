---
title: "rythembox and banshee won't play  mp3s on lubuntu"
date: 2013-04-13
forum: Multimedia Software
---

### Post by andrewrz on 2013-04-13
I have installed lubuntu-restricted-extras, but  both programs crash  after about 30 seconds when playing mp3's. I have tried on three vary different systems running lubuntu and the results are the same.  
           
this is a log from banshee.. 

"exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  05:29:39.925] Running Banshee 2.6.0: [Ubuntu 12.10 (linux-gnu, x86_64) @ 2012-12-12 06:24:28 UTC]
[Info  05:29:40.827] Updating web proxy from GConf
[Warn  05:29:40.896] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  05:29:40.896] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Warn  05:29:40.897] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  05:29:40.897] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  05:29:40.898] All services are started 0.808738
[Info  05:29:41.262] AmazonMP3 store redirect URL: [https://one.ubuntu.com/music/store/amz/](https://one.ubuntu.com/music/store/amz/)
[Info  05:29:41.642] nereid Client Started
[Info  05:29:41.714] GStreamer version 0.10.36.0, gapless: True, replaygain: False

(Banshee:4674): GStreamer-CRITICAL **: gst_element_query: assertion `GST_IS_ELEMENT (element)' failed
(!) [ 4695:    0.000] --> Caught signal 24 (unknown origin) <--
(!) [ 4681:    0.000] --> Caught signal 24Stacktrace:

 (unknown origin) <--
(!) [ 4693:    0.000] --> Caught signal 24 (unknown origin) <--"

thanks

---

