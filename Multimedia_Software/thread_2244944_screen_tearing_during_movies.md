---
title: "screen tearing during movies"
date: 2014-09-19
forum: Multimedia Software
---

### Post by redrumrogue on 2014-09-19
Hi all,

Apologies if this has already been discussed - i'm after some fresh ideas!  I've been seeing some horizontal screen tearing while playing movies.  I have my PC hooked up to my HD TV via HDMI.  PC has an nVidia GeForce GT620 card and I'm using the latest stable driver from nvidia v340.32.  I know  people may advise me not to use that driver and use the ubuntu repo ones but I'd like to see what settings I could at least try and tweak with my current driver to improve / eliminate the screen tearing.  The rest of my machine spec is in my signature below, in case it's relevant.

Anybody else had and solved this issue?

---

### Post by T.J. on 2014-09-20
If you are getting tearing during video playback, it is because the OpenGL driver is not syncing with the monitor during the refresh or your system is using XRender instead.  There are ways to fix this, but in order to get down to specifics, I need more information, specifically what Desktop environment you are using, what video card, and what version of the driver.  Normally, knowing all this would not be necessary, but you may have something misconfigured in the graphics stack.  Unfortunately, not all programmers making software on Linux (or Windows for that matter) follow the proper standards.

---

### Post by redrumrogue on 2014-09-20
Hi TJ - All the info you asked for is in my previous message.  The only difference is today i updated my driver to thr new v343.22.  I haven't tested it yet for tearing but will tonight and report back here.  Thanks for replying!

---

### Post by mc4man on 2014-09-20
If "Ubuntu-Gnome" means gnome-shell (or any non compiz session) the try adding these 2 lines to /etc/environment & log out/in or restart
```
CLUTTER_PAINT=disable-clipped-redraws:disable-culling
CLUTTER_VBLANK=True
```

---

### Post by redrumrogue on 2014-09-20
Hi mc4man - thanks for the tip.  I just watched a movie after updating the nvidia driver from v340.32 to v343.22 and there was no screen tearing.  If I see any tearing in the future I'll try those lines in my environment file.

Thanks for your help!

---

### Post by mc4man on 2014-09-20
Hopefully it's gone. If you want to test directly i've 2 vids that can expose tearing.
They're not an absolute test but pretty good, worth checking in both windowed & fullscreen.
this is small, look for no breaks in column
[http://www.datafilehost.com/d/2b12e94b](http://www.datafilehost.com/d/2b12e94b)
This one is a little bigger, first min from sintel. Tearing can occur around 30 sec's  in during the fight scene
[http://www.datafilehost.com/d/5942d3d3](http://www.datafilehost.com/d/5942d3d3)

---

### Post by redrumrogue on 2014-09-21
Hi there - thanks for the videos! Sadly, the tearing is still there but i've found it's only there is full screen and not in windowed.  I've played the teartest.mp4 video in VLC and Totem and (in fullscreen) in VLC the tear slowly works it's way down the screen and in totem the tear stays near the top of the screen.  I wonder if there are any settings in VLC that I can change?  Does anybody have an opinion on VLC vs Totem for video playback?

---

### Post by redrumrogue on 2014-09-21
I think i've found a solution .... in VLC preferences, in the Video section I changed the Video Output setting from Auto to "OpenGL GLX video output (XCB)" and so far there is no tearing in the teartest.mp4 video or any other movie file I play.  Will test this out for a while and see how it goes.

---

### Post by redrumrogue on 2014-09-22
So far so good!  Marking thread as SOLVED

---

