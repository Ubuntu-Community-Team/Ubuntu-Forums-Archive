---
title: "Democracy player crashing at start"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by rpasell on 2007-02-15
Hi,

Just installed Democracy player and tried to run it, but it started then disappeared.  I ran it from command line and got the following

DTV: Spawning auto downloader...
DTV: Spawning idle notifier
DTV: idle notifier running
DTV: Displaying main frame...
DTV: Starting event loop thread
DTV: updating the Guide
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/gtk_queue.py:103: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
WARNING: idle (http auth callback) too slow (0.655 secs)
*** Launching Democracy Downloader Daemon ****
*** Daemon ready ***
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/gtk_queue.py:119: GtkDeprecationWarning: gtk.threads_leave is deprecated, use gtk.gdk.threads_leave instead
  gtk.threads_leave()
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory
downloader: connection closed -- quitting
Shutting down downloaders...


Is this a problem with the java version I have installed?  I'm running x64 edgy.

---

### Post by cabinda on 2007-02-20
I am having a similar problem.  When I start Democracy TV, it crashes.  From the terminal:
```

jason@ubuntu:~$ democracyplayer 
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/Application.py:30: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()
DTV: Starting up Democracy Player
DTV: Version:  0.9.2.1
DTV: Revision: unknown
DTV: Loading preferences...
DTV: Restoring database...
DTV: Recomputing filters...
DTV: Spawning global feed dtv:manualFeed
DTV: Spawning global feed dtv:search
DTV: Spawning global feed dtv:searchDownloads
DTV: Spawning Channel Guide...
DTV: Spawning global feed dtv:directoryfeed
DTV: Spawning auto downloader...
DTV: Spawning idle notifier
DTV: idle notifier running
DTV: Displaying main frame...
DTV: Starting event loop thread
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/gtk_queue.py:103: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
*** Launching Democracy Downloader Daemon ****
*** Daemon ready ***
DTV: updating the Guide
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: RemoveVideos: missing action
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: find_menu_position: assertion `GTK_IS_WIDGET (prev_child)' failed
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: CopyVideoURL: missing action
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: Channels: missing action
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: NewChannel: missing action
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: NewSearchChannel: missing action
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: NewChannelFolder: missing action
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
/usr/lib/python2.4/site-packages/democracy/frontend_implementation/MainFrame.py:149: GtkWarning: NewGuide: missing action
  self.widgetTree['menubar-box'].add (self.uiManager.get_widget('/menubar'))
downloader: connection closed -- quitting
Shutting down downloaders...
Segmentation fault (core dumped)
```

System is x86.

---

