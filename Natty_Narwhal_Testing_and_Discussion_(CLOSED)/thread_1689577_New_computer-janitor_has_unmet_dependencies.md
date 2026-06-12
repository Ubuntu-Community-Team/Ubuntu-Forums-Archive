---
title: "New computer-janitor has unmet dependencies"
date: 2011-02-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-17
The newest version (2.1.0) cannot be installed.
Package computer-janitor-gtk depends on gir1.2-pango-2.0.
However that package does not exist in Natty.
Also the recent GTK introspection package gir1.2-gtk-2.0 depends on the recent gir1.2-pango-1.0.
Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/computer-janitor/+bug/720529](https://bugs.launchpad.net/ubuntu/+source/computer-janitor/+bug/720529)

---

### Post by dino99 on 2011-02-17
the good place for that package is , and always have been, trash box. Too buggy and useless as we have some other programs such gtkorphan and bleachbit which work fine and have much more power.

---

### Post by Harry33 on 2011-02-17
> **dino99 said:**
> the good place for that package is , and always have been, trash box. Too buggy and useless as we have some other programs such gtkorphan and bleachbit which work fine and have much more power.

This is also easy to do, because ubuntu-destop meta-package only recommends computer-janitor-gtk.
Then again, who needs meta-packages in the first place.):P

---

### Post by ikt on 2011-02-17
I don't see a problem :)

---

### Post by Harry33 on 2011-02-17
This bug has been fixed just a moment ago.
The version 2.1.0-0ubuntu2 works OK.

---

### Post by coffeecat on 2011-02-17
> **Harry33 said:**
> This bug has been fixed just a moment ago.

What a pity! :wink: I have to agree with the sentiments already expressed in this thread. When Synaptic informed me that it wanted to remove computer-janitor-gtk, I thought, "That's the best idea I've heard yet." :)

---

### Post by Harry33 on 2011-02-17
> **coffeecat said:**
> What a pity! :wink: I have to agree with the sentiments already expressed in this thread. When Synaptic informed me that it wanted to remove computer-janitor-gtk, I thought, "That's the best idea I've heard yet." :)

:p Ok, ok. ):P

---

### Post by NCLI on 2011-02-17
> **Harry33 said:**
> This is also easy to do, because ubuntu-destop meta-package only recommends computer-janitor-gtk.
Then again, who needs meta-packages in the first place.):P
I find the ubuntu-desktop metapackage very useful when restoring systems people have messed around with too much.

---

### Post by dino99 on 2011-02-17
> **NCLI said:**
> I find the ubuntu-desktop metapackage very useful when restoring systems people have messed around with too much.

yes, only for that case :(

---

### Post by Harry33 on 2011-02-17
> **NCLI said:**
> I find the ubuntu-desktop metapackage very useful when restoring systems people have messed around with too much.

This is a dev forum. Most of us have a decent knowledge about some linux basics.
Meta packages (IMHO) are for noobs only.
For any experienced user, who really wants to have a personalised system, and who likes to do some tweaks, do not want to be in the middle of dependency hell.

My systems or setups have never become messed up because I don't use meta packages (like xserver-xorg-input-all, xserver-xorg-video-all, ubuntu-minimal, ubuntu-standard, ubuntu-desktop, linux-headers-generic, linux-image, linux-image-generic, etc).

Of course it is useful to know what you are doing. I think anyone who wants to uninstall a package should first find out what that particular package does, why it is there.

One example here:
Xserver-xorg (a meta and documentation package) pulls in two meta packages:
xserver-xorg-input-all and xserver-xorg-video-all.
Those two meta-packages do nothing else than depend on more than twenty different input and video driver packages.
Now I do know very well what graphics card I have (NVidia). I do not need a single xserver-xorg-video driver in my system. All I need is the binary nvidia-current and of course its dependencies (like dkms).

---

### Post by cariboo on 2011-02-17
I on ther other hand think we should be using meta-packages during testing, as that is what most new users are going to install. I usually setup custom builds for specific purposes, but they never seem to last long, as I'm always moving on to something else.

---

### Post by Harry33 on 2011-02-17
> **cariboo907 said:**
> I on ther other hand think we should be using meta-packages during testing, as that is what most new users are going to install. I usually setup custom builds for specific purposes, but they never seem to last long, as I'm always moving on to something else.

Well, how can we test meta packages?
Right, there could be an erraneous dependency, but.
Then again, how can I test those twenty+ xserver-xorg-video drivers, when I only have one installed?

---

