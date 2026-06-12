---
title: "Music players can't find my codecs..."
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by paperBag on 2007-08-07
Not one, and I've tried them all. Xmms, Rhythmbox, Banshee, etc. I have almost every codec I could find, but the players just can't seem to find them for some reason.

```
dpkg -l | grep mp4
ii  faad                                       2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3   freeware Advanced Audio Decoder player
ii  libfaad2-0                                 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3   freeware Advanced Audio Decoder - runtime fi
ii  libmp4v2-0                                 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3   MP4 container library - runtime files

```

```
dpkg -l | grep gstreamer0.10-plug
ii  gstreamer0.10-plugins-base                 0.10.12-0ubuntu1                       GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.12-0ubuntu1                       GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                 0.10.5-1ubuntu2                        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                 0.10.5-0ubuntu2                        GStreamer plugins from the "ugly" set
```

Someone had a similar problem earlier:
[http://ubuntuforums.org/showthread.php?t=456353&highlight=can%27t+find+decoder](http://ubuntuforums.org/showthread.php?t=456353&highlight=can%27t+find+decoder)
but no one replied with a useful answer. I'm pleading for help on this one, because if I can't play my music, hello Windows :(

---

### Post by brent113 on 2007-08-07
I'm not an expert on this, but what worked great for me was to install automatix and have it install the codecs.  Plus it's got a lot of software that it can install, so bonus!

---

### Post by paperBag on 2007-08-07
Thanks, I'll give that one a shot.

---

### Post by paperBag on 2007-08-07
> **brent113 said:**
> I'm not an expert on this, but what worked great for me was to install automatix and have it install the codecs.  Plus it's got a lot of software that it can install, so bonus!

Dude, you're a f***in' genius! It worked like a charm. You have my sincere gratitude.

---

### Post by Chappy7777 on 2007-08-07
I'm not sure what you guys are talking about. But, what I need is a way to play the .ra and .rm files that Real Audio plays when I click on "listen here" when using Windows. 

I have installed Real Audio in 6.06 and had no luck besides a message saying "can't find "source .cgi". This doesn't tell me much other than Real Audio works different in Linux. I have just installed Feisty and am in the process of rebuilding my Ubuntu PC and learning more Linux. I am about to install Real Audio and am wondering how I get it to work the way it does in Windows, meaning when I click on a "Listen Here" I will get streaming audio. 

So, will automatix help me with that, or were you talking about something different? I could really use some help. This is pretty much the last thing I need fixed before I can put away my XP machine.

---

### Post by scapalexis888 on 2007-08-07
> **Chappy7777 said:**
> I'm not sure what you guys are talking about. But, what I need is a way to play the .ra and .rm files that Real Audio plays when I click on "listen here" when using Windows. 

I have installed Real Audio in 6.06 and had no luck besides a message saying "can't find "source .cgi". This doesn't tell me much other than Real Audio works different in Linux. I have just installed Feisty and am in the process of rebuilding my Ubuntu PC and learning more Linux. I am about to install Real Audio and am wondering how I get it to work the way it does in Windows, meaning when I click on a "Listen Here" I will get streaming audio. 

So, will automatix help me with that, or were you talking about something different? I could really use some help. This is pretty much the last thing I need fixed before I can put away my XP machine.

You can try installing the linux version of Real Player from [www.real.com](www.real.com). That worked for me.

---

### Post by Chappy7777 on 2007-08-07
> **scapalexis888 said:**
> You can try installing the linux version of Real Player from [www.real.com](www.real.com). That worked for me.
=======================================

That's exactly what I did when I was putting Dapper together, I downloaded Real Player 10 from real.com into my home folder (I think it was a .bin file that I changed by closing FFox after the download and typing into Terminal: 

chmod a+x RealPlayer10Gold.bin   ENTER
sudo ./RealPlayer10Gold.bin    ENTER 
password  ENTER
(continue)  ENTER
/opt/RealPlayer  ENTER

Setup Real Player and that was about it. It never worked right. Do I have to somehow get it into FFox as a plugin?  This is from memory but I know it's close.

---

