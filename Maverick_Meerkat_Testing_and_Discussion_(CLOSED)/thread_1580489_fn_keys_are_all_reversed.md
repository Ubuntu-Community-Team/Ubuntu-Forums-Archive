---
title: "fn keys are all reversed"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2010-09-23
I'm testing the latest daily netbook edition image on my HP Mini 210 and I noticed the fn keys are all reversed. For example, to use F10 I would press fn+Volume Up, but in Maverick when I press only the Volume Up key, it sends F10, and in order to increase the volume I need to use fn+Volume Up. All of the other fn keys all work in this same reversed fashion. This is completely backwards from how it should work. It works as expected in Lucid.

---

### Post by cariboo on 2010-09-23
That sounds strange, I have a Compaq Mini 110, to turn volume up I press Fn F10/Volume up and to turn it down Fn F11/Volume down, all my function key work that way.

One strange thing I just noticed, If I press Fn F6/Lock, I get numbers on the icons in the panel, and by pressing the corresponding number, that application opens up.

---

### Post by ljrmorgan on 2010-09-23
> **FuturePilot said:**
> I'm testing the latest daily netbook edition image on my HP Mini 210 and I noticed the fn keys are all reversed. For example, to use F10 I would press fn+Volume Up, but in Maverick when I press only the Volume Up key, it sends F10, and in order to increase the volume I need to use fn+Volume Up. All of the other fn keys all work in this same reversed fashion. This is completely backwards from how it should work. It works as expected in Lucid.

I have the same netbook and do not have this problem. I know there's an option in the BIOS to change the default behaviour to the behaviour you describe, but I guess you didn't accidentally change that!

Try going to System > Prefs > Keyboard shortcuts and make sure volume up is bound to XF86AudioRaiseVolume (or whatever) and not F10. I'm guessing that wont be the problem though - I'm not sure if there is a way of asking your computer if it thinks the function key is on. It might not do, it may just have the wrong keyboard layout or something.

---

### Post by FuturePilot on 2010-09-23
> **ljrmorgan said:**
> I have the same netbook and do not have this problem. I know there's an option in the BIOS to change the default behaviour to the behaviour you describe, but I guess you didn't accidentally change that!

Try going to System > Prefs > Keyboard shortcuts and make sure volume up is bound to XF86AudioRaiseVolume (or whatever) and not F10. I'm guessing that wont be the problem though - I'm not sure if there is a way of asking your computer if it thinks the function key is on. It might not do, it may just have the wrong keyboard layout or something.

All of the shortcut settings are currently set to XF86$FUNCTION. In order to get them to function the correct way I would have to set them to the F keys. In Lucid they work fine as XF86$FUNCTION. Yeah, I haven't changed any settings in the BIOS. I'll have to check the keyboard layout.

---

### Post by FuturePilot on 2010-09-25
Well I check the keyboard layout and it is identical to how it is in Lucid. I double checked the BIOS and it was set correct. I even changed it on the chance that it would reverse the reversed keys but it didn't make a difference.

---

