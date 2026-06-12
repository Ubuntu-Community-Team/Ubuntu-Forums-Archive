---
title: "Cheapo mce remote"
date: 2009-01-19
forum: Mythbuntu
---

### Post by My Name on 2009-01-19
I seem to have a habbit of buying hardware that kinda works but not without some jiggery pockery.
So I have a cheap MCE remote that is a mouse aswell. I have read the mythtv wiki and it all makes sense. The problem I'm having is that if I press certain buttons the feedback from xve is > KeyPress event, serial 30, synthetic NO, window 0x3c00001,
    root 0x188, subw 0x0, time 3212726, (1144,338), root:(1149,392),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3c00001,
    root 0x188, subw 0x0, time 3212734, (1144,338), root:(1149,392),
    state 0x14, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (07) ""
    XmbLookupString gives 1 bytes: (07) ""
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3c00001,
    root 0x188, subw 0x0, time 3212790, (1144,338), root:(1149,392),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3c00001,
    root 0x188, subw 0x0, time 3212790, (1144,338), root:(1149,392),
    state 0x10, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

Does that mean control_L and g at the same time? or does it mean something completely different?

---

### Post by My Name on 2009-01-19
ah it means left control key and g at the same time

---

### Post by My Name on 2009-01-19
OK now it seems that changing the key bindings in myth has no effect.
any ideas?

---

### Post by My Name on 2009-01-20
OK got it working to some extent. I was changing the key binding in the wrong section.
Another problem I'm having is that some of the buttons seem not to be keystrokes but something else. I'll post what they are tonight.
The main thing for me was to get the tv guide key to work, and that is working now.
Maybe I will buy a better remote...

---

