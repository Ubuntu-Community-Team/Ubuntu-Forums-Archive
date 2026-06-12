---
title: "Is there a way to play my videos playing on VLC to Chromecast"
date: 2015-02-07
forum: Multimedia Software
---

### Post by kindafunnylookin on 2015-02-07
How can I play my video files on my big screen TV? I usually use VLC player but have need to play them on a larger screen.

---

### Post by sandyd on 2015-02-07
I have moved your thread to the *Multimedia* forum

---

### Post by mc4man on 2015-02-07
I don't have a chromecast device (maybe I should go buy one..

Anyway I'm sure there are some threads here on using in ubuntu thru chrome, maybe search out.

As far as vlc,  the 3.x (development) version does have a chromecast plugin. There probably is  a vlc ppa version with it enabled [for 14.10 or 15.04 here]("https://launchpad.net/~videolan/+archive/ubuntu/master-daily")
14.04 is a different story, I've got it in a personal ppa but not for general use of others.

So if inclined & on 14.04 this how-to will give you the plugin, how it works is presently unknown to me
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

---

### Post by SeijiSensei on 2015-02-08
Does the computer have an HDMI port?  You can connect it to the TV.  Not as convenient as a wireless connection, of course, but pretty foolproof.  You should be able to route the sound through the HDMI cable as well.

If the TV supports DLNA and is connected to the network, you might be able to use a DLNA server on the computer like minidlna or plex.

---

### Post by kindafunnylookin on 2015-02-08
I do have HMDI port, when I hook it up all I get is the Ubuntu background page and the cursor, not any content.
Wireless connects using Chromecast, but HMDI just shows the background page no matter what I do.

Thanks form your interest and reply.

---

### Post by kindafunnylookin on 2015-02-08
So far it looks like the lead you gave me ([COLOR=#000000][INDENT][http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)[/INDENT][/COLOR]
) will be my best bet. It's a pretty complicated "How To" and I'm an bit hesitant about using it and possibly breaking my VLC, also I can't be sure it's right for 64bit. thanks for your help.

---

### Post by kindafunnylookin on 2015-02-08
So far it looks like the lead you gave me ([COLOR=#000000][INDENT][http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)[/INDENT]
[/COLOR]
) will be my best bet. It's a pretty complicated "How To" and I'm an bit hesitant about using it and possibly breaking my VLC, also I can't be sure it's right for 64bit. thanks for your help.

---

### Post by mc4man on 2015-02-08
> **kindafunnylookin said:**
> So far it looks like the lead you gave me ([COLOR=#000000][INDENT][http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)[/INDENT]
[/COLOR]
) will be my best bet. It's a pretty complicated "How To" and I'm an bit hesitant about using it and possibly breaking my VLC, also I can't be sure it's right for 64bit. thanks for your help.
The how-to is well designed & meant for you to just copy & paste in order from top to bottom. Hard to go wrong really
 It will build & install a vlc 3.x dev version for your arch. ( you should really *completely* remove your current vlc first, done with - 
sudo apt-get purge vlc-data

Other than some time & space it's  quite risk free - if you don't like the vlc you built then you just remove it (sudo apt-get purge vlc) & re-install the repo version you currently have.

Keep in mind a dev version will occasionally have some issues, usually fixed quickly but that will mean a rebuild. If you want to hold off a bit I did order a chromecast, should be here Tues. so will ck. it out next week.

---

### Post by kindafunnylookin on 2015-02-08
Thanks for that. I'm going to try that tonight. I'll post results after testing.

---

### Post by kindafunnylookin on 2015-02-08
Actually, I may wait til you try it.

---

