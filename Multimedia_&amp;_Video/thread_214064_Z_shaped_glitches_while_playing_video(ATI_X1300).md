---
title: "Z shaped glitches while playing video(ATI X1300)"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by AgentOOK on 2006-07-12
Hi , I installed Dapper Drake recently and everything is running all right but I have some problems with video/DVD playing. Be it with Kaffeine , Mplayer or VLC, while playing a video(or a DVD) I see Z shaped lines appearing and disappearing particularly when there is scrolling(in the film) . 

I tried  to take a screen capture of it but for now I haven't manage to do it.

I'm using ATI drivers(8.25.18) on a Sapphire ATI X1300, KDE and I just downloaded the latest kernel.

If you need more information to diagnose the problem just let me know.

---

### Post by AgentOOK on 2006-07-13
So I understood it has certainly something to do with vsync and page tearing. it seems that the problem is quite common for ATI [-( 


I tried to reconfigure the xserver but to no avail. 
(It indicates the right config 1280*1024@75Mhz)

I installed driconf(and set up the option to yes) the  but it didn't help either.


I also tried to specify my monitor(Belinea 101735) : it didn't existed in the list so I just picked one with the name who looked like it(Belinea 101715). The tearing disappeared but the gnome login screen was appearing only in part and the video seemed sluggish. The text(for commands) on kaffeine was quite big also.

---

### Post by krazyd on 2006-07-16
Apparently with X1xxx series cards, ATI drivers still don't correctly support video overlays resulting in tearing. From the horse's mouth: [http://rage3d.com/board/showthread.php?t=33857432](http://rage3d.com/board/showthread.php?t=33857432) (see post #6)

Edit: I really wish ATI would get their act together on this. It makes linux barely useable if you happen to own ATI X1xxx card and an LCD screen..

---

### Post by legzelda on 2007-06-06
I'm having the same problem with my X1400 in my Dell E1505 laptop.  I tried running

```
sudo aticonfig --sync-video=on
```

and

```
sudo aticonfig --vs=on
```

Neither one worked.  I also tried turning off these switches, but I still get the same Z-shaped tearing you describe.  These page tearing/vsync issues make using Ubuntu, especially for multimedia purposes, especially frustrating.  Does anyone have any suggestions for fixes?

---

### Post by Maverickprowls on 2007-06-06
I'm having the same problem with my nVidia GeForce 6150.  Glitches appear about one third of a way down the screen particularly when rapid horizontal motion is being displayed.

---

### Post by SGTEdwards on 2007-06-09
Same here

Im using Ubuntu 7.04 recently (got rid of XP), XFX Nvidia Gforce 4 MX 4000,
When I try to play avi, mkv, DVD video I get visible horizontal lines glitches on some scenes
or high motion scenes.

I get back to my sis XP to watch my videos :popcorn:

---

