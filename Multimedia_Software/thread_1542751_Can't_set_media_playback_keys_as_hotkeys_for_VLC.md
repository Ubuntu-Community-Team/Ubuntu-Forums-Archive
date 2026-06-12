---
title: "Can't set media playback keys as hotkeys for VLC"
date: 2010-07-31
forum: Multimedia Software
---

### Post by Exp HP on 2010-07-31
I've seen a couple of unsolved topics on this while researching, but they're all old and I'm hoping somebody's found a solution by now.

My laptop has the following keys that I want to assign as global hotkeys to VLC Media Player so that I can use them for... well, for their intended purpose:
**Play/Pause** (aka XF86AudioPlay)
**Prev Track** (aka XF86AudioPrev)
**Next Track** (aka XF86AudioNext)
Wouldn't it be great if these keys actually worked in something besides Totem?

Unfortunately, when I press them during the input prompt for a hotkey in VLC, nothing occurs.  It does not realize I even pressed a key; it just continues to wait for me to press a key.

However, I can set a hotkey if I combine it with a modifier key, i.e. Shift.  So I can't set regular Play/Pause, but I can set Shift+Play/Pause.   This leads me to believe that another program is using the keys as global hotkeys, intercepting the keycodes before they get passed to VLC.

Yet I've closed every app and even tried logging out and back in to make sure.  No program is running that could be stealing these keys and using them as global hotkeys.  So why can't I use them in VLC?

---

### Post by Exp HP on 2010-07-31
Now I feel silly.  It's so obvious... why didn't I think of it before?

Our desktop **GNOME** is the culprit.  The media playback and volume keys can't be used in VLC because they're global hotkeys for GNOME.

Alright, here's what you do.

System>>Preferences>>Keyboard Shortcuts
Under Sound, clear the keys for "Play (or Play/Pause)", "Previous track", "Next track", and for that matter anything else that uses a key that you want to have in VLC.

These keys will now work when setting hotkeys in VLC.*  Problem solved.*

(strangely, the keys still work in Totem as well.  I guess Totem picks up on both the keycodes and the GNOME functions)

---

### Post by BashOrgRu on 2010-10-22
Thank you so much :)

---

### Post by Azurea on 2010-10-28
Thanks a lot!, I was having the same problem. This was very useful

---

