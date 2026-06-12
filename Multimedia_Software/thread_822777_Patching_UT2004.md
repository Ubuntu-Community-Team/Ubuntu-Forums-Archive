---
title: "Patching UT2004"
date: 2008-06-08
forum: Multimedia Software
---

### Post by Mecharuva on 2008-06-08
I'm guessing 'games' falls under multimedia?
Move me if I'm wrong x.x
Anyhoo, I just recently installed Unreal Tournament 2004 via the 5CD pack (borrowed from friends).
Now I've got the v3355 patch (is that even the latest?) and I have no clue how to update UT2004 with it.
The patch (.tar.bz2 file) is sitting in my /home/mecharuva directory.
Any help?

---

### Post by Mecharuva on 2008-06-09
Bump D:

---

### Post by prshah on 2008-06-10
> **Mecharuva said:**
> 
Now I've got the v3355 patch (is that even the latest?) and I have no clue how to update UT2004 with it.
The patch (.tar.bz2 file) is sitting in my /home/mecharuva directory.
Any help?

3355, (released in Feb 06), does look like the last patch released.

Install the game and start it once (then close it) before installing the patch. 

Then open a terminal (Applications-Accessories-Terminal), then give the following commands ```
cd
tar -xvf --bzip2 patch.tar.bz2
sudo cp -r UT2004-Patch/* /usr/local/games/ut2004/
rm -rf UT2004-Patch

```

(Replace the name "patch.tar.bz2" with the actual name: I think it must be (usually) ut2004-lnxpatch3355, but depends on where you've downloaded it from.)

In case of errors, post back.

---

