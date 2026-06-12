---
title: "Can't change song in Rhythmbox with mouse wheel"
date: 2010-05-08
forum: Multimedia Software
---

### Post by SpaceBison on 2010-05-08
Upgraded to 10.04, fresh install. Now I can't change to a new song or go back to the previous one by using the mouse wheel over the rhythmbox icon in the task bar like I could in the previous release. I couldn't find an option for it in the plugins or preferences neither. Is there a way to get this back?

---

### Post by tgalati4 on 2010-05-08
Does the mousewheel scroll in firefox and other apps?

Open a terminal and run xev.

Post the output of scroll events.

Did you check your gnome keyboard shortcuts?

---

### Post by SpaceBison on 2010-05-08
Yes the mouse wheel works fine otherwise, I can use it to change the volume by hovering over the speaker icon in the taskbar and scrolling. As for rhthymbox I believe it was an option in the status bar plugin but I don't see it in there anymore.

> matt@cactus:~$ xev
Outer window is 0x4e00001, inner window is 0x4e00002

PropertyNotify event, serial 8, synthetic NO, window 0x4e00001,
    atom 0x27 (WM_NAME), time 13536363, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x4e00001,
    atom 0x22 (WM_COMMAND), time 13536363, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x4e00001,
    atom 0x28 (WM_NORMAL_HINTS), time 13536363, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x4e00001,
    parent 0x4e00001, window 0x4e00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x4e00001,
    atom 0x132 (WM_PROTOCOLS), time 13536364, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x4e00001,
    event 0x4e00001, window 0x4e00002, override NO

PropertyNotify event, serial 20, synthetic NO, window 0x4e00001,
    atom 0x183 (_NET_WM_ALLOWED_ACTIONS), time 13536365, state PropertyNewValue

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x1ca (_NET_FRAME_WINDOW), time 13536366, state PropertyNewValue

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x183 (_NET_WM_ALLOWED_ACTIONS), time 13536366, state PropertyNewValue

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x137 (_NET_FRAME_EXTENTS), time 13536366, state PropertyNewValue

ConfigureNotify event, serial 22, synthetic NO, window 0x4e00001,
    event 0x4e00001, window 0x4e00001, (1,51), width 178, height 178,
    border_width 2, above 0x20270ee, override NO

ConfigureNotify event, serial 22, synthetic NO, window 0x4e00001,
    event 0x4e00001, window 0x4e00001, (1,51), width 178, height 178,
    border_width 2, above 0x420b0e9, override NO

MapNotify event, serial 22, synthetic NO, window 0x4e00001,
    event 0x4e00001, window 0x4e00001, override NO

VisibilityNotify event, serial 22, synthetic NO, window 0x4e00001,
    state VisibilityUnobscured

Expose event, serial 22, synthetic NO, window 0x4e00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 22, synthetic NO, window 0x4e00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 22, synthetic NO, window 0x4e00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 22, synthetic NO, window 0x4e00001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x140 (_NET_WM_STATE), time 13536366, state PropertyNewValue

FocusIn event, serial 22, synthetic NO, window 0x4e00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 22, synthetic NO, window 0x0,
    keys:  4294967228 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x13a (_NET_WM_DESKTOP), time 13536366, state PropertyNewValue

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x158 (WM_STATE), time 13536368, state PropertyNewValue

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x1a0 (XKLAVIER_STATE), time 13536371, state PropertyNewValue

PropertyNotify event, serial 22, synthetic NO, window 0x4e00001,
    atom 0x1e3 (_COMPIZ_WINDOW_DECOR), time 13536417, state PropertyNewValue

PropertyNotify event, serial 31, synthetic NO, window 0x4e00001,
    atom 0x1e7 (_COMPIZ_WM_WINDOW_BLUR_DECOR), time 13536439, state PropertyNewValue

PropertyNotify event, serial 31, synthetic NO, window 0x4e00001,
    atom 0x179 (_NET_WM_ICON_GEOMETRY), time 13536439, state PropertyNewValue

FocusOut event, serial 33, synthetic NO, window 0x4e00001,
    mode NotifyNormal, detail NotifyNonlinear


---

### Post by tgalati4 on 2010-05-09
ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142284324, (97,118 ) , root: (1295,145),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142284324, (97,118 ) , root: (1295,145),
    state 0x1000, button 5, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142284574, (97,118 ) , root: (1295,145),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142284574, (97,118 ) , root: (1295,145),
    state 0x1000, button 5, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142292869, (97,118 ) , root: (1295,145),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142292869, (97,118 ) , root: (1295,145),
    state 0x800, button 4, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142292930, (97,118 ) , root: (1295,145),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142292930, (97,118 ) , root: (1295,145),
    state 0x800, button 4, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142292962, (97,118 ) , root: (1295,145),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142292962, (97,118 ) , root: (1295,145),
    state 0x800, button 4, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293001, (97,118 ) , root: (1295,145),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293001, (97,118 ) , root: (1295,145),
    state 0x800, button 4, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293040, (97,118 ) , root: (1295,145),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293040, (97,118 ) , root: (1295,145),
    state 0x800, button 4, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293093, (97,118 ) , root: (1295,145),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293093, (97,118 ) , root: (1295,145),
    state 0x800, button 4, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293119, (97,118 ) , root: (1295,145),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3c00001,
    root 0x84, subw 0x0, time 142293119, (97,118 ) , root: (1295,145),
    state 0x800, button 4, same_screen YES

--------------------

When you open xev, put the cursor inside the xev box, then roll the scroll wheel up and down, then move the mouse back to the terminal and hit control-c.

On my thinkpad (which I use two-finger scroll to simulate a mousewheel, I get a "button 5 and button 4" Button Press and Release events.  I don't see any Button Press or Release events in the xev output that you provided.

I'm using Jaunty on this laptop with version 0.12 of rhythmbox, and I don't see either a preference or a plug-in for scroll wheel control.  Perhaps it was another music player?

---

### Post by SpaceBison on 2010-05-10
> **tgalati4 said:**
> 
I'm using Jaunty on this laptop with version 0.12 of rhythmbox, and I don't see either a preference or a plug-in for scroll wheel control.  Perhaps it was another music player?

On my desktop with Jaunty in rhythmbox 0.12.5 it's there, but it's not on my laptop with Lucid in rhythmbox 0.12.8. It seems it was removed, but I found an applet that runs in the taskbar that does more or less what I want, though it takes up a lot more room. Thanks.
[IMG]http://www.spacebison.com/files/rhythmboxstatus.png[/IMG]

---

### Post by lunatico on 2010-05-29
> **SpaceBison said:**
> ... but I found an applet that runs in the taskbar that does more or less what I want, though it takes up a lot more room....

Do you mean the indicator applet?

Yes it does take much more space... icon separation is bigger. Bigger than the notification area which looks terrible. I've been trying no to, but I'm getting so annoyed with all those silly changes they made....

---

### Post by lunatico on 2010-07-19
> **SpaceBison said:**
> ...but I found an applet that runs in the taskbar that does more or less what I want, though it takes up a lot more room....

Which applet are you referring to?

---

