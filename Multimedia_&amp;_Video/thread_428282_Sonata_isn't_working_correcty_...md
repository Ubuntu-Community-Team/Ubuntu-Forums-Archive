---
title: "Sonata isn't working correcty .."
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by PhockouS on 2007-04-30
Hi . I'm new at this forum , so at start I want to say hello to You all : Hello :-)

Ok , I've got this problem .

I don't know it's fault of sonata or maybe mpd , one I know is : Sonata can't load to the dbus . 

I'm twisted , because all worked correctly to today . Now sonata is broken .

Maybe somebody can help me ? I'm googling all the time , and noone have the same problem ..

Regards



phockous@funKy:~$ sonata
/usr/lib/python2.5/site-packages/sonata.py:57: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon
Taglib and tagpy not found, tag editing support disabled.
/usr/lib/python2.5/site-packages/sonata.py:5406: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  retval = dbus.dbus_bindings.bus_request_name(session_bus.get_connection(), "org.MPD.Sonata", dbus.dbus_bindings.NAME_FLAG_DO_NOT_QUEUE)
/var/lib/python-support/python2.5/dbus/_dbus.py:851: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  import dbus.dbus_bindings as m
Po&#322;&#261;czenie z sesj&#261; D-BUS nieudane: Niemo&#380;liwe okre&#347;lenie adresu magistrali wiadomo&#347;ci (spróbuj uzyska&#263; pomoc "man dbus-launch" i "man dbus-deamon")

---

### Post by kefir on 2007-05-01
Those msgs have nothing to do with sonata not outputting sound. They're just msgs about pygtk and some functions in it that are about to be changed/moved, basically a heads-up to the developers of sonata if i understand it right. (I get the same msgs and my sonata works fine)


I suggest you look for applications hogging your sounddevice as a first step. And also make sure mpd is started :) I've had the excat same "issue" turned out i had some bogus processes that hadn't closed correctly running in the background hogging my sounddevice!

---

### Post by pete on 2007-05-03
PhockouS, the same thing happened to me...  Sonata working fine, and then one day, it starts freezing whenever I start it up with all the same messages you're getting.

As it turns out, the problem started when I set Sonata to update the MPD library on start.  This option is on the "Behavior" tab of the Sonata preferences.  Problem was, I couldn't get back to the Preferences, since Sonata would lock up as soon as it opened.

I was able to fix it by going into ~/.config/sonata/sonatarc in vim and changing line 29 ("update_on_start") from True to False.  After that, it starts up just fine.  Don't know if that's what is causing your problem, but I thought I'd throw it out there just in case.

---

