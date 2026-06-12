---
title: "minidlna vs ushare upnp servers"
date: 2009-11-10
forum: Multimedia Software
---

### Post by sdowney717 on 2009-11-10
[http://minidlna.sourceforge.net/](http://minidlna.sourceforge.net/)
[http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)
This minidlna is better than ushare.
it does automatic folder refreshing without interrupting the upnp serving of currently playing video.

with ushare, placing a file in the shared folder to become visible to the media player, you have to do a reload. then my dsm 320 stops playing the stream and i cant just restart but have to back out of the directory to replay the video.

for minidlna, just extract to a home folder.
adjust the conf file to suite your system
run it like this

Usage:
	./minidlna [-d] [-f config_file]
		[-a listening_ip] [-p port]
		[-s serial] [-m model_number] 
		[-t notify_interval] [-P pid_filename]
		[-w url] [-R] [-V] [-h]

Notes:
	Notify interval is in seconds. Default is 895 seconds.
	Default pid file is /var/run/minidlna.pid.
	With -d minidlna will run in debug mode (not daemonize).
	-w sets the presentation url. Default is http address on port 80
	-h displays this text
	-R forces a full rescan
	-V print the version number

scott@scott-desktop:~/mini/usr/sbin$ ./minidlna -f /home/scott/mini/etc/minidlna.conf
scott@scott-desktop:~/mini/usr/sbin$

---

### Post by Monkey77 on 2009-11-11
Thanks for posting that.  uShare has been broken for me of since just before the release of 9.10

This works and is actually maintained unlike ushare.

---

### Post by sdowney717 on 2009-11-13
I can also play divx files directly on the dsm 320 with minidlna.
ushare can not do this.

---

