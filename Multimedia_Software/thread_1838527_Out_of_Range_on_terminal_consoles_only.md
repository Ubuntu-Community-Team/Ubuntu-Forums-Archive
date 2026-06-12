---
title: "Out of Range on terminal consoles only"
date: 2011-09-03
forum: Multimedia Software
---

### Post by mdmcginn on 2011-09-03
I was getting Out of Range on all consoles. I can now use GNOME/Unity in Desktop mode/Console 7 just fine, but I still get Out of Range in all the non-GUI command line/terminal consoles. 

```
OUT OF RANGE
VGA IN: 1024x768
H.SYNCH: 68.8 KHZ
V.SYNCH: 85.1 HZ
CLOCK: 114.0 MHZ
```

Shouldn't I be able to fix that problem with xandr? I tried typing ```
xrandr --output VGA1 --mode 800x600 --rate 60
``` in Console 7 and pressing Ctrl-Alt-F4 and blindly typing the same thing there.

When I do that in Console 7, the resolution changes, but nothing seemed to happen when I do that in the other consoles. So if I have any problems with Unity or Chrome freezing, I can't get to the command line to fix it. I can blindly press Ctl-Alt-Del in another console to reboot my computer, so there must be a terminal in there somewhere. I just can't see it.

Partial results of lspci:
```
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) (prog-if 00 [VGA controller])
```

Results of xrandr in a terminal on Desktop mode/Console 7 (Ctrl-Alt-F7):
```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1024x768       85.0 +   75.1     72.0     70.1     60.0  
   1280x1024      75.0     72.0     70.0     60.0  
   1280x960       60.0  
   832x624        74.6  
   800x600        72.2     75.0     70.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     70.0     60.0     59.9  
   720x400        70.1 
```

When I run ```
xrandr -s 0 
```in that terminal, I get the same Out of Range message as I still get on all the other consoles. What do I need to change so I can use Consoles 1 through 6?

Thanks.

---

### Post by kongr45gpen on 2011-10-27
Having the same issue here... Please provide a solution...

---

