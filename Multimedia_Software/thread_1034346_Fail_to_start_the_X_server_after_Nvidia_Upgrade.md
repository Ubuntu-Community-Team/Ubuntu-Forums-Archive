---
title: "Fail to start the X server after Nvidia Upgrade"
date: 2009-01-08
forum: Multimedia Software
---

### Post by anxiousdog on 2009-01-08
Yesterday I did a quick upgrade to one of my Nvidia drivers when the update came through Update Manager. I didn't see any problems until after I rebooted and I got this message:

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would youy like to view the X Server output to diagnose the problem?

Here is the X server output:

> (EE) Failed to load module "type1" (module does not exist, 0) dlopen: /usr/lib/xorg/modules//libglx.so: cannot open shared object file: No such file or directory
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)


I searched around and didn't find anything recent to this but someone did say that you could make a symbolic link that could correct this. I'm not sure what to do without breaking things further.

---

### Post by anxiousdog on 2009-01-08
On further investigation, I went to the folder and saw the file that was throwing the error: /usr/lib/xorg/modules/libgls.so and it is already a symbolic link to /usr/lib/xorg/modules/extensions/libglx.so.177.80

When I go to /usr/lib/xorg/modules/extensions/ there is no file called libglx.so.177.80

I guess I will run a search on my computer and see where that file is...

---

### Post by Tekmoor on 2009-01-09
I've been unable to use the Nvidia drivers since the update as well. I've tried uninstalling/reinstalling an older version but could still not get it fixed.
Does anyone know what's going on?

---

