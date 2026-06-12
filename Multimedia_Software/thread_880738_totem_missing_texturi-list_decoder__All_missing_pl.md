---
title: "totem missing text/uri-list decoder / All missing plugins are blacklisted"
date: 2008-08-05
forum: Multimedia Software
---

### Post by rofa on 2008-08-05
I have an annoying problem with Totem on Hardy. It works fine on other machines but not on this one.

When you try to play a playlist you'll get an error message saying:

An error occurred, The playback of this movie requires a text/uri-list decoder plugin which is not installed.

From the console:

[HTML]
rfd@rfdesktop01:~$ totem
** Message: don't know how to handle text/uri-list
** Message: Error: A text/uri-list decoder plugin is required to play this stream, but not installed.
gstdecodebin.c(792): close_pad_link (): /play/decodebin0:
No decoder to handle media type 'text/uri-list'

** Message: Missing plugin: gstreamer|0.10|totem|text/uri-list decoder|decoder-text/uri-list (text/uri-list decoder)
no application found
** Message: No installation candidate for missing plugins found.
** Message: don't know how to handle text/uri-list
** Message: Error: A text/uri-list decoder plugin is required to play this stream, but not installed.
gstdecodebin.c(792): close_pad_link (): /play/decodebin1:
No decoder to handle media type 'text/uri-list'

** Message: Missing plugin: gstreamer|0.10|totem|text/uri-list decoder|decoder-text/uri-list (ignoring)
** Message: All missing plugins are blacklisted, doing nothing
[/HTML]

The gstreamer plugin is installed and I noticed that it worked fine as root. And also if I as root execute totem as user rfd with sudo like this..
[HTML]
root@rfdesktop01:/# sudo -u rfd totem
[/HTML]

I've tried to change the permissions on everything I can find regarding gstreamer and totem. Done a complete remove and reinstalled everything and it doesn't help.

If i remove gstreamer and run totem as root it will ask me to install the missing plugin. But as a user i'll just get the missing plugin message.

'All missing plugins are blacklisted, doing nothing' :/

---

### Post by Python101 on 2008-09-10
```
sudo apt-get install python-gst0.10 python-glade2 libgnomevfs2-extra
```

This worked for me.

---

### Post by kostkon on 2008-09-10
Also check if the [*libtotem-plparser10*]("http://packages.ubuntu.com/hardy/libtotem-plparser10") package is installed. If it is, then try to reinstall it.

---

### Post by skiquel on 2009-05-10
> **kostkon said:**
> Also check if the [*libtotem-plparser10*]("http://packages.ubuntu.com/hardy/libtotem-plparser10") package is installed. If it is, then try to reinstall it.

In 9.04 / jaunty, this error occurs too.

The package to install / dpkg-reconfigure -phigh is 'libtotem-plparser-dev'

(Unsure if it was best to make a new thread or bump this.)

---

### Post by flocki on 2009-08-27
I have the same issue, but installing libtotem-plparser-dev did NOT fix it.

---

### Post by statmech on 2009-09-06
None of the above approaches worked. I had the same error message when trying to play a streaming video using realplay. The best method to fix this problem for me was to follow the instructions in [COLOR="Blue"][Complete Streaming, Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=661833")[/COLOR] [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) (25 Apr 2008) for ubunty 8.04 hardy, or a [COLOR="Blue"][more recent howto]("http://ubuntuforums.org/showthread.php?t=766683")[/COLOR] [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) (26 May 2009) for more recent ubuntu distros.  Actually, I started with the instructions in the new howto until the section that is applicable to ubuntu 8.10 and higher; after that I followed the older howto for ubuntu 8.04.  I installed mplayer as instructed; it worked for streaming videos.  No more error messages.

---

### Post by trusktr on 2010-06-14
I've got the same problem with this error message in Arch Linux. Wondering what to install!

---

### Post by Rolandmaffia on 2011-05-18
I've installed RealPlayer, and opened the RTSP(google it) uri, than it played me.

[ [Download RealPlayer]("http://real.com/linux") | my test stream: [Truman's Radio Report to the American People on the Potsdam Conference - August 9, 1945]("rtsp://qtss.id.ucsb.edu/presidency/12165.mov")]

Otherwise, download the file, open with a text editor. There will the URI(s), and the protocol(s). Try in VNC, QuickTime, RealPlayer, or google for that protocol type. 

The text/uri-list mime is only a list of stream uri(s)...

---

