---
title: "[SOLVED] Miro crashes on startup"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by papatrpt89 on 2007-10-23
Hey all,

I am having some problems with Miro.  I'm running Gutsy, 32-bit, though I had this problem with Feisty as well (the Gutsy is a clean install).  It worked for a little while after installation, then after adding some channels, downloading some content from them, and watching some of them, it now crashes on startup.  I find that if I click off of the Miro Guide on startup, to one of my channels, it doesn't crash.

So, my guess is something is wrong with the mozilla engine?

If I run Miro from a terminal, I get the following:
```
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
INFO     Connecting to /home/john/.miro/sqlitedb
TIMING   Database load slow: 0.765
INFO     Recomputing filters...
INFO     Spawning auto downloader...
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
esd
none
file
INFO     loaded renderer 'xinerenderer'
INFO     got file:///tmp/tmpPHds84.html
TIMING   Icon clear: 0.294
INFO     Finished startup sequence
TIMING   idle (Finishing startup) too slow (2.572 secs)
INFO     got file:///tmp/tmpYOA9-0.html
INFO     *** Daemon ready ***
INFO     got https://www.miroguide.com/
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
```
Then it dumps me back to a terminal.

So, I guess I could use that workaround, but I shouldn't really have to.  Any ideas?

---

### Post by aidanr on 2007-10-23
You could compile the latest version it might be fixed since 0.9.8.1
[https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs)

---

### Post by papatrpt89 on 2007-10-23
> **aidanr said:**
> You could compile the latest version it might be fixed since 0.9.8.1
[https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/projects/dtv/wiki/GTKX11BuildDocs)

Thanks for the quick reply!  After building the latest source from SVN, Miro still has the same problem, with the same workaround applicable.

At least, I think this is what is happened.  This is what I get after running /tv/platform/gtk-x11/run.sh from a terminal (after compilation):

```
running install
running build
running build_py
copying /home/john/tv/portable/dl_daemon/daemon.py -> build/lib.linux-i686-2.5/miro/dl_daemon
running build_ext
running build_scripts
copying /home/john/tv/platform/gtk-x11/miro -> build/scripts-2.5
running install_lib
copying build/lib.linux-i686-2.5/miro/dl_daemon/daemon.py -> ./dist/usr/lib/python2.5/site-packages/miro/dl_daemon
byte-compiling ./dist/usr/lib/python2.5/site-packages/miro/dl_daemon/daemon.py to daemon.pyc
running install_scripts
copying build/scripts-2.5/miro -> ./dist/usr/bin
changing mode of ./dist/usr/bin/miro to 755
changing mode of ./dist/usr/bin/miro.real to 755
running install_data
copying /home/john/tv/platform/gtk-x11/miro.1.gz -> ./dist/usr/share/man/man1
copying /home/john/tv/platform/gtk-x11/xine/xine_extractor -> ./dist/usr/libexec/
running install_egg_info
Removing ./dist/usr/lib/python2.5/site-packages/miro-1.0_svn.egg-info
Writing ./dist/usr/lib/python2.5/site-packages/miro-1.0_svn.egg-info
/var/lib/python-support/python2.5/dbus_bindings.py:1: DeprecationWarning: The dbus_bindings module is not public API and will go away soon.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
INFO     Starting up Miro
INFO     Version:    1.0-svn
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/trunk/tv - 5533
INFO     Builder:    john@gutsy-pwn
INFO     Build Time: 1193172556.73
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/john/.miro/sqlitedb
TIMING   Database load slow: 0.802
TIMING   idle (Initializing database) too slow (1.258 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     Creating video display...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     loaded renderer 'xinerenderer'
INFO     got file:///tmp/tmpkAsAxi.html
TIMING   Icon clear: 0.298
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.166 secs)
INFO     got file:///tmp/tmpyxknX0.html
INFO     *** Daemon ready ***
INFO     got https://www.miroguide.com/
INFO     Checking for updates...
INFO     moving to movies directory filename is /home/john/Movies/Miro/Incomplete Downloads/unknown.part
/usr/bin/python: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
john@gutsy-pwn:~/tv/platform/gtk-x11$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
```

Though this time it doesn't dump me back to a terminal, it hangs on the last line INFO     Shutting down downloaders...

Thanks for the help! :)  Anyone have any other ideas?

---

### Post by aay on 2007-10-25
papatrpt89,

I also get this error along with a crash.

]/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor

When I googled this line, this page is the only thing that came up.  It would be nice to be able to run Miro again.  Please post back here if you find a fix.

---

### Post by papatrpt89 on 2007-10-25
> **aay said:**
> papatrpt89,

I also get this error along with a crash.

]/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor

When I googled this line, this page is the only thing that came up.  It would be nice to be able to run Miro again.  Please post back here if you find a fix.

Will do!  Kinda funny how fast google indexes ubuntuforums.org.  I posted this thread two days ago.  Let me know if you find anything too!

---

### Post by jay_ramos on 2007-10-26
sudo apt-get install icedtea-java7-plugin
sudo update-alternatives --config java  
  *choose the icedtea plugin above*
miro

:guitar:

---

### Post by papatrpt89 on 2007-10-27
> **jay_ramos said:**
> sudo apt-get install icedtea-java7-plugin
sudo update-alternatives --config java  
  *choose the icedtea plugin above*
miro

:guitar:

Thanks!

I'm getting a different error now :p

When I run from terminal, no GUI window ever opens, and the output is:
```
/var/lib/python-support/python2.5/dbus_bindings.py:1: DeprecationWarning: The dbus_bindings module is not public API and will go away soon.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
ERROR:dbus.proxies:Introspect error on :1.44:/org/participatoryculture/dtv/OneTime: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 102, in <module>
    iface.HandleArgs(dbusargs)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 63, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 135, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 603, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Nothing about java anymore...I guess that your solution fixed that problem!

Anyone else having any similar problems?  It seems weird to me that something in the repos was broken after a small bit of normal usage.

Thanks again everyone for the replies!

---

### Post by brainkilla on 2007-10-27
I've put 
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
in my sources.list and successfully d/led and installed latest miro...

---

### Post by papatrpt89 on 2007-10-27
Everything is once again working as it should!  Miro now opens properly, downloads, stores, and plays videos as per how it is supposed to.

Just so everyone knows, here is what I did to make it work correctly, using Ubuntu Gutsy Gibbon.  For those of you who don't want to read the tedious details, here are the basics.

[SIZE=3]**General instructions**[/SIZE][LIST]
[*]Install package icedtea-java7-plugin, select it for use as your java plugin (using sudo update-alternatives --config java).
[*]Completely remove (including ~/.miro) everything related to miro.
[*]Add the following repo: ```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
```
[*]Install miro from this new repo.[/LIST][SIZE=3]**Notes**[/SIZE]
Seems that the icedtea-java7-plugin is step is not necessary for some users, sometimes just clearing the ~/.miro directory and then installing from the different repo works.  If you are nervous to change your Java plugin (for fear of other programs/applets ceasing to work), just try all steps except changing your Java.
[SIZE=3][B]
Detailed instructions[/B][/SIZE]
**Prerequisites:**
Completely remove (apt-get --purge or in Synaptic, completely remove) the packages miro, miro-data, and democracyplayer.
I cleaned my user configuration of miro as well, by deleting the folder /home/*user*/.miro

**Step 1:**
Update the java plugin that you use to icedtea-java7-plugin.
 a. Open Synaptic Package Manager, click the search button, and search for icedtea-java7-plugin, right click it, select Mark for installation, select apply.
 b. Accept any licenses that it needs, and click through the series until it is installed.
[B]
Step 2:[/B]
From a terminal, type the following:
```
sudo update-alternatives --config java
```Select the iced-tea plugin that we just installed.  For me it was called /usr/lib/jvm/java-7-icedtea/jre/bin/java

**Step 3:**
Still in Synaptic, select settings, then Repositories.  Click the Third-Party Software tab.

**Step 4:**
Click the add button, and copy and paste the following where it asks for APT line:

```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
```Click Add Source, then close the Software Sources window.

**Step 5**
Synaptic should inform you that your repositories have changed.  Close this message, then click the Reload button, near the upper left of the synaptic window.

**Step 6**
Click the Search button, and search for miro.

**Step 7**
Right click the package called miro, and select mark for installation, and click through any messages Synaptic spits back at you.  Select apply, wait for everything to finish, and you should have a working installation of miro!

Good luck!  Feel free to post back with any questions.  Thanks to everyone, especially jay_ramos and brainkilla for the help!

---

### Post by Ruazinn on 2007-10-28
papatrpt89, to get the updated miro to work, jay_ramos' java plugin fix needs to be included in the final procedure.

Thanks everyone!!! Solved my miro problems in less than 10 minutes.

---

### Post by papatrpt89 on 2007-10-28
> **Ruazinn said:**
> papatrpt89, to get the updated miro to work, jay_ramos' java plugin fix needs to be included in the final procedure.

Thanks everyone!!! Solved my miro problems in less than 10 minutes.

Glad everything is working!  I will this into the HOWTO.

---

### Post by aay on 2007-10-31
papatrpt89,

Thanks.  Miro is working fine for me now.  I did everything you suggested except I used the version of Miro in the standard Ubuntu repos.

Works fine now.

Adam

> **papatrpt89 said:**
> Everything is once again working as it should!  Miro now opens properly, downloads, stores, and plays videos as per how it is supposed to.

Just so everyone knows, here is what I did to make it work correctly, using Ubuntu Gutsy Gibbon.  For those of you who don't want to read the tedious details, here are the basics.

[SIZE="3"]**General instructions**[/SIZE]
[LIST]
[*]Install package icedtea-java7-plugin, select it for use as your java plugin (using sudo update-alternatives --config java).
[*]Completely remove (including ~/.miro) everything related to miro.
[*]Add the following repo: ```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
```
[*]Install miro from this new repo.
[/LIST]

[SIZE="3"]**Detailed instructions**[/SIZE]
**Prerequisites:**
Completely remove (apt-get --purge or in Synaptic, completely remove) the packages miro, miro-data, and democracyplayer.
I cleaned my user configuration of miro as well, by deleting the folder /home/*user*/.miro

**Step 1:**
Update the java plugin that you use to icedtea-java7-plugin.
 a. Open Synaptic Package Manager, click the search button, and search for icedtea-java7-plugin, right click it, select Mark for installation, select apply.
 b. Accept any licenses that it needs, and click through the series until it is installed.
[B]
Step 2:[/B]
From a terminal, type the following:
```
sudo update-alternatives --config java
```
Select the iced-tea plugin that we just installed.  For me it was called /usr/lib/jvm/java-7-icedtea/jre/bin/java

**Step 3:**
Still in Synaptic, select settings, then Repositories.  Click the Third-Party Software tab.

**Step 4:**
Click the add button, and copy and paste the following where it asks for APT line:

```
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
```
Click Add Source, then close the Software Sources window.

**Step 5**
Synaptic should inform you that your repositories have changed.  Close this message, then click the Reload button, near the upper left of the synaptic window.

**Step 6**
Click the Search button, and search for miro.

**Step 7**
Right click the package called miro, and select mark for installation, and click through any messages Synaptic spits back at you.  Select apply, wait for everything to finish, and you should have a working installation of miro!

Good luck!  Feel free to post back with any questions.  Thanks to everyone, especially jay_ramos and brainkilla for the help!

---

### Post by papatrpt89 on 2007-10-31
aay,

You are welcome!  Glad to hear it is working as it should!

---

### Post by philidox on 2007-11-10
Thx papatrpt89 ur fix worked perfectly for the miro crash

---

### Post by foxx on 2007-11-14
Thank you for this solution but I think not everyone want's to replace its Java JRE - I think not every application is working with icetea-jre. I switched back to sun's jre with help of "sudo update-alternatives --config java" and miro starts nevertheless. Maybe the Java-Path is saved in the "~/.miro" directory. So if you want to leave another Java JRE as standard simply switch back to it after starting Miro the first time with icedtea ;)

foxx

---

### Post by MozartlovesUbun2 on 2007-11-15
[http://ubuntuforums.org/showthread.php?p=3779090#post3779090](http://ubuntuforums.org/showthread.php?p=3779090#post3779090)


ok I closed Firefox which had google mail chat open and after that now MORO opens normally!

so does google chat use java, theres a conflict there with miro or something?

---

### Post by david.rahrer on 2007-11-15
I received an update for Miro through the Ubuntu update system last night.  I wonder if that fixed the problem?  I switched back to Sun Java 6 because the Icetea 7 screwed up the java in my logmein.com account, but Miro still works fine.

---

### Post by richieboy on 2007-11-21
hi.

i followed the instructions in this thread re icedtea java and got miro working.  yay!  but now java won't work in my mozilla based browsers:  ff, swiftweasel, epiphany.  and this is after i switched back to sun's java as the default.  java only works in opera.  does anyone have any ideas?   please help.

thanks,

rich

---

### Post by david.rahrer on 2007-11-21
I don't know if it was just coincidence, but I had to switch back to Sun JRE 6, then remove the IcedTea stuff from synaptic and reboot before I could get my problem app to work again (logmein).  Give it a try.

PS: after doing so, my Miro install stopped working, contrary to what I said a post or so above :(

---

### Post by richieboy on 2007-11-21
i removed icedtea java too and switched back to sun's java as the default.  now some applets work, some don't.  java.com says my installation is ok and plays the dancing duke applet.  please help.  i need to play runescape.

thanks,

rich

---

### Post by talent03 on 2007-11-22
Nevermind, I just reinstalled Ubuntu.
-------------------------------
I have an issue with miro crashing on startup but I don't know if its the same issue. It has been bugging me all day, because I cannot get it to work. I have started firefox from scratch, erased ~/home/whatever/.miro and gconf/miro, reinstalled xine and tried switching it to gstreamer, but after all of that, it still doesn't work. :/

```
jaime@ubuntu:~$ miro
/usr/lib/firefox
INFO     Starting up Miro
INFO     Version:    1.0
INFO     Revision:   unknown
INFO     Builder:    willg@jupiter
INFO     Build Time: 1195054435.77
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/jaime/.miro/sqlitedb
INFO     Spawning global feed dtv:manualFeed
INFO     Spawning global feed dtv:singleFeed
INFO     Spawning global feed dtv:search
INFO     Spawning global feed dtv:searchDownloads
INFO     Creating channel tab order
INFO     Creating playlist tab order
INFO     *** Launching Downloader Daemon ****
INFO     Spawning Miro Guide...
INFO     Adding default feeds
u'http://www.getmiro.com/screencasts/windows/win.feed.rss'
(u'Starter Channels', [u'http://richie-b.blip.tv/posts/?skin=rss', u'http://feeds.pbs.org/pbs/kcet/wiredscience-video', u'http://www.jpl.nasa.gov/multimedia/rss/podfeed-hd.xml', u'http://www.linktv.org/rss/hq/mosaic.xml'])
INFO     Spawning global feed dtv:directoryfeed
INFO     Spawning auto downloader...
INFO     Displaying main frame...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x878d1b4> took too long: 1.270

** (miro.real:6928): WARNING **: Invalid borders specified for theme pixmap:
        /home/jaime/.themes/Mac4Lin_GTK_v0.3/gtk-2.0/Range/null.png,
borders don't fit within the image

** (miro.real:6928): WARNING **: Invalid borders specified for theme pixmap:
        /home/jaime/.themes/Mac4Lin_GTK_v0.3/gtk-2.0/Frame-Gap/frame1.png,
borders don't fit within the image
TIMING   gtkSyncMethod: <function getDisplay at 0x87b44c4> took too long: 1.596
INFO     First URL is https://www.miroguide.com/firsttime
TIMING   Icon clear: 0.002
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (2.273 secs)
INFO     *** Daemon ready ***
Segmentation fault (core dumped)
jaime@ubuntu:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

```
:confused:

---

### Post by divadotrebla on 2007-11-24
Thanks installing that java flavor I got miro working.

---

### Post by akshunj on 2007-12-01
It takes a few seconds to load applets with the iced-tea java plugin, but it seems to work with these demos:

[http://java.sun.com/applets/jdk/1.4/index.html](http://java.sun.com/applets/jdk/1.4/index.html)

I am running with iced-tea for now.  Other than a slow load-time, I don't see any problems...

--Akshun J

---

### Post by david.rahrer on 2007-12-01
I'm confused as to why a project as current and active as Miro hasn't fixed this yet.  Does anyone know the status or just how deep this goes?

---

### Post by zero_koop on 2007-12-02
I'm afraid to switch any Java stuff in case it just causes more problems for me.  I'll probably just wait until Miro releases a fix.  Currently, all I need to do is click off of the Miro Guide before it starts to load, otherwise it will just end the program.  Everything else in Miro works fine.  Then, if I want to add a channel I just browse the Miro Guide through Firefox and download the "subscribe" file and use Miro to open that file.  The channel is then added to my list.

---

### Post by draconid on 2007-12-15
Thanks for the howto.  Fortunately I don't tend to use anything else that uses java (at least not that I'm aware of) so hopefully this fix won't effect anything else.  I had a few problems adding the repository and had to go direct to the apt sources list.  I'm using Linux Mint and the Synaptic version is apparently slightly different.  But editing the list manually worked fine.  Now to go play with Miro!

---

### Post by papatrpt89 on 2007-12-15
Miro does seem to be pretty temperamental  sometimes.  I hope this guide helps most people, it seems to be doing the trick most of the time.

---

### Post by molom on 2007-12-31
> **draconid said:**
> Thanks for the howto.  Fortunately I don't tend to use anything else that uses java (at least not that I'm aware of) so hopefully this fix won't effect anything else.  I had a few problems adding the repository and had to go direct to the apt sources list.  I'm using Linux Mint and the Synaptic version is apparently slightly different.  But editing the list manually worked fine.  Now to go play with Miro!

I am trying to install Miro 1.0 on Linux Mint Daryna. I have tried a .mint file from the software portal and I have tried a .deb from an ftp site, which Miro suggests and they both give that issue, where it unexpectedly quits at startup of the program and it also gives an error message meanwhile. How do you install Miro on Linux Mint?

Cheers,
molom

---

### Post by mocha on 2008-01-06
Hmmm..  I just installed Miro 1.0 on a Fiesty machine today.  The icedtea-java7 is not an option for me.  Whenever I watch a video and then stop playback or click on something else I would get a segmentation fault like this:

```
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]
INFO     got file:///tmp/tmpHn9nUG.html
INFO     got action:playViewNamed?viewName=watchableItems&firstItemId=164
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0x9a598cc>
INFO     got file:///tmp/tmpY0lnYW.html
INFO     got action:handleSelect?area=tablist&viewName=feedTabs&id=728&shiftDown=0&ctrlDown=0
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
/usr/bin/miro: line 3:  7803 Segmentation fault      (core dumped) LD_LIBRARY_PATH=/usr/lib/firefox ADDON_PATH=/tmp/empty miro.real $@
```


Then I discovered that by starting the program like below, I don't get the segfault anymore:

```
miro --xine-driver=opengl
```

Maybe this info will help someone.

---

### Post by shiv_indap on 2008-01-09
miro --xine-driver=opengl

This solved my problem
Thanks

---

### Post by David Valentine on 2008-01-17
> **shiv_indap said:**
> miro --xine-driver=opengl

This solved my problem
ThanksThis worked for me, too, with no need to switch java versions.  Thanks!  :)

Update:  I later found that somehow the symlink /usr/bin/java had been changed to point to the non-installed-therefore-non-existent icedtea java, screwing up my other java applications (does Miro do that during install?).  Once I changed the symlink back to point to my Sun java, miro crashes during startup.  It is really a shame that Miro forces us to choose between java versions (see [bug report]("http://bugzilla.pculture.org/show_bug.cgi?id=9064")), and therefore between applications we wish to run.  The developers seem to be recommending that feisty users (gutsy too?) should use svn.  I don't know if that will help, but see [here]("https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs") for instructions.

---

### Post by zero_koop on 2008-01-21
Just fixed the startup problem myself, but I didn't need to take all of the suggested steps.  In fact, all I did was to install the icedtea-java7-plugin (and its dependencies) using Synaptic Package Manager and it worked right away!  I did run the
```
sudo update-alternatives --config java
```
code before starting Miro but it had already selected the new icedtea java.  So am I now stuck using this type of Java so long as I want to keep Miro working?  Thanks for the help.

---

### Post by james_xxx on 2008-01-22
A new Miro came down the upgrade pipeline for me today, and I was hoping that it would correct the crashing problem, but for me it didn't. Oddly Miro is working fine on my laptop. I have tried switching to Iced-Tea, as well as other suggestions made in this forum, but to no avail.

I also did an apt-get remove miro --purge (miro-data, too), and re-installed, but that made no difference.

Is anyone else experiencing this? Any ideas on a fix?

Thanks!

---

### Post by Hatchet on 2008-01-23
whoops

---

### Post by c1rcu17 on 2008-01-25
still having miro crashing problems. this is the terminal output for Gusty when I start miro.

```
INFO     Starting up Miro
INFO     Version:    1.1.1
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.1/tv/resources - 6063
INFO     Builder:    pbuilder@mercury
INFO     Build Time: 1201146701.85
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/austin/.miro/sqlitedb
TIMING   Database load slow: 0.637
TIMING   idle (Initializing database) too slow (0.869 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
/var/lib/python-support/python2.5/miro/frontend_implementation/MainFrame.py:177: GtkWarning: Theme directory scalable/places/22 of theme black-white_2-Gloss_big has no size field

  self.widgetTree = WidgetTree(resources.path('miro.glade'), 'main-window', 'miro')
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
INFO     loaded renderer 'xinerenderer'
INFO     First URL is https://www.miroguide.com/
INFO     got file:///tmp/tmpUmNnvC.html
TIMING   Icon clear: 0.395
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.395 secs)
INFO     got file:///tmp/tmpeta92M.html
INFO     First URL is https://www.miroguide.com/
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     *** Daemon ready ***
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/
INFO     First URL is https://www.miroguide.com/
INFO     WARNING: error in Feed.update for Feed - Systm -- <class 'httpclient.BadHeaderLine'>: Error: HTTP error -- Bad Header Line: line:  DAV/2 PHP/5.2.4, next line: X-Powered-By: PHP/5.2.4
INFO     WARNING: error in Feed.update for Feed - Diggnation -- <class 'httpclient.BadHeaderLine'>: Error: HTTP error -- Bad Header Line: line:  DAV/2 PHP/5.2.4, next line: X-Powered-By: PHP/5.2.4
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     WARNING: error in Feed.update for Feed - Tekzilla -- <class 'httpclient.BadHeaderLine'>: Error: HTTP error -- Bad Header Line: line:  DAV/2 PHP/5.2.4, next line: X-Powered-By: PHP/5.2.4
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
austin@Sager-NP2090:~$ TIMING   WARNING: Calling <bound method DownloaderDaemon.closeCallback of <dl_daemon.daemon.DownloaderDaemon object at 0x839bfcc>> on AsyncSocket: Outgoing 127.0.0.1:43183 too slow (5.103 secs)
```


any ideas?

---

### Post by kdog_1914 on 2008-02-03
> **jay_ramos said:**
> sudo apt-get install icedtea-java7-plugin
sudo update-alternatives --config java  
  *choose the icedtea plugin above*
miro

:guitar:

Perfect!  Thank you

---

### Post by themoebius on 2008-02-09
Hmmm maybe I'm still doing something wrong, but I still get the same error:

```

zac@zac-desktop:~$ miro
/usr/lib/firefox
INFO     Starting up Miro
INFO     Version:    1.1.2
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources - 6194
INFO     Builder:    pbuilder@mercury
INFO     Build Time: 1202440018.67
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/zac/.miro/sqlitedb
TIMING   Database load slow: 0.058
INFO     Spawning global feed dtv:manualFeed
INFO     Spawning global feed dtv:singleFeed
INFO     Spawning global feed dtv:search
INFO     Spawning global feed dtv:searchDownloads
INFO     Creating channel tab order
INFO     Creating playlist tab order
INFO     Spawning Miro Guide...
INFO     Spawning global feed dtv:directoryfeed
INFO     Spawning auto downloader...
INFO     Displaying main frame...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
INFO     *** Launching Downloader Daemon ****
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a55e64> took too long: 3.469
INFO     First URL is https://www.miroguide.com/firsttime
TIMING   Icon clear: 0.002
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (4.181 secs)
INFO     Adding default feeds
u'http://www.getmiro.com/screencasts/windows/win.feed.rss'
(u'Starter Channels', [u'http://richie-b.blip.tv/posts/?skin=rss', u'http://feeds.pbs.org/pbs/kcet/wiredscience-video', u'http://www.jpl.nasa.gov/multimedia/rss/podfeed-hd.xml', u'http://www.linktv.org/rss/hq/mosaic.xml'])
TIMING   idle (_installDefaultFeeds() (using asUrgent)) too slow (0.621 secs)
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmpawH8iE.html
INFO     First URL is https://www.miroguide.com/
INFO     got file:///tmp/tmpLMAxw9.html
INFO     First URL is https://www.miroguide.com/
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     bad HTML in description for http://richie-b.blip.tv/posts/?skin=rss
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/firsttime
INFO     First URL is https://www.miroguide.com/
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING  eventloop: Interrupted system call
WARNING  eventloop: Interrupted system call
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

```

---

### Post by jorwex on 2008-02-19
I wouldn't say this is solved personally.

---

### Post by bigbooger on 2008-02-28
[http://www.getmiro.com/documentation/index.php/Change_Video_Playback_from_xine_to_gstreamer](http://www.getmiro.com/documentation/index.php/Change_Video_Playback_from_xine_to_gstreamer)

This seemed to help my issues with Miro.. especially if you find Miro crashes after playing a video and then switching to a new channel, video, or folder.:guitar:

With this fix I had no need to change java at all... *I had tried changing Java to the iced tea but it screws with other software installed that uses java... now everything seems to be fine so far.

---

### Post by digby280 on 2008-03-08
I had this problem and I found out it was caused by the Medibuntu packages (although I'm not sure which one).  If you are using Medibuntu it would be worth trying reverting to the Gusty packages.  It looks to me from the version numbers that these are in fact the same versions.  However, apt-get seems to favour the Medibuntu package.  I'd guess because the version number is longer.

---

### Post by SFN on 2008-03-16
> **bigbooger said:**
> [http://www.getmiro.com/documentation/index.php/Change_Video_Playback_from_xine_to_gstreamer](http://www.getmiro.com/documentation/index.php/Change_Video_Playback_from_xine_to_gstreamer)

This seemed to help my issues with Miro.. especially if you find Miro crashes after playing a video and then switching to a new channel, video, or folder.:guitar:

With this fix I had no need to change java at all... *I had tried changing Java to the iced tea but it screws with other software installed that uses java... now everything seems to be fine so far.

I can confirm that this worked for me too.

Thanks!


EDIT:

Oops. I forgot that I also had to dump .miro/ before it worked.

---

### Post by MadMac on 2008-03-19
Worked great for me, as well!    =D>

Thanks!


> **jay_ramos said:**
> sudo apt-get install icedtea-java7-plugin
sudo update-alternatives --config java  
  *choose the icedtea plugin above*
miro


---

### Post by geoken on 2008-03-21
I hope miro sorts this out as switching to a different java runtime isn't an option for some people (ie. Eclipse users).

---

### Post by SFN on 2008-03-24
OK, this is lame but at least it's fixable.

There was an update to miro today. After accepting the update, this problem returned. I went to edit 
```
/usr/share/python-support/miro/miro/frontend_implementation/VideoDisplay.py 
```
to reflect gstreamer again and guess what? VideoDisplay.py is gone. That's because it's now located at ```
/usr/share/python-support/miro/miro/platform/frontends/html/VideoDisplay.py.
```

Seriously, was that necessary?

Also, once you get there, these two lines
```

self.add_renderer("xinerenderer")
#self.add_renderer("gstrenderer")

```
are different. The lines you need to look for are now
```

 try:
            self.add_renderer(r + "renderer")
        except:
            try:
                logging.error ("initRenderers: error detected...  trying to add$
                # try to add the xine renderer if the preferences aren't right
                self.add_renderer("xinerenderer")

```
and they should be changed to read
```

 try:
            #self.add_renderer(r + "renderer")
            self.add_renderer("gstrenderer")
        except:
            try:
                logging.error ("initRenderers: error detected...  trying to add$
                # try to add the xine renderer if the preferences aren't right
                #self.add_renderer("xinerenderer")
                self.add_renderer("gstrenderer")

```
After that's done, the fix is in place again and miro runs fine.

Yeesh.

---

### Post by techmin on 2008-04-08
If you like it is possible to use sun-java6-plugin for firefox and icedtea plugin for miro:

If you have installed sun-java-plugin miro and icedtea
yuo have

firefox java plugin point to:
/etc/alternatives/firefox-javaplugin.so
firefox-javaplugin.so point to
/usr/lib/jvm/java-7-icedtea/jre/lib/i386/gcjwebplugin.so
miro use mozilla-javaplugin.so
this point to:
/usr/lib/jvm/java-7-icedtea/jre/lib/i386/gcjwebplugin.so

a this point
sudo update-alternatives –config java
and select sun java.

after:
cd /etc/alternatives
after:
sudo ln -sf /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so firefox-javaplugin.so

duplicate firefox:
sudo cp -r /usr/lib/firefox /usr/lib/miro
after:
cd /usr/lib/miro/plugins
after
sudo ln -sf /etc/alternatives/mozilla-javaplugin.so libjavaplugin.so

and adjust mozillalibpath:
sudo gedit /usr/share/miro/resources/app.config
mozillaLibPath=/usr/lib/miro

A this point you use sun plugin for firefox and icedtea for miro.
This is only a tip

---

### Post by duo001 on 2008-04-08
My issue is a bit different. Whenever I try to play certain HD content all I see is a blue screen where the video should be, but I hear the audio. 
Geekbrief TV in HD works fine, while any of the revision 3 videos in HD do not...


I don't think that it is revision 3's videos, they would have had a lot of complaints before now.
Any help would be awesome.

---

### Post by thanhluan001 on 2008-05-13
For someone who still wants to change JRE, the IcedTea package has change to openjdk-6 in Hardy

Icedtea-java7-bin --> openjdk-6-bin
icedtea-java7-jre --> openjdk-6-jre
icedtea-java7-plugin --> icedtea-gcjwebplugin

So when you do:

sudo update-alternatives --config java 

You should be looking at:  /usr/lib/jvm/java-6-openjdk/jre/bin/java

Source: [http://ubuntuforums.org/showthread.php?t=737308](http://ubuntuforums.org/showthread.php?t=737308)

---

### Post by Morimando on 2008-05-28
Just to get this straight... the issue is with the JRE, version 1.6 of Java, right? Because i am somehow not able to figure that out at the moment, and unfortunately xulrunner, java and mozilla-firefox have been upgraded since i last saw a working miro, which makes things  alittle difficult for me. I need to add, that on this machine I am using Gentoo, but i figure the problem won't be different.What I noticed is that Miro 1.2.3 doesn't work at all, apparently because it dislikes xulrunner (new version?)
My versions installed are:
```
[ebuild   R   ] net-libs/xulrunner-1.9_rc1  
[ebuild   R   ] media-tv/miro-1.2.1  
[ebuild   R   ] dev-java/sun-jre-bin-1.6.0.06  
[ebuild   R   ] www-client/mozilla-firefox-3.0_rc1-r1  
*)	Sun JRE 1.6.0.06 [sun-jre-bin-1.6]
```
After reading this thread, i got the impression that it all has to do with the SUN Java, but then again Miro was working absolutely fine with Sun's Java before i updated my system, so i do not see a general problem with Miro and Sun's Java. I would suspect that - as i have the xulrunner 1.9 RELEASE CANDIDATE installed, it is more likely that the issue has to do with xulrunner, but i don't necessarily want to plunge into version-selection-and-endless-compiling-hell before i am somewhat more sure.. 
(i use the development version of xulrunner because i had to unmask it for Firefox 3 - at least i think that was why i unmasked it back in the days before i learnt about selective unmasking of a single version instead of the whole development line of a packet). Now if you say that it is more likely, that xulrunner is the culprit, i will experiment with that and let you know if there's a version that 'just works'. 
OTOH the likelyhood of Java being the culprit is increased IMHO by the fact that it crashes upon navigating to the miroguide, which - i suspect - might use Java... 
As i don't like to switch my Java VM, i would very much prefer finding a different solution. (Bad experiences with Blackdown et al, Sun's VM just works best, even if they didn't manage a decent 64bit plugin for Firefox yet..my bets are that they will make it long before a 64bit Adobe Flash sees the light of day :lolflag: )
So well, long story short, let me know whether it's really the Java VM that broke things or if xulrunner is more likely to be the bad guy.
Regards :)

---

### Post by Morimando on 2008-05-30
Miro is working again for me, not by changing xulrunner or Java, but simply by unmerging firefox 3 and remerging firefox 2 (both 64bit versions). As in Ubuntu 8.04 Firefox 3 ist the standard browser, this might be your solution as well.
I guess this will be fixed - if Firefox 3 is the problem - within the next releases of Miro. I don't know much about Iced Tea Java, but I can imagine that it does bypass something that SUN Java doesn't while invoking Firefox (or just the Gecko engine) to display the miroguide (from which the unexpected crash seems to stem). The "argument from firefox-integration" so to say seems compelling - at least to me, but then again, i am no specialist when it comes to programming and such (I major in languages). Let me know whether downgrading firefox is a viable solution (if you test it), just for my information. Also, if it is, we probably should create a new bug report for the Miro developers or something along those lines.
Wish you a nice weekend (and please let me also know, if my assumption is totally incorrect and firefox isn't involved at all ;) )
Martin

---

### Post by Sn3ipen on 2008-06-01
Miro wont work after upgrading to hardy for me. It works fine untill i try to play a movie, then it crashes:/

---

