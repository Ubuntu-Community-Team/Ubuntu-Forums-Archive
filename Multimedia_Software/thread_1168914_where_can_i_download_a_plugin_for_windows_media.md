---
title: "where can i download a plugin for windows media"
date: 2009-05-24
forum: Multimedia Software
---

### Post by devananda on 2009-05-24
i am requested to get a plugin for wma,,,where can i get it

---

### Post by jerrrys on 2009-05-24
what media player and what ubuntu?

i use VLC media player for wma...

[http://www.google.com/search?q=vlc+media+player+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=vlc+media+player+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by devananda on 2009-05-24
> **jerrrys said:**
> what media player and what ubuntu?

i use VLC media player for wma...

[http://www.google.com/search?q=vlc+media+player+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=vlc+media+player+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)



sorry ,,i need the plugin  windows media audio  decoder  for ubuntu 9.04.  t
o be used with the movie player
thanks for your help
should i download vls player??

---

### Post by cwsnyder on 2009-05-24
As far as I am aware at this point, the Jaunty movie player application does not include the decoder for Windows WMA or WMV files.

The VLC player does include the Windows Media decoders.

---

### Post by logos34 on 2009-05-24
yeah, get vlc 

but if you would rather use the default (Totem?), I think this might help:

sudo apt-get install w32codecs

---

### Post by miegiel on 2009-05-24
> **logos34 said:**
> sudo apt-get install w32codecs

Adding the [_Medibuntu Repository_]("https://help.ubuntu.com/community/Medibuntu") and installing the [_Restricted Formats_]("https://help.ubuntu.com/community/RestrictedFormats/") should help alot too.

---

### Post by manolomanolo on 2009-09-11
Manual install
[http://packages.medibuntu.org/jaunty/w32codecs.html](http://packages.medibuntu.org/jaunty/w32codecs.html)

Or install fro repositories:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

then

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

then

```
sudo apt-get install w32codecs
```

Both methods install the same packages and didn't work in my cas, anyway.
So, I'm still unable to play WMA files created through QBASE for MS Windows.

---

### Post by ahbart on 2009-09-11
I always use mplayer and the mozilla-mplayer plugin. Beware you should remove the other mozilla media pugins from synaptic. So choose between: mozilla-plugin-vlc, totem-mozilla and mozilla-mplayer.
It's all about choice and taste isn't it ;-)

---

