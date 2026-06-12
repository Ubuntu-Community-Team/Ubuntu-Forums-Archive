---
title: "upgrade to maverick went a little wrong &quot;penguintv&quot;"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2010-09-21
as it was finishing the upgrade with a few minutes to go, "penguintv" caused a problem. I clicked threw the warning and several more popped up about it and I finally got a message saying the system was left in an unstable state and the upgrade failed or something like that.

anyhow I rebooted and the kernel 2.6.35 generic refused to boot to the gui, but 2.6.32-24-generic did get me to the gnome desktop.
Screen refresh is way low, so I figure the nvidia video driver needs installing.
Something happened to the gedit menu item under accessories is missing.

A screen shot also shows some weird chars in the title

---

### Post by NightwishFan on 2010-09-21
Try running:
```
sudo apt-get update
```

Then:
```
sudo apt-get -f install
```

Then try the running update-manager -d from the ALT+F2 run dialogue again.

---

### Post by sdowney717 on 2010-09-21
> Reading package lists... Done
scott@scott-desktop:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@scott-desktop:~$ 


I reinstalled the latest nvidia driver and I can now get the desktop on the 2.6.35 kernel

BUT, I dont have any title header bar on any windows.(no window decoration)
Seen that before.

OK, logged out and in and window decorations are back.
Fonts look different, thinner more faded than I like. Wonder what I did on the prior version to improve them.

---

### Post by NightwishFan on 2010-09-21
Probably setting sub-pixel smoothing (for an lcd) and slight hinting. Works like a charm here.

Is everything working? As for Nvida, boot to 2.6.35 in recovery mode. Try the option to fix Xorg, if there is not one, then go to a root prompt and run:
```
jockey-text -d xorg:nvidia_current
```

---

