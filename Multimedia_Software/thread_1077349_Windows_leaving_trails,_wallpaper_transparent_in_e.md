---
title: "Windows leaving trails, wallpaper transparent in expo/3d cube"
date: 2009-02-22
forum: Multimedia Software
---

### Post by Cayal on 2009-02-22
[COLOR="Silver"]I am having a very strange problem with my display just recently. With Compiz enabled, the space where my desktop would be is very glitchy; any movement on it, like window closing animations, moving widows and so on is "stamped" onto it, leaving a screen full of trails. After switching viewports which clears the trails, it seems the wallpaper is completely transparent, and I can see the cube through it, this effect is also apparent in Expo and when rotating the cube.

I tried disabling Compiz, though, and the glitch just formed itself as a huge black bar that takes up the bottom third of my screen, leaving only Docky and my GNOME panel visible. It's worth noting that since it last worked I:

&#8226;Tried to set a webcam as my wallpaper using the instructions found [here]("http://ubuntuforums.org/showthread.php?t=879897"), to no avail since my built-in webcam isn't recognized by Ubuntu
&#8226;Installed the Kubuntu-desktop package and booted into Kubuntu successfully
&#8226;Booted into windows to update my video driver using an installer from Intel's website

I've tried rebooting several times, which didn't work, and it doesn't seem like any of those things should be causing this. I'm using a Lenovo 3000 N200 with Intel GM965 integrated graphics.

[Here]("http://paste.ubuntu.com/121352/") are the contents of my Xorg.0.log and [this]("http://paste.ubuntu.com/121350/") is the output of "LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --sm-disable --ignore-desktop-hints ccp", which I already have pasted from searching for help on IRC.[/COLOR]


EDIT: The problem was conky being in my startup items, killing it restored things back to normal.

---

