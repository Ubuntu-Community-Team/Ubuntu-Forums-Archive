---
title: "mpd as mpd user pulseaudio and dbus problem"
date: 2011-11-10
forum: Multimedia Software
---

### Post by derEremit on 2011-11-10
Ok, first what was my goal:
I got a really low power atom pc which mainly acts as mpd server, but sometimes as a presentation tool connected to a tv.
I'm running oneiric.

for this i need mpd running and playing sound through pulseaudio.

I resarched quite a bit and now i'm stuck.
what i found out.

You should not run pulseaudio as a system daemon.
so i tried to run mpd with pulseaudio under the mpd user.

when i start mpd it claims it can't connect to pulseaudio.
when i run ```
pulseaudio -D
``` it says it can't connect to DBus.
I found out that pulseaudio since a few versions requires a dbus connection.
when i run ```
pulseaudio -D
``` as a normal desktop user pulseaudio can connect to dbus.

But i don't know where i can give the mpd user permissions to connect (or start) a dbus daemon...

that's where i'm stuck.

switching mpd to using alsa doesn't work either as lightdm starts pulseaudio so alsa says that the resource is already busy.

---

### Post by maystar_1 on 2011-12-03
Hey,

I recognized this behavior on my ubuntu machines, too.  I use my desktop user as mpd user, because this was a solution for other problems in older ubuntu versions. So the user should be able to start dbus, since dbus is running after login to X11. But since I've updated my systems to 11.10 oneiric (one of them has a fresh installation) I can't use mpd anymore before I login to X11. MPD log tells me 
```
Failed to enable "Pulse Output" [pulse]: pa_context_connect() has failed: Connection refused
```
and in the syslog I found
```
Dec  3 16:38:45 Henry pulseaudio[1194]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
Dec  3 16:38:45 Henry pulseaudio[1194]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Dec  3 16:38:45 Henry pulseaudio[1191]: [pulseaudio] main.c: Daemon startup failed.
Dec  3 16:38:46 Henry pulseaudio[1576]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
Dec  3 16:38:46 Henry pulseaudio[1576]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Dec  3 16:38:46 Henry pulseaudio[1573]: [pulseaudio] main.c: Daemon startup failed.
Dec  3 16:38:46 Henry pulseaudio[1622]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
Dec  3 16:38:46 Henry pulseaudio[1622]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Dec  3 16:38:47 Henry pulseaudio[1619]: [pulseaudio] main.c: Daemon startup failed.
Dec  3 16:38:47 Henry pulseaudio[1629]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
Dec  3 16:38:47 Henry pulseaudio[1629]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Dec  3 16:38:47 Henry pulseaudio[1626]: [pulseaudio] main.c: Daemon startup failed.

```

I found this problem all around the net, but no solution. It seems to be independent of the distribution.
[https://bbs.archlinux.org/viewtopic.php?id=114975]("https://bbs.archlinux.org/viewtopic.php?id=114975") 
[https://bugzilla.redhat.com/show_bug.cgi?id=747963]("https://bugzilla.redhat.com/show_bug.cgi?id=747963")
[http://lists.debian.org/debian-user/2011/11/msg01281.html]("http://lists.debian.org/debian-user/2011/11/msg01281.html")

I also recognize, that if I login immediately KDE startup hangs for some time and then a popup tells me, that consolekit can't connect to dbus. Then in KDE several things like the networkmanager widget or the usb drive mount function do not work till next login. If I wait with login about half a minute, this will not happen. Although I 've recognized this behavior in older ubuntu versions, too, I suspect it to be caused by a race condition of mpd/pulseaudio and dbus. Someone else also recognized a slower boot up:
[http://www.serkey.com/xubuntu-and-consolekit-timeout-at-startup-bftcdp.html]("http://www.serkey.com/xubuntu-and-consolekit-timeout-at-startup-bftcdp.html") 

If I login per terminal/ssh, I can successfully start pulseaudio with "pulseaudio --start".
I'm not familiar with dbus at all, so I can't give any further information now. Perhaps someone can give me a hint. And perhaps someone has an idea where to file this bug, mpd, dbus, ubuntu, pulseaudio?

---

### Post by maystar_1 on 2011-12-03
I must correct myself:

If I start pulseaudio before I login to X with pulseaudio --start, mpd works but pulseaudio can just output sound through network or dummy devices. In syslog there are theses messages in this case:
```
Dec  3 17:26:48 panda-board pulseaudio[4896]: [pulseaudio] pid.c: Stale PID file, overwriting.
Dec  3 17:26:48 panda-board pulseaudio[4896]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
Dec  3 17:26:49 panda-board pulseaudio[4896]: [pulseaudio] module.c: Module "module-zeroconf-discover" should be loaded once at most. Refusing to load.
Dec  3 17:26:49 panda-board pulseaudio[4896]: [pulseaudio] module-gconf.c: pa_module_load() failed
Dec  3 17:30:19 panda-board pulseaudio[4896]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Dec  3 17:30:19 panda-board pulseaudio[4896]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="platform-soc-audio.1" card_name="alsa_card.platform-soc-audio.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.

```

---

### Post by marsbard on 2011-12-12
I have the same problem, after having read your post I think it may be related to setting up a headless MPD server box: [http://mpd.wikia.com/wiki/PulseAudio](http://mpd.wikia.com/wiki/PulseAudio)

---

### Post by marsbard on 2011-12-12
Actually I don't think that's right; I think your use case is the same as mine, sometimes I want the audio from the X environment too, for example watching a movie.

I think that disabling mpd as a daemon and running it from inside the startup of Gnome (in my case) might be the way to go

---

### Post by maystar_1 on 2011-12-13
Run mpd from X as user and not as service is no option for me, because on 2 of my 3 machines the normal use case is to listen to music without a X login.

Since this was possible in older ubuntu versions, I guess the problem is not solvable. I'm surprised that there are so less discussion about this. Are so less people use mpd in Ubuntu? Or have I misconfigured something basically?

---

### Post by joris1977 on 2012-01-16
I had sort of the same problem after upgrading to 11.10 on my headless ubuntu "server" (just old dual celeron computer) .

Same error in the log:
```
Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
```

After upgrading I couldn't play any audio from my ssh user.

In the end I was able to work around this, because this computer also acts as an xbmc server to the television and audio still worked on the xbmc user. So now all my audio (MPD/subsonic) goes over the xbmc user.

But I would be interested in howto really fixing this, because it would be a bit stupid that you cannot run pulseaudio on a headless box...

---

### Post by maystar_1 on 2012-01-17
I've got it by resetting the configuration of mpd and pulsaudio. I've used this script here 
[http://lkubuntu.wordpress.com/2011/10/27/purgeconfig-a-safer-way-to-reset-configuration-files/](http://lkubuntu.wordpress.com/2011/10/27/purgeconfig-a-safer-way-to-reset-configuration-files/)
with "pulsaudio mpd" as parameter and just modified the pathes in the mpd.conf. I left the user settings untouched. After this everything seems to work. I guess this is som kind of update problem.

---

### Post by duplico on 2012-01-19
> **maystar_1 said:**
> I've got it by resetting the configuration of mpd and pulsaudio. I've used this script here 
[http://lkubuntu.wordpress.com/2011/10/27/purgeconfig-a-safer-way-to-reset-configuration-files/](http://lkubuntu.wordpress.com/2011/10/27/purgeconfig-a-safer-way-to-reset-configuration-files/)
with "pulsaudio mpd" as parameter and just modified the pathes in the mpd.conf. I left the user settings untouched. After this everything seems to work. I guess this is som kind of update problem.

So you fixed it by resetting the configs for mpd and pulseaudio? Is this still without any X session? In my own battle with this issue, I'm continuing to have the same D-Bus errors as before, even when I think I've told pulse not to load any of the D-Bus modules.

---

### Post by maystar_1 on 2012-01-22
> **duplico said:**
> So you fixed it by resetting the configs for mpd and pulseaudio? Is this still without any X session? In my own battle with this issue, I'm continuing to have the same D-Bus errors as before, even when I think I've told pulse not to load any of the D-Bus modules.

The sound works fine, if I am at the login screen of lightdm. I think there were still problems with kdm, but I can't really remember. I haven't modified any settings of pulseaudio, so there are the default modules in my configuration.

---

### Post by limaxray on 2012-02-23
I was having the same problem after upgrading from Debian Squeeze to Wheezy on a headless armel SBC that I've been using as a sound server.  Purging the configs doesn't do anything.

It seems a per-session D-Bus daemon must be running for the user trying to start pulseaudio.  This is normally started automatically when you start X, but that doesn't happen if you're going headless.

Here's the answer:
[http://ubuntuforums.org/showthread.php?t=1743072](http://ubuntuforums.org/showthread.php?t=1743072)

I had to install the dbus-x11 package, but I'd imagine you'd already have that if you have a headful setup.

I wrote a quick script to handle starting a D-Bus daemon and exporting the required variables, and call it to start a pulseaudio daemon.  It could probably use some better fault handling and clean up, but it works fine for my use case.  You will need to manually cleanup though, otherwise you'll have a new D-Bus daemon started every time you run this script.

```

#!/bin/bash

dbusinfo=( $(dbus-launch) )
DBUS_SESSION_BUS_ADDRESS=${dbusinfo[0]#DBUS_SESSION_BUS_ADDRESS=}
DBUS_SESSION_BUS_PID=${dbusinfo[1]#DBUS_SESSION_BUS_PID=}

export DBUS_SESSION_BUS_ADDRESS
export DBUS_SESSION_BUS_PID

pulseaudio --start

```

---

### Post by joris1977 on 2012-02-23
Wow thanks limaxray, this seems to work. At least pulse audio is running now. Strange thing is that there still is no sound. I have already checked if the sink was not muted or that alsamixer was muted... Well at least one step further. 

For some reason I didn't have dbus-x11 package installed. That is weird because xbmc is working with pulse audio and has x installed.

---

### Post by limaxray on 2012-02-24
No problem.  I only use pulseaudio as a sound server sink and can confirm this works fine playing networked audio.

Now if you're trying to play audio from local sources from different users, you're going to have some problems.  You will need to start pulseaudio from the user you intend to use it with.  So, if your running mpd system wide, you need to run that script as mpd before starting mpd.  You also need to make sure pulseaudio isn't running for any other users since pulseaudio will hog the audio device. 

See if this works:

```

$ sudo killall pulseaudio
$ sudo -u mpd ./startpulse
$ sudo /etc/init.d/mpd start

```  

Of course this may not be ideal since it only allows you to play audio from one user.  If you need audio from multiple users, you could start pulseaudio in system mode (which would probably be the easiest way to go if you don't mind the security implications) or do **[something like this]("http://fedoraforum.org/forum/showpost.php?p=1493857&postcount=5")**, starting a new dbus and pulseaudio session for each user.

---

