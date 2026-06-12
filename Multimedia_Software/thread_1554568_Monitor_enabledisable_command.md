---
title: "Monitor enable/disable command"
date: 2010-08-16
forum: Multimedia Software
---

### Post by Fender89 on 2010-08-16
I need to find out a command to enable and disable a secondary monitor using the Nvidia X Server. I've got a monitor attached to my laptop that I don't use all the time and would like to just have a launcher to switch between "twinview" and "disabled" quickly rather than having to go through the menus. It's physical position is vertically above the primary monitor so I have to put in a custom position every time I enable it.

---

### Post by realzippy on 2010-08-17
this should be possible with *xrandr*.
Both monitors running,open a terminal,type:

```
xrandr
```

and post the output please..

---

### Post by Fender89 on 2010-08-17
This is with the additional screen attached:
```
Screen 0: minimum 320 x 175, current 1920 x 1980, maximum 1920 x 1980
default connected 1920x1980+0+0 0mm x 0mm
   1440x900       50.0    119.0  
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0     55.0     56.0     57.0     58.0  
   960x600        59.0  
   960x540        60.0  
   840x525        61.0     62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0     72.0     73.0  
   800x512        74.0  
   720x450        75.0  
   720x400        76.0  
   700x525        77.0     78.0     79.0     80.0  
   680x384        81.0     82.0  
   640x512        83.0     84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0     91.0  
   640x400        92.0  
   640x350        93.0  
   576x432        94.0     95.0     96.0     97.0     98.0     99.0    100.0  
   512x384       101.0    102.0    103.0    104.0    105.0  
   416x312       106.0  
   400x300       107.0    108.0    109.0    110.0    111.0  
   360x200       112.0  
   320x240       113.0    114.0    115.0    116.0  
   320x200       117.0  
   320x175       118.0  
   1920x1980     119.0* 
```

and when I disable that monitor, running just with the laptop display:
```
Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1920 x 1980
default connected 1440x900+0+0 0mm x 0mm

```

---

### Post by realzippy on 2010-08-17
Let's make a test:
With both monitors running,open a terminal and run:

```
xrandr --output default --mode 1440x900
```


if this should work,try "starting" 2nd monitor with:

```
xrandr --output default --mode 1920x1980
```


if both commands should work,you could create a starter on the Desktop
with those commands..

Will be offline about 4 hours....

---

### Post by Fender89 on 2010-08-17
> **realzippy said:**
> Let's make a test:
With both monitors running,open a terminal and run:

```
xrandr --output default --mode 1440x900
```


if this should work,try "starting" 2nd monitor with:

```
xrandr --output default --mode 1920x1980
```


if both commands should work,you could create a starter on the Desktop
with those commands..

Will be offline about 4 hours....

Unfortunately not. When I ran the first script nothing changed visually but I had an "invisible box" on my larger 1920x1080 monitor, where I couldn't move my pointer outside of an area which I assume was 1440x900 in size. When I ran the second one, it set it back to normal.

---

### Post by aeiah on 2010-08-17
you can use nvidia-settings from the command line

you can load a config file, or issue commands one after the other as if you're using it normally with the gui. when you've got the right series of commands just put them in a script and trigger it with a menu button or something.

```

man nvidia-settings

```

---

### Post by realzippy on 2010-08-17
> **aeiah said:**
> you can use nvidia-settings from the command line

you can load a config file, or issue commands one after the other as if you're using it normally with the gui. when you've got the right series of commands just put them in a script and trigger it with a menu button or something.

```

man nvidia-settings

```

@aeiah:

AFAIK the xinerama settings are set up in the *xorg.conf* file and **not**
in the *.nvidia-settings-rc*,so a X restart would be required to switch...not exactly what OP wants.Could you be more specific concerning to the "commands" which turn on/off 2nd monitor in nvidia-settings?
Checked out the nvidia-settings manpages also before,cannot find anything to switch monitors.

-----------

Read somewhere that xrandr conflicts with xinerama,so my first idea cannot work.
But it might be worth testing to disable xinerama and set up
the dualview with xrandr....


Edit:
Or do you use "Twinview" ?Can you post your xorg.conf file?


Edit2:

There is a program "[disper]("http://willem.engen.nl/projects/disper/")" which might do what you want.

---

### Post by Fender89 on 2010-08-17
> **realzippy said:**
> @aeiah:

There is a program "[disper]("http://willem.engen.nl/projects/disper/")" which might do what you want.

This works beautifully,thank you so much.

---

### Post by realzippy on 2010-08-18
Yes,I also installed it,works here for casual plugged old beamer,no
more manual setup.Thanks for the idea,and set thread as "solved" (Threadtools) please...

---

