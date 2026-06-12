---
title: "AC97 Sound Not Working in 8.10"
date: 2008-11-05
forum: Multimedia Software
---

### Post by tlongren on 2008-11-05
Hi All,

I've read many, many posts recently about audio problems, most of which relate to pulseaudio not being configured properly.  I'm not convinced any of those topics relate to my problem.

I upgraded from 8.04 a few days ago to 8.10 and now I have no sound at all.

Here's what lspci says I have for a sound card:
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

```
When I issue the "aplay -l" command, I get this result:
```
aplay: device_list:215: no soundcards found...
```

When I right-click on the volume control applet and left-click "Open volume control", I get this error:
```
No volume control GStreamer plugins and/or devices found.
```

Now, I have the exact same sound card in another box running 8.10 and it works OK.  I'm not even able to get the modules to load on this problem box.  I noticed the soundcore module isn't even loaded on this problem box, and no modules with "snd" in the name are loaded.

Can anyone help me out here?  I can provide many more details if requested, I'm just not sure what's needed to help figure out what's going on here.

Thanks!!

---

### Post by jkmspyksma on 2008-11-12
A possible solution has been posted on a different thread:

[http://ubuntuforums.org/showthread.php?t=968054](http://ubuntuforums.org/showthread.php?t=968054)

The symptoms you've given look exactly like those I had on my Lenovo laptop with an AC'97 Audio Controller.

Let me know if it works for you.

---

