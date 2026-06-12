---
title: "Using XEV to detect Multimedia Keys"
date: 2009-01-03
forum: Multimedia Software
---

### Post by earthmeLon on 2009-01-03
I recently set up my laptop to accept input from my Wiimote (I love it!!) and while trying to set up a configuration to use the remote to control my multimedia, I ran into a problem using xev (to detect the keys).

Whenever I pressed a button, I would get something like:

```
FocusOut event, serial 34, synthetic NO, window 0x4e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x4e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```

I wasn't able to figure out the keycode or keysym and it was getting painfully annoying (I couldn't find any support anywhere)

For some reason, I decided to hold down SHIFT and then press the buttons.  Perfect :D  Now I got my keys:

```
KeyRelease event, serial 35, synthetic NO, window 0x4e00001,
    root 0x1a6, subw 0x0, time 43402641, (-396,69), root:(338,753),
    state 0x11, keycode 173 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

I just wanted to post this so it'd be floating around the internet for someone else to hopefully find before they go crazy like I was.

Also, I found something that might help parse the keycodes if you're trying to grab multiple buttons (forgot where I found it, sorry I can't link to it)

```
 xev | sed -n 's/^.*keycode *\([0-9]\+\).*$/keycode \1 = /p' | uniq
```

**NOTE:**  If you hold down shift to get your buttons working, it will show up as keycode 50 (at least it does on my computer, so disregard that code)

---

### Post by kubaz on 2009-06-12
Fascinating! Thanks a lot. You probably saved me few hours of trying and googling :).

---

