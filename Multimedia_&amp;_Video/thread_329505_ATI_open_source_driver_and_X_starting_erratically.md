---
title: "ATI open source driver and X starting erratically"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by kalahari875 on 2007-01-01
I have an ATI All-In-Wonder 8500DV video card. Before I start, let me say that I tried using the fglrx drivers and, when I got hardware acceleration, X would always hang when opening desktop windows so it was unusable. If I dsabled hardware acceleration, video performance was very poor. 

So, I am using the open source radeon driver ("ati"), and I get nice video performance with hardware acceleration.

Kubuntu Edgy does not shut down cleanly. It tries, but after the screen clicks to change video modes nothing else ever appears. The machine does not shut down or reboot. 

When I SysRq or pull-the-power-cord reboot it, the first time coming up it never starts X successfully (it changes video modes after briefly showing the "Kubuntu" screen, but never shows the wait cursor or subsequent login dialog). If I reboot it again, it will usually boot successfully the second time.

I have pored over the log files trying to figure out what the problem is and don't see it. I've attached several logs. Can anyone help?

[ATTACH]22045[/ATTACH]
[ATTACH]22043[/ATTACH]
[ATTACH]22046[/ATTACH]
[ATTACH]22047[/ATTACH]
[ATTACH]22048[/ATTACH]

Thanks in advance. I don't want to have to buy a new video card. ](*,)

---

