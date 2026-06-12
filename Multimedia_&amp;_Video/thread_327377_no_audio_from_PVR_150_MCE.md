---
title: "no audio from PVR 150 MCE"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by pathdoc on 2006-12-29
Hi,
I recently bought an OEM hauppauge pvr 150 mce.  so far, I've gotten myth working and can output video from mplayer as well.  the only problem is that there is no audio coming out of my audigy 2.  everthing else in regards to sound works fine on the system.  i am using edgy btw

any help would be appreciated.

---

### Post by pathdoc on 2006-12-29
never mind.  I followed the firmware installation for ivtv on the edgy web page, but somehow, the sound firmware never got installed.  I just installed it manually and it seems to be doing the trick!

---

### Post by superm1 on 2006-12-29
> **pathdoc said:**
> never mind.  I followed the firmware installation for ivtv on the edgy web page, but somehow, the sound firmware never got installed.  I just installed it manually and it seems to be doing the trick!
Do you know by chance which firmware file was missing?  Did you install the firmware deb to start, or did you install this deb to resolve it or the tgz?  If there was a packaging cruft bug, i'd like to nail this.

---

### Post by Robocoastie on 2007-01-27
how on earth did you get your pvr 150 mce to work in the first place? on edgy I get a blank screen when I fire up xawtv and have to ctrl-alt-F keys to cycle back into x,  and with tvtime I get blue screen and says no input device cannot open capture device /dev/video0.

Video0 is probably the wrong device but I can't for the life of me figure out how to change that, linuxtv.org does nothing but link over to mythtv site which is equally archaic and useless. The wiki's seem to talk about nothing anymore except how to program, nothing about setting up the card. It's maddening.

ps ignore the forum saying I'm running "Breezy" on the right hand side I haven't figured out how to change that. I'm running Edgy 6.10 64bit.

---

### Post by superm1 on 2007-01-27
> **Robocoastie said:**
> how on earth did you get your pvr 150 mce to work in the first place? on edgy I get a blank screen when I fire up xawtv and have to ctrl-alt-F keys to cycle back into x,  and with tvtime I get blue screen and says no input device cannot open capture device /dev/video0.

Video0 is probably the wrong device but I can't for the life of me figure out how to change that, linuxtv.org does nothing but link over to mythtv site which is equally archaic and useless. The wiki's seem to talk about nothing anymore except how to program, nothing about setting up the card. It's maddening.

ps ignore the forum saying I'm running "Breezy" on the right hand side I haven't figured out how to change that. I'm running Edgy 6.10 64bit.
Setting up the card is described in [http://help.ubuntu.com/community/Install_IVTV_Edgy](http://help.ubuntu.com/community/Install_IVTV_Edgy)

tvtime's website says it doesnt support ivtv cards however.

---

### Post by Robocoastie on 2007-01-28
thanks, yea I followed the ivtv walk through. it seems the card is working I just wasn't using any proper program to actually use it with. It seems mythtv is the only program which supports it and I've tore my hair out trying to set that up. gawd, no thanks. one thing after keeps Linux from being the all purpose desktop of people's dreams. oh well, I've burned far far too much time over the last several days trying to get multimedia to all work waste of time, energy and resources, the multimedia/power machine will remain with XP 2005 until I'm forced due to driver death into getting VISTA and the old 900mhz will stay the one that real work gets done on with Xandros 3x. which continues to be the most rock solid stable linux I've used since my Slackware days (course it's draw back is bleeding edge h/ware won't run on it).

---

### Post by superm1 on 2007-01-28
> **Robocoastie said:**
> thanks, yea I followed the ivtv walk through. it seems the card is working I just wasn't using any proper program to actually use it with. It seems mythtv is the only program which supports it and I've tore my hair out trying to set that up. gawd, no thanks. one thing after keeps Linux from being the all purpose desktop of people's dreams. oh well, I've burned far far too much time over the last several days trying to get multimedia to all work waste of time, energy and resources, the multimedia/power machine will remain with XP 2005 until I'm forced due to driver death into getting VISTA and the old 900mhz will stay the one that real work gets done on with Xandros 3x. which continues to be the most rock solid stable linux I've used since my Slackware days (course it's draw back is bleeding edge h/ware won't run on it).
Well VLC can also be used with these cards, but i'm not sure if it supports doing the channel changing in VLC.  I use them with myth myself :)

Sorry to hear you leaving ubuntu!

---

