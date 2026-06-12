---
title: "Gnome vs Xorg keyboard layout"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by 65 mustang on 2007-11-13
At startup i always received  a message 
> 
The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.
I interpreted this to mean.  Xorg thinks i have a 101 key keyboard and gnome thinks i have a 105 key keyboard.

I really do have a 105 key keyboard (101 does not have the windows (super) key).

So after much pain of adding one line of:
```

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
**    Option      "XkbModel" "pc105"**
EndSection

```
to my xorg.conf behold the same error.  X still thinks its a 101 key.  :(

So i back that change out and conclude the xorg.conf is not working correctly.

**Here is the real fix:**
In gnome go to system->preferences->keyboard and change the keyboard layout to 101 or whatever X thinks it is.  Bang! Fixed.  No more warnings at boot up.

Now here is the kicker.  In theory now Xorg and GNOME think i have a 101 key keyboard.  But the super keys still work!

I dont really have any issues anymore with this as a problem  But i am posting this as a possible bug.  Check over my logic on this.  I might be missing something.

Also note "the the" in the error message.

---

### Post by stuphi on 2007-11-14
Yay! I have been having this problem. I will try this out when I get home tonight. Thanks for the post.

---

### Post by Kingfield on 2007-12-19
but my keyboard is really a 105 T-T. And i have the exact same problem

---

