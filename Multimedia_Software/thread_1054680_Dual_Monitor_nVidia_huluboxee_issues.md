---
title: "Dual Monitor nVidia hulu/boxee issues"
date: 2009-01-29
forum: Multimedia Software
---

### Post by RusH487 on 2009-01-29
I've recently installed Ubuntu Hardy on my desktop with a GeForce5200XT video card and the latest nVidia drivers.

I have an NEC 15" monitor (secondary) hooked up as well as a 37" Westinghouse 1080p LCD (primary) in a dual monitor configuration (Westinghouse on DVI and NEC on VGA).  My problem is that when I go to run Hulu in full screen mode on the 37" it tries to run full screen between both monitors with the picture split in the middle.  When I go full screen on the 15" monitor, however, it works perfectly fine.

My other issue is that I just installed Boxee and when I go to run it in full screen mode it shows up 5x bigger than it should be with half the buttons cut off.  It then proceeds to lag so badly that I can't shut it down with the mouse, only Alt-F4.  When I run it in windowed mode everything runs as it should, but when I go to make something full screen it lags again to the point where I can't watch it.  I don't understand this as when I play a DivX movie with VLC at full screen it runs perfectly fine.

I realize this is an obscure problem and I probably won't get any responses, but I figured it would be worth a shot to ask just the same.

---

### Post by macpointman on 2009-02-11
I am running into the same issues running an ATI card and drivers with Compiz installed Otherwise everything works great

---

### Post by RusH487 on 2009-03-03
Ultimately, I found the quick (and PITA) fix for this was just to disable one of the display outputs.  When running on one screen, everything worked fine.

---

### Post by Rob Maurer on 2009-03-09
How do you do that? (How do you disable one of the display outputs)? I am having the same issue with Boxee.

---

### Post by RusH487 on 2009-03-09
I don't recall the exact way to do it being as I've since built a new machine that no longer uses nVidia, but if you open your terminal and type in > sudo nvidia-settings there should be a spot under the 'type x settings' where you can select to only have one monitor displayed instead of two.  Apply the settings and the second monitor should shut off.  Then, when you run Boxee it should only run on the remaining screen.  If you really have problems getting this to work, let me know and I'll see if I can't dig up my old machine again to figure out how to do it more clearly.

---

### Post by kewljedi on 2009-05-29
I got boxee to use only one monitor by using the Window Rules plugin for Compiz. 

Prefs->Compiz Settings Manager
Enable Window Rules
Add a Size Rule
name=Boxee
set the size to be smaller than one monitor, or it will try to use both.

---

