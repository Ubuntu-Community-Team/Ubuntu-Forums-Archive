---
title: "MCE Remote"
date: 2007-11-02
forum: Mythbuntu
---

### Post by besmith2@hotmail.com on 2007-11-02
I got an MCE remote with a USB receiver, it seems to work however it repeats commands to infinity and beyond making the system seem like it is locking up, I confirmed this by running irw. How do I stop this?

---

### Post by weiser on 2007-11-02
Hey,

Meybe you must look the your lircrc. there you can set repeat = 3

like:

begin
  prog = mythtv
# This is the Blue key
# Use it as a volume key
  button = Blue
  repeat = 3
  config = F11
end

---

