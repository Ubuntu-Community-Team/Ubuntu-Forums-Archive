---
title: "Caps Lock functionality inverted?"
date: 2010-05-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-05-25
When the Caps Lock LED is lit, everything is lowercase. When not lit, everything is uppercase.

---

### Post by dino99 on 2010-05-25
check the 3rd level settings with keyboard

---

### Post by LKjell on 2010-05-25
Make sure that shift is not pressed down. Hit on both of them a few times.

---

### Post by Starks on 2010-05-25
> **dino99 said:**
> check the 3rd level settings with keyboard
```
eric@kingfisher:~$ xmodmap -pm
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

```

---

### Post by Starks on 2010-05-25
Also, here's xev...

```
KeyPress event, serial 33, synthetic NO, window 0x4000001,
    root 0xb1, subw 0x0, time 98854593, (476,-322), root:(479,369),
    state 0x0, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 34, synthetic NO, window 0x4000001,
    atom 0x14c (XKLAVIER_STATE), time 98854602, state PropertyNewValue

KeyRelease event, serial 36, synthetic NO, window 0x4000001,
    root 0xb1, subw 0x0, time 98854634, (476,-322), root:(479,369),
    state 0x2, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4000001,
    root 0xb1, subw 0x0, time 98855433, (445,-372), root:(448,319),
    state 0x2, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 36, synthetic NO, window 0x4000001,
    atom 0x14c (XKLAVIER_STATE), time 98855437, state PropertyNewValue

KeyRelease event, serial 36, synthetic NO, window 0x4000001,
    root 0xb1, subw 0x0, time 98855539, (445,-372), root:(448,319),
    state 0x2, keycode 66 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

