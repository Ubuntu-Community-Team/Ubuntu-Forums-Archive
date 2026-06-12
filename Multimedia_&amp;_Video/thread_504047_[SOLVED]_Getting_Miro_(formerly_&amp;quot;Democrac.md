---
title: "[SOLVED] Getting Miro (formerly &amp;quot;Democracy Player&amp;quot;) to work with Feisty"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by riddell on 2007-07-18
Hi,

I'm trying to get the current version of Miro (formerly Democracy Player) to run. I've downloaded the version via svn and I'm getting a missing python (?) package message:

"Can't find xulrunner-xpcom, mozilla-xpcom or firefox-xpcom"

I've got all the packages installed that the documentation recommends. I even tried installing xulrunner and python-xpcom, but they didn't seem to provide the needed package.

Any suggestions?

Cheers,

Allen

---

### Post by tikal26 on 2007-07-18
Hey Ridell , 

You just need to add their repo on your list, 
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) feisty/
 and install Miro not democracy player (it is a dummy packages) and Miro-data and that is it. I have kubuntu feisty 64 and it works.

---

### Post by bsantos on 2007-07-18
Anyone got it to work with Gutsy?

---

### Post by riddell on 2007-07-18
Actually, I should say that it isn't even working for me. It downloads fine but playback doesn't work -- and I can't immediately identify the problem watching the terminal output...

---

### Post by p_quarles on 2007-07-18
I'm having exactly the same problem. The error output in the terminal indicated that Gecko (the engine in Firefox) received an X Window system error called "Bad Match." 

Miro has a page about problems with the Feisty Fawn package, but I'm getting a 503 error every time I try to click through. In any case, I noticed in their Linux forums that a Red Hat user was having trouble because Miro uses Firefox 2.0.3, whereas Red Hat's current package is 2.0.4. The same is true of Ubuntu. 

I'm guessing that's the problem. Just wish I knew what to do about it.

---

### Post by p_quarles on 2007-07-18
Nope, I was wrong. I did, however, get it to work after installing the right codec: ```
sudo apt-get install libxine-extracodecs
```

Hopefully, this will work for others as well.

---

### Post by stmiller on 2007-07-20
> **riddell said:**
> 
"Can't find xulrunner-xpcom, mozilla-xpcom or firefox-xpcom"



Install the packages required in the line about Feisty here:

[https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs)

---

### Post by jbdev on 2007-07-20
> **p_quarles said:**
> Nope, I was wrong. I did, however, get it to work after installing the right codec: ```
sudo apt-get install libxine-extracodecs
```

Hopefully, this will work for others as well.

Worked for me ... Thanks

---

### Post by Yfrwlf on 2007-07-21
> **p_quarles said:**
> Nope, I was wrong. I did, however, get it to work after installing the right codec: ```
sudo apt-get install libxine-extracodecs
```

Hopefully, this will work for others as well.

Thank you!  I was having the same issue, where it would download fine but would automatically close after trying to open the video.  After trying to open the video files directly using Totem, it asked to download codecs, and I figured that was the problem.  I guess the codecs it uses are different, or there is no centralized codec system, so even though Totem could play them, Miro still would not.  After installing that package though it worked.  I assume it's because Miro uses Xine instead to play them, so it needed Xine-specific codecs.

If I'm right about all that, then I really hope Linux will standardize it's codecs so they can be used by any media player.  Thanks for your help! ^^

Off topic, but I sure wish everyone would convert videos to open codec formats though so that we won't have to use these annoying patent/legal/crap-encumbered codecs.  Open codecs and standards, damn it!  Every time you choose to encode something with a controlled codec, you make that content controlled by stupid laws in the U.S. and other countries. >.<

---

### Post by p_quarles on 2007-07-22
FYI, installing the xine codecs worked for a while, but then Miro started crashing again. I found the answer at Miro's web page (apparently it's very unstable in Debian/Ubuntu) and posted a better solution (at least for me) in this thread:
[http://ubuntuforums.org/showthread.php?t=506600](http://ubuntuforums.org/showthread.php?t=506600)

---

### Post by louiech21 on 2007-07-28
I have Ubuntu Fiesty and I have the software installed for Miro + the repositories, and when I try to open Miro it pauses as if it is loading my podcasts then it completely closes with no explanation.
Any suggestions??? :(

---

### Post by Yfrwlf on 2007-07-28
> **louiech21 said:**
> I have Ubuntu Fiesty and I have the software installed for Miro + the repositories, and when I try to open Miro it pauses as if it is loading my podcasts then it completely closes with no explanation.
Any suggestions??? :(

Well first off, if you want to *possibly* get more information about why something ever crashes, try running the program from the terminal and look at the output.  It'll be neat when a standardized system for outputting errors to X when programs are not being run from a terminal is created.  For now though, that's what you need to do.

I don't know why it's crashing for you though, it works fine on my system under Feisty.  I think all I did was add the repository, isntall the "miro" package which installed several other things, and started it up.  I'd test it on my other machine but it's running Gutsy atm.

Off topic, but it's really pretty, btw, and composite desktop effects enable automatically after installing drivers that support it, or at least when you do it through the restricted hardware driver manager.

---

### Post by tvor on 2007-10-29
I have the same problem, it shut downs in 3 sec. :

:~$ miro
/usr/bin/miro.real:84: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  import dbus_bindings
/var/lib/python-support/python2.5/dbus_bindings.py:5: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
INFO     Starting up Miro
INFO     Version:    0.9.9.1
INFO     Revision:   unknown
INFO     Builder:    ben@pitpat
INFO     Build Time: 1189015412.11
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/pajda/.miro/sqlitedb
TIMING   Database load slow: 0.184
INFO     Spawning auto downloader...
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
alsa
oss
pulseaudio
arts
esd
file
none
INFO     loaded renderer 'xinerenderer'
INFO     got file:///tmp/tmpICejfF.html
TIMING   Icon clear: 0.404
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.622 secs)
INFO     got file:///tmp/tmpIo4on_.html
INFO     got [https://www.miroguide.com/](https://www.miroguide.com/)
TIMING   timeout (Feed update (Feedless Videos)) too slow (1.031 secs)
INFO     *** Daemon ready ***
Segmentation fault (core dumped)
pajda@pajda-laptop:~$ WARNING  downloader: connection closed -- quitting

---

