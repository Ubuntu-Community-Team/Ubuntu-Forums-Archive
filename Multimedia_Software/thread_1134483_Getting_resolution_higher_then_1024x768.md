---
title: "Getting resolution higher then 1024x768"
date: 2009-04-23
forum: Multimedia Software
---

### Post by Flip101 on 2009-04-23
As the title describes, my question is how to get the resolution higher. Right now the max is 1024x768 @ 100 Hz. Before ubuntu i had windows XP and the same computer, same monitor and i could go 1280x960 and even higher.
My driver is the default one that comes with 9.04 (since i didn't install any other driver). I have a Club 3D ATI x1650 Pro videocard.

I like the driver that is enabled now because it's fast and my OS is stable. I used to have problems with drivers either it was very slow or i couldn't play video or another problem. So i don't really like to try another driver, but i will if it's needed to fix my problem.

If anyone can help would be great, thx!

---

### Post by sa31fh on 2009-04-23
Try this:

If say you want a resolution of 1280x1024 @75 Hz. Open a terminal and type:

cvt 1280 786 75

This will give you the modeline. After that type:

xrandr --newmode MODELINE

Here, replace MODELINE with the output you got from the cvt command after 'Modeline'. Next time you login or reboot you should have the new option in your Display settings.

---

### Post by Flip101 on 2009-04-23
Thank you for your swift reply!

How do i make sure the modes added are compatible with my videocard and monitor? Suppose i add a mode that is not compatible, will this cause trouble? how can i remove this mode?

---

### Post by sa31fh on 2009-04-23
I usually just experiment till I get it right :). But you can check here : [https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions")

For deleting a mode, I'm not completely sure but this should work I think:
Command:  xrandr --delmode <output> <name>
Example: xrandr --delmode VGA 1280x1024

---

### Post by Flip101 on 2009-04-23
After logging in and out i didn't see the new mode.
When i did the command again this was the command and it's output:

```
xrandr --newmode "1280x786_75.00"  104.50  1280 1360 1488 1696  786 789 799 823 -hsync +vsync

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  23
  Current serial number in output stream:  23
```

Also i read at the website you gave me i can change resolution by:
```
xrandr --output LVDS --mode 1024x768
```
But this didn't do anything either. I tried 800x600, 1280x960 and setting different rates too.

---

### Post by sa31fh on 2009-04-23
Did you check if the new mode is available in:   System >  Preferences > Display    ?
It *should *work since I've used a few times myself.

As for your second command, your output might be incorrect. Try VGA as the output. If you just type xrandr in your terminal, it should tell you the name of the output connected.

---

