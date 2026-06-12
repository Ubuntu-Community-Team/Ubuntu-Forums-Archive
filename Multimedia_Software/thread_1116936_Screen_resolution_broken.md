---
title: "Screen resolution broken"
date: 2009-04-05
forum: Multimedia Software
---

### Post by stromdal on 2009-04-05
After almost a year of functioning just fine, the screen resolution on my MythBuntu box broke last week. The box is hooked up to a 42" LCD TV with native resolution of 1920x1080, now all I get is 800x600 output from my box. Last time I encountered this kind of problem it turned out to be nothing wrong with the graphics card or driver. Rather, the graphics card and monitor doesn't communicate properly, so the graphics card can't get any information from the monitor about what kind of monitor it is, so it defaults to a low-res output. I fixed the problem by manually telling the graphics card the proper screen resolution by the command

```
gksudo displayconfig-gtk
```

This time, since it's a MythBuntu box (running on xfce, not Gnome), the command doesn't work. Is this right? SHOULD it work? I tried searching for displayconfig in Synaptic, but with no result. I set the "Screen" section of xorg.config to the following:

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor       "Configured Monitor"
    SubSection "Display":
        Modes      "1920x1080" "1280x800"
    EndSubSection
EndSection
```

The modes I entered doesn't show up when I run the "Display" option in the "Xfce Settings Manager", nor do they show up when I run "xrandr".

Any pointers? Should "displayconfig-gtk" work? Why don't I even get an error message when I run the command? Can I install some package to get displayconfig-gtk to work, or is it a part of Gnome itself? 

----

Some basic information:

```
~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

```
~$ uname -a
Linux Mythbuntu-Frontend 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
```

```
~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV28GL [Quadro4 980 XGL] (rev a1)
```

Please help! The low resolution and messed-up aspect ratio is killing me!

---

### Post by wolfen69 on 2009-04-05
run
```
sudo nvidia-settings
```
and try to set the resolution in **x server display configuration**. remember to **appl**y, then **save to x configuration file.** then reboot.

---

### Post by MykeBuntu on 2009-04-17
Just a wild guess (lord knows I'm no Myth guru) but did you recently update to the new Nvidia accelerated (v180 iirc) driver with Update Manager? That recently popped up for me-- but I stayed at v177. Is it possible it dropped back to the free driver to do the update? 

Do RightClick/System/Hardware Drivers to see what video driver you're using.

When I first tried Myth (v7.10) I spent MONTHS noodling with the video settings in the xorg file trying to get things working. But I haven't needed to touch it at all for v8.04 or v8.10.

Good luck

---

