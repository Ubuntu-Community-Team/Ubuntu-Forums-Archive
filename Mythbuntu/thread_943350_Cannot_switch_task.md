---
title: "Cannot switch task?"
date: 2008-10-10
forum: Mythbuntu
---

### Post by singedwings on 2008-10-10
I am having the most annoyingly simple problem. When setting the backend up I need to switch task to the terminal, but alt-tab does nothing. I am using 8.10 beta.

Why? or how can I get round this?

---

### Post by SiHa on 2008-10-10
Alt + Tab will only switch between tasks already running, not start a fresh one, so if backend setup is the only app running, it will do nothing.

ALT+F2 should bring up a run dialog.
Enter```
xterm
``` to open the X terminal.

---

### Post by singedwings on 2008-10-10
See that is why I am having such a problem. Alt-tab appears not to work when I have other programs running eg firefox, and alt-F2 does not work for me either?!

---

### Post by newlinux on 2008-10-10
does alt+tab work when mythtv-setup is not running? Maybe for some reason your alt key isn't getting captured at all...

---

### Post by singedwings on 2008-10-10
No it does not appear to be working outside myth either. I don't know how to fix this.

---

### Post by newlinux on 2008-10-10
does alt anything work? Like keyboard shortcuts, or in most windows (like firefox) press Alt-F to get to file menu? What desktop environment are you using?

---

### Post by singedwings on 2008-10-10
No alt-f did not work in firefox. I am using mythbuntu 8.10 beta, so the desktop is sort of xfce.

---

### Post by newlinux on 2008-10-10
Maybe you chose the wrong keyboard type when installing. You might want to use ```
xev
``` and see what pressing the "alt" key generates. I think you can switch the keyboard type in xorg.conf. Not my area of expertise, you might want to ask this on the hardware part of the forum.

---

### Post by singedwings on 2008-10-10
When I installed I selected uk keyboard and I have a microsoft natural pro keyboard. Was this the wrong choice?

xev gives me:

FocusOut event, serial 34, synthetic NO, window 0x2600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x2600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   1   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x2600001,
    root 0x5e, subw 0x0, time 33307677, (324,341), root:(875,761),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

Sorry I don't know why a smiley appeared but it is really a : and a (

---

### Post by newlinux on 2008-10-10
```
...state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,...
```

Indicates you pressed the left Alt key so I think it is being interpreted fine... At this point I have no idea what problem is. Sorry... Hopefully some others will be along to help you.

---

### Post by SiHa on 2008-10-11
Just a thought. Does your keyboard have multifunctional(programmable) F-Keys? I've got a Logitech Cordless jobbie, and there's an F-Mode button that switches between standard and programmed mode for the F-keys. 

After boot, ALT+F2 works. Press the F-Mode key once, and ALT+F2 does nothing. It doesn't affect ALT-TAB, so may be completely unconnected, but as your 'ALT_L' key seems to be detected OK, it just occurred to me that it might not be the 'ALT' that's the problem...

---

### Post by singedwings on 2008-10-13
I have one of those keyboards attached to another computer, but the one I am having the problem with does not.

But, I have had a result, even though I was getting a positive response with xev I tried another keyboard, which works!

This now sounds like a bug to me should I post it?

---

