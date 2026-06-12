---
title: "Sound gone with the wind"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by eeried on 2008-01-17
Hello,

Here's some output (aplay -l ans lspci -v):
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at fa000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

```
card  0: Intel [HDA Intel], périphérique 0 : ALC883 Analog [ALC883 Analog]
  subdevice : 0/1
  subdevice : #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC883 Digital [ALC883 Digital]
  Ssubdevice : 1/1
  subdevice : #0: subdevice #0
```

In fact I have a Realteak ALC888 card.

All was well until this morning: I listened to some music on Jamendo and I donwloaded some music through Bittorrent and the sound went/ I tried to use Audacious on my downloaded (leagal, thank you) music,a nd threr's a message saying to check if I have permissions, or if the device is busy.

I got the same results yesterday while trying to configure Ekiga (trough the druid), and yet the sound was alright tot listen to Jamendo albums on line.
The sound did work on Ekiga some time ago.

Is there something wrong with Jamendo (at one point this morning I had to kill firefox because jamendo seemed to a ressource hog, and firefox froze)? or can it be something else that stops the sound?

Your help would most appreciated!.

---

### Post by namnam on 2008-01-17
When you say you listen to Jamendo online, is that through flash? I know flash on 64bit systems can cause problems with sound.

---

### Post by eeried on 2008-01-17
Thanls for your reply namnam.

I have no idea what Jamendo onboard player is. It may be flash but I have the 32bits version of Gutsy, and I have the flash plugin -- I didn't install flash I just downloaded the tar.gz file from Adobe, and extracted it then copied the .so file to the firefox plugin dir. 

Anyway, I think Jamendo-orange alone is reponsible for that sound problem. After quitting Firefox I was able to listen to a downloaded track on Audacious.

Jamendo-orange is a bit of a bug -- they're working at the new site and it's improved since a couple of days ago.

Well, I've hit upon ogg.jamendo which is orange too, and brand new, and offering ogg only is more to my linking. I'll see if it's less buggy.

However I was very happy with playing tracks using mplayer plugin which is so good (I don't need a flash player or Totem player, but appearance and modernism win the day :(

---

### Post by eeried on 2008-01-22
That was Jamendo alright...

---

