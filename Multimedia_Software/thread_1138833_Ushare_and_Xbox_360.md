---
title: "Ushare and Xbox 360"
date: 2009-04-26
forum: Multimedia Software
---

### Post by mr_x408 on 2009-04-26
i recently discovered that it was possible to stream media to my xbox 360 from my ubuntu pc wirelessly much like a windows pc can, using a program called Ushare. i have installed and attempted to configure Ushare but when i try to connect my xbox to it it cant find my computer, can anyone tell me what i am doing wrong with configureing it

heres my config file:

# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49153

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/mike/music/LimeWire/Saved

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
ENABLE_DLNA=




i have used these tutorials with no luck so far: 
[http://www.youtube.com/watch?v=o-OB3PDYqAI](http://www.youtube.com/watch?v=o-OB3PDYqAI)
[http://blog.beplacid.net/2008/11/24/xbox-360-debianubuntu-linux-media-video-music-streaming/](http://blog.beplacid.net/2008/11/24/xbox-360-debianubuntu-linux-media-video-music-streaming/)

---

### Post by quattroman on 2010-07-21
not sure if you still need this, or have resolved it.

I would try leaving the port blank. 

I will install lucid lynx tonight at a real computer. I am trying this now on VM.

---

### Post by Sir Rodness on 2010-08-27
You may have figured it out, however this is my configuration that works with my xbox.

In my terminal I type "sudo gedit /etc/ushare.conf" then enter the following configuration. 

USHARE_NAME=uShare
USHARE_IFACE=eth0 ##note your network interface may be different
USHARE_PORT=49200
USHARE_TELNET_PORT=1337
USHARE_DIR=<path to the root folder you want your xbox to see>
USHARE_OVERRIDE_ICONV_ERR=
USHARE_ENABLE_WEB=no
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no

Also, most sites claim that ushare will run automatically on boot. Sure doesn't appear to be the case for me. So I have to type the following in my terminal to get ushare started manually each time I restart my computer, "sudo /etc/init.d/ushare start". Replace "start" with "stop" if you want to turn ushare off. Also I noticed that I have to stop and restart uShare anytime I update my root media folder with new content.

Hope this helps.

Cheers.

---

### Post by quirkification on 2010-09-06
I was under the impression that uShare was no longer available and that it didn't work. I will have to give this a try next weekend when I have more time to fiddle around with it, as college eats up 85% of the weekdays minus Friday for me. BAH, back to the books.

**Does uShare work for all formats?** (photos, movies, music) because I was thinking about getting a 1 TB external HDD for my windows 7 I keep on my laptop because with the upgrade I do not have a disk to reinstall in the future, so I can never reformat, LAME!

Regardless of using linux or 7 with the external HDD, which I would rather be on Linux; however, I may just use windows as my media share OS. Although, the reboot is annoying it WILL work with no prevail.

---

### Post by cj.surrusco on 2010-09-06
I would set 'Enable Telnet' to no, and 'Enable DLNA' to no. And yes, Ushare works with Xbox, I use it. It's a little bit flukey though. Sometimes I have to restart the service, and my mp3's won't play for some reason. Photos and .avi videos work well enough, though.

---

### Post by quirkification on 2010-09-06
sweet deal, I will have to spend some more time getting them to play well together. I for one cannot wait to get Kinect for use the the media center, that will be tight.

::hand swipe:: ::hand swipe:: ::"play video":: ::video plays::

I hope it all goes well setting this up tomorrow.

Are you able to play your media music while playing your games too?

---

### Post by cj.surrusco on 2010-09-06
> **quirkification said:**
> sweet deal, I will have to spend some more time getting them to play well together. I for one cannot wait to get Kinect for use the the media center, that will be tight.

::hand swipe:: ::hand swipe:: ::"play video":: ::video plays::

I hope it all goes well setting this up tomorrow.

Are you able to play your media music while playing your games too?

Well no, not really. You are supposed to be able to, but for some reason I haven't been able to get the music to work. The xbox sees the files, but won't play them. I've only gotten .avi movies and pictures to work.

---

### Post by quirkification on 2010-09-11
[PHP]sudo gedit /usr/share/mime/packages/freedesktop.org.xml
[/PHP]
did you change x-msvideo to x-ms-wmv
you have to do that to play videos.

I am still having no luck getting my xbox to even see my laptop. This sucks, 3 months ago I was running windows, all all those losers have to do is share the folder. DARN YOU MICROSOFT!!! ::SHAKES FIST::

---

