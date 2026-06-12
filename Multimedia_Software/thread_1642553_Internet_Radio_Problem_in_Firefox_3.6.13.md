---
title: "Internet Radio Problem in Firefox 3.6.13"
date: 2010-12-10
forum: Multimedia Software
---

### Post by Rick B. on 2010-12-10
The Iceberg Radio live stream (On top of the page here: [http://www.classicalwebcast.com/usa.htm](http://www.classicalwebcast.com/usa.htm)) 
plays OK in Seamonkey 2.0.10 but not in Firefox 3.6.13 which I just installed in Ubuntu 9.10 today. Is anyone else having Internet Radio problems with the latest release of Firefox? Thanks.

---

### Post by ajgreeny on 2010-12-10
Works fine here in UK.

What plugins do you have in your FF?   Flash is needed for some steams and an mp3 stream player for others.  I use **adobe-flash** from the ubuntu partner repos and **gecko-mediaplayer** for the mp3s, as I prefer it to **totem-mozilla**

---

### Post by Rick B. on 2010-12-12
Here are the Firefox 3.6.13 installed multimedia plugins:

Shockwave Flash 9.0 r999
Shockwave Flash 10.1 r999. Gnash 0.8.6, the GNU SWF Player
Shockwave Flash 10.1 r102
All VLC Multimedia & Windows Media Player Compatible Plugins for Totem 2.28.2
DivX Web Player version 1.4.0.233
QuickTime Plug-in 7.2.0

---

### Post by ron999 on 2010-12-12
Hi
The Iceberg stations play using Flash.

You only need 1 flashplayer installed.

This is the one that I use:-
Shockwave Flash 10.1 r102

I suggest you get rid of these:-
Shockwave Flash 9.0 r999
Shockwave Flash 10.1 r999. Gnash 0.8.6, the GNU SWF Player

---

### Post by Rick B. on 2010-12-13
I disabled the other two Flash versions and nothing has changed. Still no music on Iceberg Radio using Firefox 3.6.13 and Karmic 9.10. There must be some other issue involved here as I was able to listen to the music with 3.6.12 previously on my laptop and presently with 3.6.12 on my Dell desktop running Lucid 10.04. The plugin updater shows that Flash 10.1 r102 is out of date and should be updated to 10.2 r102.65. I don't know if this will make any difference. More feedback from the forum is needed from anyone who has this same problem after updating Firefox to 3.6.13. Thanks.

---

### Post by ron999 on 2010-12-13
There's a Firefox optimization thread.
Lots of information there and lovinglinux might help you.
Here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1193567]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Rick B. on 2010-12-15
I've been fooling with this problem now for several days. Out of curiosity I went into Tools > Add-ons and Disabled "Ubuntu Firefox Modifications 0.9rc2". Went back to Iceberg Radio and the problem is now solved! There is obviously a problem with these Ubuntu modifications that affect certain things in FF 3.6.13. It is enabled on my Dell desktop in FF 3.6.12 and Iceberg Radio does work with that configuration. I have found on the Ubuntu forums that I'm not the only one having problems with these Ubuntu FF add-on mods :

[http://ubuntuforums.org/showthread.php?t=1589714&highlight=Ubuntu+Firefox+Modifications+0.9rc2](http://ubuntuforums.org/showthread.php?t=1589714&highlight=Ubuntu+Firefox+Modifications+0.9rc2)

Also put the above add-on description in a search engine and it will return quite a few hits.

---

