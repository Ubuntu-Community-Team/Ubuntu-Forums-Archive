---
title: "Java in firefox"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by mrtn-- on 2007-08-22
Hi,

How do I install the java plugin for firefox? I've installed Java 6.0 Web start, but firefox still can't show java. I've read [https://help.ubuntu.com/community/Java#head-7f353d2f3fb1a09aac09cf1caee565e897319306](https://help.ubuntu.com/community/Java#head-7f353d2f3fb1a09aac09cf1caee565e897319306) but i simply don't understand the instructions, they're too laconic.

Happy for any help I can get.

Mårten

---

### Post by RomeReactor on 2007-08-22
Hi. Try [this thread]("http://ubuntuforums.org/showthread.php?t=506138").

---

### Post by mrtn-- on 2007-08-22
Thanks for your help!

I installed the packages according to the instructions in that thread, and now I can use java applets in the browser. However, everytime I load a java applet it says that it cannot renew the cache and I get the following error message:

sun.plugin.cache.JarCacheVersionException: Antalet attribut som angetts i 'cache_archive' överensstämmer inte med dem i 'cache_version'

That is "the number of attributes stated in the 'cache_archive' does not correspond to those in the 'cache_version'"

	at sun.plugin.cache.JarCacheUtil.getJarsWithVersion(JarCacheUtil.java:68)
	at sun.plugin.AppletViewer.initJarVersionMap(AppletViewer.java:738)
	at sun.plugin.AppletViewer.createClassLoader(AppletViewer.java:794)
	at sun.plugin.AppletViewer.appletInit(AppletViewer.java:678)
	at sun.plugin.viewer.LifeCycleManager.initAppletPanel(LifeCycleManager.java:166)
	at sun.plugin.viewer.MNetscapePluginObject$Initer.run(MNetscapePluginObject.java:448)

---

