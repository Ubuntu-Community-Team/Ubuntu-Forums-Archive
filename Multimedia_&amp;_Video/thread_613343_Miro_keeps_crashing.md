---
title: "Miro keeps crashing"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-11-14
Hi, 

Every time it looks like everything's loaded in miro, it crashes.  Here's the output from the terminal.  Any ideas?

Thanks 

```

douglas@douglas-desktop:~$ miro
/var/lib/python-support/python2.5/dbus_bindings.py:1: DeprecationWarning: The dbus_bindings module is not public API and will go away soon.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
INFO     Starting up Miro
INFO     Version:  0.9.8.1
INFO     Revision: unknown
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/douglas/.miro/sqlitedb
TIMING   Database load slow: 1.644
INFO     Recomputing filters...
INFO     Spawning auto downloader...
INFO     Spawning idle notifier
INFO     idle notifier running
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "CheckVersion" not implemented
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
alsa
oss
pulseaudio
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a08f7c> took too long: 1.818
TIMING   gtkSyncMethod: <function getDisplay at 0x8a9b09c> took too long: 2.016
INFO     got file:///tmp/tmp57yVEI.html
TIMING   Icon clear: 0.525
INFO     Finished startup sequence
TIMING   idle (Finishing startup) too slow (5.770 secs)
TIMING   idle (Finishing startup) cumulative is too slow (5.770 secs)
INFO     got file:///tmp/tmpaBhDrc.html
INFO     *** Daemon ready ***
INFO     got https://www.miroguide.com/
TIMING   feed update for: http://revision3.com/diggnation/feed/quicktime-large too slow (0.175 secs)
TIMING   feed update for: http://jetset.blip.tv/?skin=rss too slow (0.195 secs)
TIMING   feed update for: http://www.onnetworks.com/videos/shows/25/podcast/hd too slow (0.106 secs)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
douglas@douglas-desktop:~$ 

```

---

### Post by rcmn on 2007-11-14
same here .I have kubuntu 7.10 fresh install .And miro(1.0.2) is very sludgy and crash randomly.
Hope it'll get better because i like the idea.
nb:it never really worked well for me.always experienced that kind behavior.

---

### Post by maluka on 2007-11-14
have you installed the latest Miro build?

---

### Post by sloggerkhan on 2007-11-14
```
$ miro
/usr/lib/firefox
INFO     Starting up Miro
INFO     Version:    1.0
INFO     Revision:   unknown
INFO     Builder:    willg@jupiter
INFO     Build Time: 1194972179.14
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/redice/.miro/sqlitedb
TIMING   Database load slow: 0.408
TIMING   idle (Initializing database) too slow (0.582 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
INFO     Creating video display...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x87901b4> took too long: 3.006
TIMING   gtkSyncMethod: <function getDisplay at 0x87b54c4> took too long: 3.168
INFO     First URL is https://www.miroguide.com/
TIMING   Icon clear: 1.473
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (5.094 secs)
TIMING   idle (finalizing startup) cumulative is too slow (5.094 secs)
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmp4RtNoB.html
TIMING   gtkAsyncMethod: <function selectDisplay at 0x87b5454> took too long: 1.861
INFO     got file:///tmp/tmpjTH8cQ.html
INFO     got https://www.miroguide.com/
TIMING   WARNING: Calling <function <lambda> at 0x89d0a3c> on HTTPClient: http://panther2.video.blip.tv/user_photo_richie b547.jpg too slow (1.641 secs)
TIMING   timeout (Save database) too slow (0.571 secs)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
$ 
```
Does pretty much the same thing on my computer. This is with the ubunty gutsy deb for their "1.0" release or 1.0 and whatever bits.

---

### Post by vagamente on 2007-11-15
The same for me... but solved with this [http://ubuntuforums.org/showthread.php?t=588617](http://ubuntuforums.org/showthread.php?t=588617)

---

### Post by rcmn on 2007-11-15
> **vagamente said:**
> The same for me... but solved with this [http://ubuntuforums.org/showthread.php?t=588617](http://ubuntuforums.org/showthread.php?t=588617)

I didn't realize Miro was dealing with the coffee stuff ...No wonder !!! 
So i solved it
```

#sudo apt-get remove miro && apt-get autoremove

```

---

### Post by djrobthaman on 2007-11-15
Maluka, I have the version in the default gutsy repositories.  The version number listed is something like 9.8.1 or 9.7.1, so I'm assuming that means 1.0.

Vagamente, thanks for the link.  Did you notice any issues with changing from java to iced tea??? I know that iced tea is the open source version which I was actually going to change to in the long run, but I've also seen people say it isn't on par yet with the closed source version.

---

### Post by djrobthaman on 2007-11-15
Also, thanks for all the quick responces






[SIZE="1"]Yay for post 200 :)[/SIZE]

---

### Post by MozartlovesUbun2 on 2007-11-15
Same here
===============

mozart@network:~$ miro
/usr/lib/firefox
INFO     Starting up Miro
INFO     Version:    1.0
INFO     Revision:   unknown
INFO     Builder:    willg@jupiter
INFO     Build Time: 1195054435.77
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/mozart/.miro/sqlitedb
TIMING   Database load slow: 1.254
TIMING   idle (Initializing database) too slow (1.930 secs)
INFO     Spawning auto downloader...
INFO     Spawning idle notifier
INFO     idle notifier running
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
INFO     loaded renderer 'xinerenderer'
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     got file:///tmp/tmpTzqgR6.html
TIMING   Icon clear: 0.238
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.497 secs)
INFO     got file:///tmp/tmpcLr-Zf.html
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     *** Daemon ready ***
INFO     got [https://www.miroguide.com/](https://www.miroguide.com/)
GCJ PLUGIN: thread 0x8230bf0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x8230bf0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x8230bf0: NP_GetValue
GCJ PLUGIN: thread 0x8230bf0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x8230bf0: NP_GetValue return
GCJ PLUGIN: thread 0x8230bf0: NP_GetValue
GCJ PLUGIN: thread 0x8230bf0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x8230bf0: NP_GetValue return
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
mozart@network:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

---

### Post by MozartlovesUbun2 on 2007-11-15
ok I closed Firefox which had google mail chat open and after that now MORO opens normally!

so does google chat  use java, theres a conflict there with miro or something?

---

### Post by rcmn on 2007-11-15
> **MozartlovesUbun2 said:**
> ok I closed Firefox which had google mail chat open and after that now MORO opens normally!

so does google chat  use java, theres a conflict there with miro or something?

:lolflag:

Sorry i have to stop following that thread or i'll spill my coffee again ...

---

### Post by tacone on 2008-01-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/miro/+bug/182383](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/182383) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Workaround (quality is worse), tested with 1.1-1
(you can get the .deb here: [http://www.getmiro.com/download/ubuntu.php](http://www.getmiro.com/download/ubuntu.php) )

- At command line type: gconf-editor
- find and select /apps/miro
- right click in the right pane and add a new key.
- key name: renderers
- type: list
- list type: string
- add a single value: gstrenderer

Now launch and enjoy Miro withotu crashes !

The bug on launchpad (could get updated with better solution)
[https://bugs.launchpad.net/ubuntu/+source/miro/+bug/182383](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/182383)

---

