---
title: "how to verify DVD burn?"
date: 2008-06-29
forum: Multimedia Software
---

### Post by starfry on 2008-06-29
Hopefully a simple question...

After burning an iso to a DVD, how do I verify it is correct ?

"cdrecord" (aka wodim) has no verify command that I can see.

I am having problems with reliability of DVD+R DL.

Thanks.

---

### Post by TenPlus1 on 2008-06-29
Brasero will let you burn an .iso image and verify it's checksum when complete...

---

### Post by starfry on 2008-06-29
My Brasero (native installed Hardy) says it has no plugins. What do I have to do to get that working?

Specifically, when I do "Burn Image" it says "the medium is not writeable with the current set of plugins"

This thread: [http://ubuntuforums.org/showthread.php?t=789022&highlight=medium+current+set+plugins](http://ubuntuforums.org/showthread.php?t=789022&highlight=medium+current+set+plugins)

implies that Brasero is broken for dual layer.

I generally feel more comfortable with the command line (closer to what is going on).

That said, if Brasero (or any other Gui) solves my problems...


**update** I downloaded that latest svn trunk of brasero but I can't compile it. It seems to be missing the "configure" command as described in the INSTALL file. Duh! **

---

