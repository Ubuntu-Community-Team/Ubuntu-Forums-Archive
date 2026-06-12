---
title: "help installing real player to work in firefox"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by bradford72 on 2007-07-11
Anybody know how to install RealPlayer so that works in Firefox?  I can get it to work using the instructions on the download page, but not from inside firefox.  Specifically, I am wondering which directory to extract the files to, because firefox tells me that "No system path found for nphelix.xpt"  I can run the player just fine from wherever I chose to install it, but I can't figure out where to install it so that firefox can find it.  thanks in advance!

---

### Post by NilsE on 2007-07-11
If you download the RealPlayer .bin file from the link below to your home folder /home/xxxxx   (xxxxx is your login name) or wherever you want

[http://www.real.com/linux](http://www.real.com/linux)

```
Go into synaptic and make sure libstdc++.5 is installed

Then go into a regular terminal (not a root terminal)

cd /home/xxxxx   (xxxxx is your login name) or cd to wherever you downloaded it to.

chmod +x RealPlayer10GOLD.bin

sudo ./RealPlayer10GOLD.bin
```

NOTE: Take all the defaults and positive to anything that asks for a positive response.

---

### Post by sdowney717 on 2007-07-11
I have mplayer handling real player file formats

All I did was install mplayer, mplayer plugin, and the win32 codecs.

If you do this make sure you remove real player plugins and leave mplayer plugins

cbsnews, cbs inner tube are real player format.

---

### Post by southernman on 2007-07-11
I don't use it, but I read that VLC player is the most versatile. I use Mplayer, but haven't tried any RP format's.

---

### Post by sdowney717 on 2007-07-12
If you dont use the win32 codecs, it wont work for real player formats.
 wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)

like this or so

---

### Post by thefirstcalled on 2007-07-13
Thank you so much - I followed your directions, and it works perfectly!  Now I can listen to my favorite streaming inspirational programs!

---

