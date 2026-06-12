---
title: "Amarok - iPod not found"
date: 2008-08-22
forum: Multimedia Software
---

### Post by mouseclone on 2008-08-22
I was looking to a fix to my iPod problem.  I installed the 64bit version of 8.04 a while back and never really hooked up my iPod.  Just have not taken a trip in a while.

So I went searching and found a post that was old and in the archives.  I wasn't happy that the post had never been answered so I'm going to answer it here.

When you try and auto detect your iPod in Amarok you may get the error:

[INDENT]No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.[/INDENT]

So if you get this error and your iPod is not found you will need to do the following.  I did this with Amarok install on the system already.

[INDENT]sudo apt-get build-dep amarok && sudo apt-get remove amarok* && sudo apt-get install amarok*[/INDENT]

This should build and install the dependencies, while removing all of Amarok and reinstalling it.

You should now see the device under Devices.  If you run auto detect you will get the error, but not because you don't have what you need, but because it doesn't see anymore devices on your system.

I hope this helps.

---

