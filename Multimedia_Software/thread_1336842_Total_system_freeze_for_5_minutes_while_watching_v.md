---
title: "Total system freeze for 5 minutes while watching videos"
date: 2009-11-24
forum: Multimedia Software
---

### Post by ivotedforkodos on 2009-11-24
This has been really bugging me. When I watch videos, the system will freeze for up to 5 minutes for no apparent reason. This will happen at seemingly random intervals, between 5 and 10 times during a DVD, and it is EXCRUCIATING. 

I've tried all the media players, VLC, XBMC, SMPlayer, Totem, they all do it. I don't think it's related to the DVD drive, since it happens when I'm watching ripped DVDs and downloaded TV shows in Miro. The system always comes back, but during the lockout (which can last up to 5 minutes!) I can't do anything. No mouse movement, no clock ticking, no Force Quit, no Ctrl-F1, no Ctrl-Alt-Del, nothing. I can't even eject the DVD manually! However, when the system comes back, the keystrokes are executed. 

I ran VLC in a terminal and this is the error that pops up during each freeze:

[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)

I do see some fglrx errors in dmesg:

[ 5376.641358] [fglrx:firegl_lock_free] *ERROR* lock was not held by 1! (*lock=0x80000005)
[ 5376.641363] [fglrx:firegl_unlock] *ERROR* firegl_lock_free failed!
[ 5385.065694] [fglrx] GART Table is not in FRAME_BUFFER range 
[ 5385.090732] [fglrx] Firegl kernel thread PID: 6342
[ 5385.098425] [fglrx] Gart USWC size:816 M.
[ 5385.098428] [fglrx] Gart cacheable size:60 M.
[ 5385.098433] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[ 5385.098435] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 

but I'm not sure if that's related. Does anyone have any ideas as to what this might be, or how to correct it? I'm running Jaunty with an ATI graphics card. 

Thanks!

---

