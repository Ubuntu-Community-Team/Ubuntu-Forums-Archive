---
title: "EvilChili videos wont play"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by wearekosh on 2007-03-24
Hi

I miss my [www.evilchili.com](www.evilchili.com) videos since shifting to Ubuntu :( 

Can some one help me to get the videos at evilchili to work 
I have MPlayer and plugin's  for mozilla installed also  Gstreamer 
I don't know if it is a problem but when i look in Synaptic Package Manager I seem to have both the gstreamer "bad" set and "ugly" set of plugin's installed? is this a problem? :confused: 

thanks

---

### Post by Toadmund on 2007-03-24
Works for me, are you 64 or 32 bit?
I am 64 bit.

---

### Post by wearekosh on 2007-03-24
I got it working when i found this here

[http://www.ubuntuforums.org/showthread.php?t=337825](http://www.ubuntuforums.org/showthread.php?t=337825)

So change some things for Firefox. First close Firefox. I went to /usr/lib/firefox/plugins and moved all the libtotem files out of the plugins folder. Like so:
$ sudo mkdir /usr/lib/firefox/totem_plugins
$ sudo mv /usr/lib/firefox/plugins/libtot*.* /usr/lib/firefox/totem_plugins
Firefox only refreshes its plugin list (cached) when a new plugin arrives so give it a new time-stamp to see, specifically the mplayer one.
$ sudo touch /usr/lib/firefox/plugins/mplayerplug-in.so
Now start Firefox and you'll have the *.asf location open with mplayer. (imho you're better off without THAT radio station though) Check the url about:plugins again and you'll see Totem is gone :) and that asf is now enabled for mplayer.

seem ok for me now

---

