---
title: "Pandora dependency errors"
date: 2010-09-15
forum: Multimedia Software
---

### Post by Speedwagon on 2010-09-15
I don't know what I did, but I did something recently, as Pandora keeps getting dependency errors.  Pandora is working just fine, but if I open the Software Center, it tells me it needs to fix itself before it can do anything.  If I do this, Pandora gets removed.  And I have an error box next to the Pandora icon on the upper right bar, telling me

> An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error: BrockenCount>0' This usually means that your installed packages have unmet dependencies

And this is on a 64bit Maverick install, though it was doing the same on the 64bit Lucid install(I just did the Maverick beta upgrade today).

Also, in a terminal:
```
-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kdesudo update-manager-kde
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  com.pandora.desktop.fb9956fd96e03239939108614098ad95535ee674.1
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,114kB disk space will be freed.
Do you want to continue [Y/n]? 

```

I use Pandora desktop app, so I don't want to remove it.  But I don't have any idea what the problem here is.

---

### Post by Speedwagon on 2010-09-17
Anyone?  I can't use the Software Center without it removing Pandora, and I find that very much annoying.

---

### Post by sikander3786 on 2010-09-17
Try,

```

sudo dpkg --configure -a

```

If even that doesn't help, probably you should file a bug report at launchpad.

---

