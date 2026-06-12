---
title: "No DVD Playback"
date: 2009-04-02
forum: Multimedia Software
---

### Post by shade34321 on 2009-04-02
so my DVD's wont play...i've installed the medibuntu repo, and it still wont play...vlc will open a window to play it and automatically close it out.....MPlayer looks like it's trying to play it but the picture is garbled then it goes crazy....Totem starts to play it and gets through the legal stuff when it tells me it cant read the resource anymore. I'm using Jaunty. I've made sure the DVD drive works and browsed some picture's that were on a DVD. This computer had windows on it before I installed Ubuntu and it played these DVD's then without a problem. Any ideas on how to fix this would be greatly appreciated.

---

### Post by Therion on 2009-04-02
Fire up a Terminal and cut and paste:```
sudo aptitude install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2
```

---

### Post by shade34321 on 2009-04-02
Thanks!!!! It worked......I've  been working on this for about a month!!! Thanks!!!

---

### Post by Therion on 2009-04-03
> **shade34321 said:**
> Thanks!!!! It worked......I've  been working on this for about a month!!! Thanks!!!
No problem, glad that worked out for you.  

Further, while most of us do appreciate a user who tries to research and resolve on their own, instead of pounding your head against a wall for an entire **month**, allow me to remind you the forums *are* free and most of us don't bite.  Not hard anyway.

;)

---

### Post by mavbt1 on 2009-04-11
Thank you.. This fixed the playback issue...

---

### Post by Swagman on 2009-04-12
Wish it did for me. All I get is

> 
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: 16352
libdvdnav: DVD Serial Number: 28A59D99
libdvdnav: DVD Title (Alternative): 16352
libdvdnav: Unable to find map file '/home/susan/.dvdnav/16352.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdread: Invalid main menu IFO (VIDEO_TS.BUP).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
libdvdread: Invalid IFO for VMGM (VIDEO_TS.BUP).
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/scd0' failed: could not create access: no access module matched "dvd"


---

### Post by Jpardue on 2009-04-12
The comprehensive multimedia how-to sticky in this thread shows all the packages you need for DVD playback in vlc. His whole sticky is necessary to anyone wanting complete multimedia playback in ubuntu. I'm sure you are aware it's there, this is just a reminder :)

---

### Post by Swagman on 2009-04-13
I may be mistaken but his sticky goes through a process of uninstalling flash etc on the way.

Well flash works just fine on my machine so why would I uninstall it when it's playing dvd's that I would like solved ?

Just to clarify... I'm not actually bothered that dvd's don't play on my system.... HOWEVER

As I have successfully managed to persuade someone to install Ubuntu it would be nice for others  reading his Trials and Tribulations to see how good Ubuntu is.

[**Trials and Tribulations**](http://www.peterborough.net/forum/forum_posts.asp?TID=6738&PN=1&TPN=4)

I figured.. heck I'll suss the bugger out on my machine then show him (or point him here) how to do it.

---

### Post by hosoka on 2009-04-13
Is this the similar action that is needed for earlier request on [http://ubuntuforums.org/showthread.php?t=1124237](http://ubuntuforums.org/showthread.php?t=1124237)  ??

---

