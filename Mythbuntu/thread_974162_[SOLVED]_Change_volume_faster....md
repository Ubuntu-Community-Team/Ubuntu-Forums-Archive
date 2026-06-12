---
title: "[SOLVED] Change volume faster...?"
date: 2008-11-07
forum: Mythbuntu
---

### Post by biggyfred on 2008-11-07
Changing the volume happens 2% at a time. I was wondering if anyone knows if it can be changed at a different rate, like 5% or 10% per button push. 

Thanks in advance.

---

### Post by bawilson2 on 2008-11-07
Is this with a remote?  I've been able to change it by modifying the lirc when using a remote.

---

### Post by biggyfred on 2008-11-07
> **bawilson2 said:**
> Is this with a remote?  I've been able to change it by modifying the lirc when using a remote.
I figured it would probably be easier to change it so the keyboard shortcut would do it and lirc would mimic, but lirc would work too. 

You just set it so every button push in lirc hit 3 times or something like that?

---

### Post by bawilson2 on 2008-11-07
I modified the repeat parameter in the lirc config file.  Mine looked something like this:

begin
    remote = mceusb
    prog = mythtv
    button = VolDown
    config = [
    repeat = 2
    delay = 0
end


Usually the repeat is set to zero.  If that's the case it will only accept one input from the button each time it is pressed.  If you increase the repeat it will accept every Xth input.  That way if you're holding down the button it will go much faster.  It isn't exactally what you're looking for but it is what I used to make the volume move much faster.  The delay is also helpful if you want to still allow for small adjustment.  It will ignore the first X repeats before using the repeat setting.

---

### Post by biggyfred on 2008-11-07
That's a lovely idea. Many thanks.

---

