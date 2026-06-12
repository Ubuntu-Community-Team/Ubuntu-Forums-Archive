---
title: "Can' play RMVB files"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by gReEnT3a on 2007-04-01
After a fresh installation of Feisty, i am trying to get it play multimedia files.

I have no problem in playing AVI, WMV, MP3 and other file formats, but it just won't play RMVB files. It gives an error saying "Video codec Real Video 4.0 is not handled". I have already install w32codecs and libxine, libxine-extracodecs....

Did I missed anything?

Advices is appreciated :p

EDIT: I am currently using Totem-Xine

---

### Post by baosheng on 2007-04-03
i also had this problem.
maybe you should ask this question again at Feisty Fawn sub-forum.

---

### Post by senuxis on 2007-04-05
You need to install Realplayer for Linux. There is a package in the Dapper and Edgy Eft repository,  but, I'm not sure about Feisty Fawn.

---

### Post by gReEnT3a on 2007-04-05
Personally I don't think RealPlayer is a good choice, I don't even use it in Windoes :lolflag: 

Playing RMVB file works file with Totem-Xine in both Dapper and Egdy, but not in Feisty (for me).
I understand that its still in beta, but i thought there might be some workaround to this~

I've installed XINE-UI, and RMVB works fine with it though....wonder why it doesn't work with totem...

bug?

---

### Post by hanzomon4 on 2007-05-04
If you use totem-xine in feisty follow these instructions.> **NeoChaosX said:**
> I'm having this problem, too. It started happening in Feisty; in Edgy, Real files played audio just fine in Kaffeine as well. It was exactly like one problem I had a year ago when I couldn't get WMVs to play sound despite having w32codecs installed; it turns out I had to tweak ~/.xine/catalog.cache to get it to play sound. Maybe playing with that file again will get it working, but I'm not so sure.

chggr: I'd prefer not to use VLC for a number of reasons, one of which there are some format it actually doesn't support (I have a few videos encoded in Indeo v4, which it doesn't support). So fixing xine to get this working would be preferable.

ETA: Found a solution. Open up ~/.xine/catalog.cache in a text editor and find this section:
```
[/usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so]
size=11300
mtime=1171041406
type=131
api=15
id=realadec
version=10104
supported_types=52494336 52559872 52756480 
decoder_priority=5
```
Bump up the 'decoder_priority' value to 10. That should get audio with Real files working.

First scratchy sound in SDL games, now this. And Canonical smoothed out all my audio problems with Edgy...

---

### Post by Madlax on 2007-07-08
The fix worked for me......thank you so much

i had a lot of trouble installing the w32 codecs,only to find my Rmvb files plays fine but with no audio

with this fix Audio is fine now

i think anyone with the problem should try it...

---

### Post by 65 mustang on 2007-08-19
:KS Thankyou!  That worked.

---

### Post by vitorsouza on 2008-03-11
I couldn't play RMVB files in Kaffeine, although they worked in mplayer. What worked for me was editing ~/.kde/share/apps/kaffeine/xine-config and uncommenting the decode.external.real_codecs_path line, completing with the codec directory.

decoder.external.real_codecs_path:/usr/lib/codecs

Hope it helps others with the same problem as me.

---

