---
title: "Independent DPMS control for displays?"
date: 2008-04-27
forum: Multimedia Software
---

### Post by DorianX on 2008-04-27
I've got an nvidia GeForce 8300 that's hooked up to use DFP and TV-out as separate X screens.

What's driving me crazy at the moment is that I can't seem to get independent control over the DPMS features.

I want to be able to turn off the TV-out when I'm not using it (Without reconfiguring the X server and therefore needing to restart X) When I try this:

xset -d :0.1 dpms force standby

both screens go out, and as soon as I touch the mouse, both screens come back on.  The same happens with :0.0 or with no -d option at all (The TV-out is :0.1) 

The reason I need this is that I only use the TV out occasionally, and the rest of the time I want the output turned off because the connection is via an auto-sensing switch.  It's incredibly annoying to be watching TV or a DVD, then touch my computer, wanting to use the main (that is, not the TV) screen, only to have my show or movie interrupted to show me an empty gnome desktop on my television.

Things seem to have gotten worse since I upgraded to Hardy as well: the video card would only trigger the switch when X was restarted before, now it happens every time the display wakes up from standby.

---

### Post by DorianX on 2008-05-02
I just found nvtv, which seems like it ought to do the thing I want (specifically, it's got a "turn tv output off" option), but it says "No supported cards found" when I run it.  Can anyone confirm or deny whether nvtv is compatible with this particular card?

---

