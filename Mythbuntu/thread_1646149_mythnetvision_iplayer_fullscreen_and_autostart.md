---
title: "mythnetvision iplayer fullscreen and autostart"
date: 2010-12-15
forum: Mythbuntu
---

### Post by Crowie on 2010-12-15
Hi 

Is anyone else unable to play bbc iplayer on mythnetvision if the display is set to fullscreen (default) at the start.  If I edit the bbciplayer.xml and change to either bbcweb or bigscreen it works fine.

Also is it possible to have bbciplayer content automatically play when it is selected from within mythnetvision.  Similar to youtube content and other players.

Thanks

---

### Post by JasonEde on 2011-01-09
That helped get my iplayer working too. I've been wondering about using the remote to start amd stop iplayer stuff... I've found this [http://hatherly.com/blog/?p=31](http://hatherly.com/blog/?p=31) which looks promising. Will post back if it get it working.

---

### Post by JasonEde on 2011-01-15
Well I've got mouse movements working in mythnetvision using link above. I needed to start irexec in my .profile and have the line before it xhost +

Now I noticed that after applying updates iplayer never actually starts playing... It thinks about it a lot and then eventually says unable to start. I've checked the xml file and it is set to bigscreen. Have also tried bbcweb, but same thing there.

Any ideas on things to try?

---

### Post by Crowie on 2011-01-20
bbcweb or bigscreen works fine for me its just when its set to fullscreen and there doesnt appear to be any autoplay for iplayer at present.

I believe there is some further work in 0.25 for remote control use.

---

