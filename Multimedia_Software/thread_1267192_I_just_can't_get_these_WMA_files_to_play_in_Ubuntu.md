---
title: "I just can't get these WMA files to play in Ubuntu, what am I missing?"
date: 2009-09-15
forum: Multimedia Software
---

### Post by hoppipolla on 2009-09-15
Heya, I have some wma9 files I want to play in Ubuntu but it fails to find codecs - I have installed the restricted-extras package... I'm not really sure what's missing?

Thanks guys - I'm actually trying to play them in Banshee but they don't really seem to play in anything - any thoughts?

Hoppi :)

---

### Post by hoppipolla on 2009-09-15
Please help meeeee! ^_^

(I have awesome tracks by The Starting Line that I want to play lol :) )

---

### Post by mc4man on 2009-09-15
The short of it
wma2 - all players, for gstreamer players one of the gstreamer plugins, you should be good there because of the restricted extra's thing

wma3 ( 9.1 Professional) - all players with w32codecs installed ( get it from medibuntu
gstreamer players also need the gstreamer0.10-pitfdll installed (search gstreamer in synaptic

wma3 (Windows Media Audio 10 Professional) - all players that can use w32codecs - gstreamer players **probably** can't play

wmal - all players that can use w32codecs, gstreamer player **will not** play

Some players that can play all - amarok, mplayer, a well built vlc, most xine based players

Note: all wma3 (9 and 10) can be decoded by a recent ffmpeg, some players built off of that will be able to play in the absense of w32codecs, most notably mplayer and a modified vlc. 

All versions of wma can be enabled for gstreamer players with the purchase of the fluendo windows media pack (gstreamer only

---

### Post by hoppipolla on 2009-09-15
Awesome thank you, I've just installed Medibuntu so I'll see how I get on :)

---

### Post by hoppipolla on 2009-09-17
Nope ._.  Still nothing.. how weird ._.

---

### Post by TheStroj on 2009-09-17
Try VLC, it has almost all codecs installed.

---

### Post by zeronothing on 2009-09-17
Also check to make sure your files are not DRM WMA files. If they are DRM that would cause them not to play. Did you download them from a online store?

---

### Post by mc4man on 2009-09-17
Why don't you try to idenify the type of wma you have.

A right click properties -> audio is somewhat helpful though can't tell a wma3 9.1 from a wma 10

Mediainfo will give complete info 
[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

You'd need to pick your release and install from bottom to top (cli package not needed
( libzen0, libmediainfo0, gui
Easy way is to open mediainfo and then drag and drop file into, then switch the view to hmtl for full info, text to copy

opening Banshee from the  terminal would show something like this for wma3 (10) (which banshee can't play

> (Banshee:13602): GStreamer-WARNING **: pad dmodec_wmadmodv30:src returned caps which are not a real subset of its template caps
Total Unfree 0 bytes cnt 0 [(nil),0]


A wmal in banshee would show this
> ** Message: don't know how to handle audio/x-asf-unknown, codec_id=(int)355
[Error 11:29:18.687] GStreamer stream error: CodecNotFound
no application found


Wma2 and wma3 (9.1) play fine

Is there any possibility the wma's are 'locked' (encrypted)?

Edit>
> Try VLC, it has almost all codecs installed.
No repo, and probably no ppa vlc will play wma3 or wmal

What is capable of in regards to wma

[http://ubuntuforums.org/showthread.php?p=7794653#post7794653](http://ubuntuforums.org/showthread.php?p=7794653#post7794653)

---

### Post by hoppipolla on 2009-09-17
I actually removed them as I thought I would just hunt them down as mp3s (to be honest I don't know why I felt it necessary to fully DELETE them but it seemed like a good idea at the time lol)... it's weird though how tricky they were to play - I might stick to mp3s and oggs and stuff now if I can :)

---

