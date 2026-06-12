---
title: "Play .wax files"
date: 2010-10-18
forum: Multimedia Software
---

### Post by jeffrey2009 on 2010-10-18
Anyone know how I can play a .wax radio station on ubuntu.  The link I have is:

[http://82.135.234.195/pukas2.wax](http://82.135.234.195/pukas2.wax)

I don't think this is possible based on some research but find it hard to believe and do not understand why.

Regards,

Jeffrey

---

### Post by Chronon on 2010-10-19
Hi.

See if this procedure works for you:
[http://ubuntugenius.wordpress.com/2010/06/27/how-to-setup-internet-online-web-radio-stations-in-ubuntus-rhythmbox-media-player/](http://ubuntugenius.wordpress.com/2010/06/27/how-to-setup-internet-online-web-radio-stations-in-ubuntus-rhythmbox-media-player/)

---

### Post by cchhrriiss121212 on 2010-10-19
I can open the stream with xine and mplayer.

---

### Post by jeffrey2009 on 2010-10-19
Tried Gnome mplayer on ubuntu 10.10 but it did not seem to work.  Do I need any kind of plugins.  I will try xine now.

---

### Post by qamelian on 2010-10-19
Files with the .wax extension are just text files containing metadata about the actual stream. If you open the file in gedit, you should be able to locate the actual URL of the audio stream. This extension is just a Windows Audio redirector.

---

### Post by mc4man on 2010-10-19
The problem with some players (totem, ect.), is that the first address in the .wax doesn't work, other players (vlc, ect. will move on to the next one))

> <asx version = "3.0">

  <entry>
     <ref href = "mms://82.135.234.19[COLOR="Red"]5[/COLOR]/Pukas2"/>

    <ref href = "http://82.135.234.199/Pukas2"/>

  <Title>Pukas 2</Title>
...............

either just use the http or edit the mms to 
<ref href = "mms://82.135.234.199/Pukas2"/>

Or forget using the .wax - use the http directly or make yourself a .m3u

Ex. - pukas2.m3u

```
#EXTM3U
#EXTINF:0,Pukas 2
mms://82.135.234.199/Pukas2?MSWMExt=.asf
mms://82.135.234.199:80/Pukas2?MSWMExt=.asf

```

Edit:
note that is a wmap stream which by default should be supported in most players **in maverick**. In lucid only xine based,  mplayer or  vlc will playback - wmap support in gstreamer can be added by updating the lucid gstreamer plugins from ppa in my sig.

---

