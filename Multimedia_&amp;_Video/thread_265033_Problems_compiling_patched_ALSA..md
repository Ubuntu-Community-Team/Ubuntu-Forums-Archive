---
title: "Problems compiling patched ALSA."
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by marinosr on 2006-09-25
I have a Compaq V3000 with an nVidia chipset. There is a known bug with this configuration that causes no sound to come out of the headphone jack. 

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412)

I'm trying to apply the patch that is given in the above thread, but this is what I get as output:

```

root@ENIAC:/home/marinosr/Desktop/alsa-driver-1.0.12# ./hda-generic-hp-fix.diff
diff: 63e58b008259: No such file or directory
./hda-generic-hp-fix.diff: line 2: ---: command not found
./hda-generic-hp-fix.diff: line 3: +++: command not found
./hda-generic-hp-fix.diff: line 4: @@: command not found
./hda-generic-hp-fix.diff: line 5: syntax error near unexpected token `}'
./hda-generic-hp-fix.diff: line 5: ` };'

```

Regardless of this, I went ahead and compiled ALSA. I told ./configure to use hda-intel as the driver. Now the sound works fine, except the same problem of no headphone output. I've never patched anything with a diff file, and I know very little about what's supposed to happen. Any help would be greatly appreciated.

---

### Post by marinosr on 2006-09-25
Testing... my thread's not showing up.

---

