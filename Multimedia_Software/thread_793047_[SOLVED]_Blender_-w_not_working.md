---
title: "[SOLVED] Blender -w not working"
date: 2008-05-13
forum: Multimedia Software
---

### Post by rolodoom on 2008-05-13
Blender can't open with (-w) or without(-W) border
```
$ blender -w
$ blender -W
```Actually, in my box the command blender -w to open the program  with border doen't work.

Any suggestions?? I have tried uninstall and install and it doesn't fixed it. I also has ubuntu hardy on another computer and has no problem there, so I think is something in the configuration files but don't know what.

---

### Post by rolodoom on 2008-05-14
Found the solution. The problem happens to be a compiz problem.

Solution:

[LIST=1]
[*]Install compizconfig-settings-manager
[*]Go to advanced desktop effects settings (System>Preferences)
[*]Go to Utility > Workarounds
[*]Disable Legacy fullscreen support.
[/LIST]
Cheers.

---

