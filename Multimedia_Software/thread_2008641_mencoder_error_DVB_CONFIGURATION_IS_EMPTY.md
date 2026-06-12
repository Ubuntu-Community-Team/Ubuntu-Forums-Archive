---
title: "mencoder error DVB CONFIGURATION IS EMPTY"
date: 2012-06-23
forum: Multimedia Software
---

### Post by fixitdude on 2012-06-23
For those that have run into the dreaded "DVB CONFIGURATION IS EMPTY" error..

This can be several things and the error really doesn't explain ANYTHING, bad, bad programming. Plus the real errors are not displayed for some reason just before it prints this.

Here's what it could be:

You need a "channels.conf" file in the ~/.mplayer folder.

I used "w_scan -f a -c US -X" to create mine, you mileage may vary, see google.

Some other file names it may be looking for "channels.conf.ter" "channels.conf.cbl" "channels.conf.sat" "channels.conf.atsc" if you have something special. Most of the time it's just "channels.conf".

Or for some reason it can't access "/dev/dvb/adapter%d/frontend0" , where "%d" is a number from 0 to 4, it tries them all. Yes, the "frontend0" is hard coded so if that needs to be changed then make a symbolic link to the proper device.

You should "ls -al /dev/dvb/" and "ls -al /dev/dvb/adapter0/" and see what GROUP this thing belongs to, like for Ubuntu 12.04 it's "video" and when you are in your GUI like KDE then you are part of that group, but when you log out, guess what? It takes you out!

This makes it hard to run mencoder from a script or cron when KDE isn't running.

You might want to add yourself to the video group:

sudo adduser YOUR_USER_NAME video

You need to log back in before the group change takes effect.

For good measure you could also do this unless it's already that way:
sudo chown -R root.video /dev/dvb/adapter0

(that's recursive and should change everything in that folder)

Hope this helps.


This is just for search keywords so people can find this info:

MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://TV1.
Cannot open file/device.

---

