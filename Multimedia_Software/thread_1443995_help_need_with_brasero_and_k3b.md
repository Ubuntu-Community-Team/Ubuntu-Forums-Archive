---
title: "help need with brasero and k3b"
date: 2010-03-31
forum: Multimedia Software
---

### Post by slick1a on 2010-03-31
Hi guys and gals, 

I have been using brasero for some time successfully, however since upgrading to current distro i noticed the general layout of brasero has changed.

normally if i wanted to burn a few avi files to a dvd- disk which i have done many times ( for the purpose of freeing up space on my HD) the process was straight forward.

select data project 
select required avi files
select burn  and voila.

now brasero only gives me the option to burn image files  < not what i want

---

### Post by slick1a on 2010-04-10
In short im unable to burn anything the way i want too...

the only file path choice i have is an image file ..why is this?

---

### Post by slick1a on 2010-04-20
Having trawlled forums it seems lots of people are having issues with the azureus.jar file update being on a loop or successfully downloading only to be asked to do this again?

Topping this my 'PLACES' bar opens everthing in VLC instead of Nautilus ?????????????? WHY???

HOw can i fix this??

My results thus far: 

slick@slick-desktop:~$ sudo azureus
file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/swt-gtk-3.4.jar ; file:/home/slick/

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed

(SWT:4127): Gdk-CRITICAL **: gdk_window_get_user_data: assertion `window != NULL' failed
DownloadManager::addDownloadManager: fails - td = null, fd = null
DEBUG::Tue Apr 20 23:52:28 BST 2010::org.gudy.azureus2.core3.global.impl.GlobalManagerImpl::addDownloadManager::720:
  java.io.IOException: Input/output error
	at java.io.UnixFileSystem.createFileExclusively(Native Method)
	at java.io.File.createNewFile(File.java:900)
	at org.gudy.azureus2.core3.util.TorrentUtils.copyTorrentFileToSaveDir(TorrentUtils.java:2136)
	at org.gudy.azureus2.core3.global.impl.GlobalManagerImpl.addDownloadManager(GlobalManagerImpl.java:656)
	at org.gudy.azureus2.core3.global.impl.GlobalManagerImpl.addDownloadManager(GlobalManagerImpl.java:571)
	at org.gudy.azureus2.pluginsimpl.local.download.DownloadManagerImpl.addDownload(DownloadManagerImpl.java:390)
	at org.gudy.azureus2.pluginsimpl.local.download.DownloadManagerImpl.addDownload(DownloadManagerImpl.java:319)
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderTorrentImpl.downloadTorrent(ResourceDownloaderTorrentImpl.java:307)
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderTorrentImpl.asyncDownload(ResourceDownloaderTorrentImpl.java:271)
	at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderAlternateImpl.asyncDownload(ResourceDownloaderAlternateImpl.java:261)
	at org.gudy.azureus2.ui.swt.update.UpdateWindow.nextUpdate(UpdateWindow.java:546)
	at org.gudy.azureus2.ui.swt.update.UpdateWindow.update(UpdateWindow.java:539)
	at org.gudy.azureus2.ui.swt.update.UpdateWindow.access$000(UpdateWindow.java:61)
	at org.gudy.azureus2.ui.swt.update.UpdateWindow$5.handleEvent(UpdateWindow.java:276)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3401)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3033)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:183)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:67)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:84)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:216)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)

ideas ???

---

