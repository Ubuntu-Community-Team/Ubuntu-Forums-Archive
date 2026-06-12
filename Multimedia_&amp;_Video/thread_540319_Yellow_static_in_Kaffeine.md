---
title: "Yellow static in Kaffeine"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by srunni on 2007-09-01
Hi,

I'm trying to play a 720p .mkv file in Kaffeine, but I keep getting yellow static when playing it. I don't have any static problems with VLC Media Player or MPlayer, but I have audio problems with them, so I can't use them. Is there any way to fix the problem in Kaffeine?

Thanks in advance for the help!!

---

### Post by wolfen69 on 2007-09-01
it sounds like a sound card issue to me.

---

### Post by Amazona aestiva on 2007-09-01
Are win32 codecs installed? Those perhaps help.
Use the first link in my signature, and find Kaffeine.

---

### Post by srunni on 2007-09-01
@wolfen69:
It's not a audio problem, it's a video problem.

@Amazona aestiva:
Yeah, win32 codecs are installed.

---

### Post by Amazona aestiva on 2007-09-01
Ubuntu uses Kaffeine 0.8.3.
Here is the 0.8.4(that I use):[http://www.getdeb.net/app.php?name=Kaffeine+Player]("http://www.getdeb.net/app.php?name=Kaffeine+Player")
You have to remove the older version with this: (before install 0.8.4)
```
sudo apt-get remove kaffeine-xine
```

---

### Post by srunni on 2007-09-01
Actually, I'm running Kaffeine 0.8.5 - I have the Feisty backports repository enabled.

---

### Post by Amazona aestiva on 2007-09-01
I see...
I Haven't enabled them...
and what's the problem with VLC or Mplayer?
You wrote something about sound error, issue?

---

### Post by srunni on 2007-09-01
With VLC and MPLayer, I can't get the sound as loud as I can in Kaffeine. I'm running a Sony VAIO PC, which has a Sigmatel audio card. The Linux driver for this card isn't perfect, and the sound isn't anywhere near as loud as it is in Windows. I usually have to turn up the volume all the way on my 505 watt surround sound speaker system to get a decent level of sound in Linux (on Windows, about 30-35% volume is enough). However, this doesn't seem to work as well in VLC or MPlayer as in Kaffeine. I would personally like to use VLC for everything, since that's what I was used to back in my Windows days, but after upgrading from Dapper to Feisty, I had some issues with scratchy sound in VLC. I fixed that, but the sound still isn't as loud as I'd like it to be. If there's a way to simply increase the max volume limit in VLC/MPlayer, that would be perfect.

---

### Post by Amazona aestiva on 2007-09-01
If I turn volume max in VLC, the sound became ugly. I think because it is too loud?

So if I'm right VLC's max volume is above 100%. (I'm not sure)

I advise to get a Sound Blaster from Creative labs. Those cards usually works correctly, and most of them is cheap. Of course this problem with your card might get solved in the close future.

---

### Post by srunni on 2007-09-01
Yeah, I've been thinking about getting a new audio card. Since there's no way to know when the problem will be solved, that would be the best option.

As for the sound in VLC losing quality when you turn it up, I can't turn it up high enough for that to happen.

---

### Post by Amazona aestiva on 2007-09-01
In Mplayer there is a way to increase max volume!!!!!!(perhaps)
First
Right click -> Preferences -> audio -> enable equalizer

Then
Right click -> equalizer -> try to modify them(every with the same quantity)

Hey it's only an idea I haven't try it!

---

### Post by Amazona aestiva on 2007-09-01
Or try XMMS media player: (This haven't worked for me)
```
sudo apt-get install xmms
```

---

### Post by srunni on 2007-09-01
Hmmm, the settings in the equalizer are grayed out, and I can't change them. Can you change them?

I'll give XMMS a shot - I thought it was audio only.

---

### Post by Amazona aestiva on 2007-09-02
Have to enable the equalizer before modify:
> First
Right click -> Preferences -> audio -> enable equalizer

XMMS audio only?:oops:... I have said it never worked for me...

So Sound Blaster works... I have no idea. Sorry...

---

### Post by srunni on 2007-09-02
Well, according to Wiki ( [http://en.wikipedia.org/wiki/Xmms](http://en.wikipedia.org/wiki/Xmms) ) it's an "audio player", so I guess video wouldn't work in it. I still can't get MPlayer to let me change the equalizer settings though....I'll see if I can get some help on IRC.

---

