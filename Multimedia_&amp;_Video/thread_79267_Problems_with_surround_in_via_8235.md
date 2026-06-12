---
title: "Problems with surround in via 8235"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by faustobp on 2005-10-19
I'm having problems to setup my sound card (on board via 8235) to duplicate the stereo output on the surround speakers (line in configured as out).

There is no "surround" volume control in the gnome-volume-control (it is just a switch).

amixer shows:
```

Simple mixer control 'Surround',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Front Left: Playback [on]
  Front Right: Playback [on]

```

But I think it shoud show something like this:
```

Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 24 [77%] [on]
  Front Right: Playback 24 [77%] [on]

```

Some one knows how to enable the volume control to the surround channels? Is this a bug?

---

### Post by campbeln on 2006-10-09
I'm having the same issue (well, I was!). I found this post in another forum:


[from [https://launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/45246]](https://launchpad.net/distros/ubuntu/+source/alsa-utils/+bug/45246])
Arthur Penn  at 2006-05-31 22:25:09 UTC

I had the same problem after upgrading Breezy to Dapper RC, but not on a ThinkPad--instead on a frankenbuild Athlon XP 2200+ desktop. In my case, in alsamixer there were four identical entries labeled VIA DXS all the way to the right of the mixer console. These were all turned down to zero. I turned them up to 81 and then I got sound from speaker-test, KDE, etc.


So I fired up a shell, ran 'alsamixer' then arrowed to the right all the way, and there they were... 3 levels for 'VIA DXS'. I turned these babies up to '100<>100' and my sound is back to normal. Best of luck!!

---

