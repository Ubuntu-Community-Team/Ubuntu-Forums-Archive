---
title: "[SOLVED] Shortcut keyboard buttons"
date: 2008-08-23
forum: Multimedia Software
---

### Post by barkerben on 2008-08-23
Hi - I am using a MS desktop elite keyboard with various shortcut keys. If I go to system--->preferences--->keyboard shortcuts, most (lthough not all) of these keys generate a keycode when pressed - for example, the Play/pause button generates 0xa2. However, none of the media players I have tried pick up on the keyboard mappings defined through this GUI. 

To fix, I tried using xkeybinding coupled with xte so that each time I pressed, for example, the play/pause media button, a space bar keycode was generated to pause/play the video.

However, xkeybindings did not recognise the keycode 0xa2. When I checked usigng xev, for a standard key I would get:

KeyPress event, serial 31, synthetic NO, window 0x4e00001,
    root 0x1a6, subw 0x0, time 24978946, (153,486), root:(1578,546),
    state 0x0, keycode 41 (keysym 0x66, f), same_screen YES,
    XLookupString gives 1 bytes: (66) "f"
    XmbLookupString gives 1 bytes: (66) "f"
    XFilterEvent returns: False

But for the media keys I would get something like:

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  109 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

No keycode...likewise if I use xbindkeys -k it does not see the media keys at all...


Cheers,

ben

---

### Post by barkerben on 2008-08-24
I think I have solved it :-) I found that using the graphical keyboard shortcuts utility in Ubuntu (system -->preferences-->keyboard shortcuts) prevented anything else from using those keys, while also not doing anything useful with them! I unmapped them from there, and then was able to use xbindkeys -mk to identify the keycodes, and assigne them to the commands I wanted using xte using the following config file:

"xte 'key space'"
	m:0x0 + c:162

"xte 'key Left'"
	m:0x0 + c:144

"xte 'key Right'"
	 m:0x0 + c:153

"me-tv"
	m:0x48 + c:64 + m:0x40 + c:115 + m:0x0 + c:36
"xine"
   m:0x0 + c:129

---

