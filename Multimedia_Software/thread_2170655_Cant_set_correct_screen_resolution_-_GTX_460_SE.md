---
title: "Cant set correct screen resolution - GTX 460 SE"
date: 2013-08-27
forum: Multimedia Software
---

### Post by richoz27 on 2013-08-27
Ubuntu noob here. Just installed Ubuntu 12.04, had no screen initially but managed to update to the current nvidia drivers and now I can at least see something.

My problem is I cant set the resolution to 1920 x 1080. I have spent the last 6 hours trying numerous fixes including modifying the xorg.conf file, none of which have solved my problem.

I have a GTX 460 SE graphics card, DVI 1 has a VGA adapter going into the PC input of my TV (Hisense 55", 1080 HD). I have been running 1920x1080 in windows without issues, although it only seems to work via VGA not HDMI.

I would post the xorg.conf file but its been a bit butchered by me trying multiple fixes, Ubuntu doesnt seem to care if I delete this file anyway, I still get the same resolutions I dont want.

All I want to do is force Ubuntu to display this resolution (1980x1080) as I know my TV can do it, detect displays does nothing.

Really keen to give Ubuntu a go but this seemingly simple requirement is starting to turn me back to the dark side! Please help!

---

### Post by richoz27 on 2013-08-27
I have been trying to add a new mode using xrandr:

```
cvt 1920 1080 60
```

I then try to add the new mode using the info after "modeline":

```
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

Which then gives me the following error:

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  31
  Current serial number in output stream:  31

I suppose this means that some of the numbers I cut and paste from the modeline are not right?

Looks like if I can get this right I can then assign this mode to DVI-I-0 which looks to be the output im using on my card, which should then give me the resolution I need?

---

### Post by richoz27 on 2013-08-30
Is this the wrong forum?

Ive spent days trying to get the desired resolution, none of the "fixes" work. xorg.conf seems to do nothing at all, the resolutions always reverts to 1024x768 no matter what I do.

The best I can do is:

set the resolution to 1152x864 (monitor actually says 1152x870 when I click apply)

then:

```
xrandr --output DVI-I-0 --scale 1.667x1.25
```

This closely approximates 1920x1080.

On reboot it goes back to the default so I have to do this every time i boot up. Even setting the resolution to 1152x864 in the nvidia settings and then saving the xorg.conf, writes this info to the file but seems to completely ignore this on reboot and goes back to 1024x768.

I cant believe how difficult it is to SET THE RESOLUTION FFS. Surely im not the only one thats come across this problem??

---

### Post by QIII on 2013-08-30
Moved to Multimedia & Video.

Between that and a title change, let's see if we can get some better play.

Best wishes.

---

