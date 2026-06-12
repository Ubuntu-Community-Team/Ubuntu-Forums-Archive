---
title: "Mplayer GUI fullscreen with Twinview"
date: 2008-08-28
forum: Multimedia Software
---

### Post by ReksZ on 2008-08-28
I just installed 8.04.1 a few days ago, and I'm having a strange problem with Mplayer. I have an Nvidia 8500GT card with a Dell 19" CRT plugged into the VGA and a Samsung 22" LCD plugged into the DVI.

When I fullscreen Mplayer in the 19" monitor (which is at 1280x1024 resolution) fullscreen works great. However, when I fullscreen on the 22" monitor (which is at 1680x1050), the video is the same size as it would be on the 19" monitor, with black bars at the top and bottom, and a massive black bar to the side.

I already have the 22" monitor set as the primary display for the X screen under the Nvidia options screen. I have used the command line version of mplayer to fullscreen the video at the right resolution by specifying it with the screenh and screenw options, but then it messes up the subtitles. So my question is this:

Does anyone know what the fields are (if they exist) in the gui.conf file to tell the gui version what the screen height and width are, or is there a command I can type in the mplayer.conf file to tell the command line version to accept the SSA or whatever subtitle formatting?

Or is there something I can change in xorg.conf to make it clear to all my programs that the 1680x1050 monitor is the one they're going to be fullscreen on?

---

### Post by Valk01 on 2008-09-18
subbing, because i have this exact same problem running two dissimilar widescreens. opposite though. chops off a bunch of video, which hides me subs.

---

### Post by SharkMachine on 2008-12-23
Try adjusting the xineramascreen option.

For example if you want to run mplayer on your secondary monitor
```
gmplayer -xineramascreen 1
```

If you want to make it default, add this line```
xineramascreen=1
```to your mplayer configuration file, which is in .mplayer folder in your home folder.

---

### Post by euxneks on 2009-03-19
Sorry to dredge up an old post, but thought I would clarify for someone else who comes across this.

I am using TwinView with NVidia, so basically xinerama, with output on my TV. This means that I was getting the similar problem of fullscreen video on the TV being the size of the larger dimension monitor - I could only see part of the video then.

In any case, the top of ~/.mplayer/config should look something like this:
```
# Write your default config options here!
xineramascreen=1

```
If you have a [gnome-mplayer] part, placing it after this will only affect gnome-mplayer, which is different from gmplayer.

Interestingly enough, it doesn't look like I need to specify this option if I just use "mplayer" instead of "gmplayer"

:???: :-k

---

### Post by vace117 on 2010-03-24
Setting *xineramascreen=0* was not sufficient for my setup. 

The video was of the correct size, but it was placed in the middle of the virtual desktop (surrounded by blackness), which once again made it cut off on the TV.

I also had to specify *fstype=none*. So my *.mplayer/config* looks like this:
```

monitoraspect=16:9
xineramascreen=0
fstype=none

```

Now everything works great!

---

