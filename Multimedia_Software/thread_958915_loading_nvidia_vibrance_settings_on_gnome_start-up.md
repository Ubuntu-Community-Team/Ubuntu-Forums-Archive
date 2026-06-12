---
title: "loading nvidia vibrance settings on gnome start-up"
date: 2008-10-25
forum: Multimedia Software
---

### Post by dustint83 on 2008-10-25
i dont know if this is suppost to happen at startup or not, but it doesnt for me

the digital vibrance, antialiasing, and anisotropic filtering do not load on startup, to get the settings to take effect, i simply have to load the nvidia control panel and right away without clicking anything i can see the vibrance take effect on my wallpaper

in games, if i dont load the control panel first, antialising and AF are disabled completely

surely theres a way to load these settings at boot rather than having to open control panel everytime

any suggestions?

---

### Post by dustint83 on 2008-10-26
bump

---

### Post by dustint83 on 2008-10-26
bump again

---

### Post by dustint83 on 2008-10-26
bn6um6857m85787f

---

### Post by Agent ME on 2008-10-27
Press Alt-F2 *(or open a terminal)* and type
```
gksudo nvidia-settings
```
Set everything to how you want. Then press the "X Server Display Configuration" page on the left. Find the "Save to X Configuration File" button, and press it. It will bring up a little dialog box - press the Save button. Now everything you set will be applied by default.

There is a side-effect - whenever the computer is switching displays or stuff, instead of blanking the screen, it will show the Nvidia logo instead. Not really sure how to change that, but I kinda like that *(as opposed to having the screen blank and not knowing what my computer is doing)*.

---

### Post by dustint83 on 2008-10-27
> **Agent ME said:**
> Press Alt-F2 *(or open a terminal)* and type
```
gksudo nvidia-settings
```
Set everything to how you want. Then press the "X Server Display Configuration" page on the left. Find the "Save to X Configuration File" button, and press it. It will bring up a little dialog box - press the Save button. Now everything you set will be applied by default.

There is a side-effect - whenever the computer is switching displays or stuff, instead of blanking the screen, it will show the Nvidia logo instead. Not really sure how to change that, but I kinda like that *(as opposed to having the screen blank and not knowing what my computer is doing)*.


cant do that, i have twinview disabled to correctly report my refesh rate in gnome so that tab does not load

on another note, before i had disabled twin view, i already saved the config to file. that doesnt do anything more than back up your settings, it doesnt load anything on startup

thanks for your suggestion though

---

### Post by steveneddy on 2008-10-29
> **Agent ME said:**
> Press Alt-F2 *(or open a terminal)* and type
```
gksudo nvidia-settings
```Set everything to how you want. Then press the "X Server Display Configuration" page on the left. Find the "Save to X Configuration File" button, and press it. It will bring up a little dialog box - press the Save button. Now everything you set will be applied by default.

There is a side-effect - whenever the computer is switching displays or stuff, instead of blanking the screen, it will show the Nvidia logo instead. Not really sure how to change that, but I kinda like that *(as opposed to having the screen blank and not knowing what my computer is doing)*.

Perfect - thank you.

---

### Post by loomsen on 2008-10-29
> Not really sure how to change that

Add```

Option "NoLogo" "True"

```

to you device section in your xorg.conf (/etc/X11/xorg.conf)

Further, and more important, you don't need to run nvidia-settings as root if you have your xorg configured.
Settings done in the GUI, like digital vibrance, antialiasing, texture sharpening for instance, are not specified in your xorg.conf.

If you run nvidia-settings as normal user your settings will be saved to ~/.nvidia-settings-rc

Finally, add a startup entry to your session preferences (System-->Preferences-->Sessions)
```
nvidia-settings -l
```

This will just load your settings after login but not start the GUI.
(This is basically what you want after you set everything up to your liking)

So, after basic configuration of your xorg.conf, there's no further use for SUdoing things.

---

