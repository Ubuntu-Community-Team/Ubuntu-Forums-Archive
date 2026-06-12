---
title: "Video don't show with high screen size"
date: 2011-09-19
forum: Multimedia Software
---

### Post by avi9526 on 2011-09-19
I've got new bigger (not to much) display and also got a bug.
If system just started - all OK.
But after 20 min of work with OS I've got next problem: if video player window is maximized - no video. When I reduce window size - video appear. Or, I close some programs (Firefox, Thunderbird) and video can appear (or not).
First I think that is not enough RAM, but I have RAM 0,8..1,4 GB used from 2 GB.
What the problem? Resources? How to solve :confused:

---

### Post by _aleksandar_ on 2011-09-19
Post output of following commands:

```
xrandr -q
``````
lspci |grep VGA
``````
lspci -knn |grep -i vga -A 4
```

---

### Post by psrdotcom on 2011-09-19
which player you are using?

Try to change the video attributes in the player settings.

---

### Post by avi9526 on 2011-09-19
```
xrandr -q
Screen 0: minimum 320 x 200, current 3200 x 1200, maximum 3200 x 3200
DFP1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 546mm x 352mm
   1920x1200      60.0*+
   1152x648       60.0 +
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        60.0  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x1024+1920+176 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)

``````
lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600XT]
``````
lspci -knn |grep -i vga -A 4
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV630 [Radeon HD 2600XT] [1002:9588]
        Subsystem: PC Partner Limited Device [174b:e420]
        Kernel driver in use: fglrx_pci                                                                                                                                                       
        Kernel modules: fglrx, radeon                                                                                                                                                         
01:00.1 Audio device [0403]: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series] [1002:aa08]
```> **psrdotcom said:**
> which player you are using?

Try to change the video attributes in the player settings.
I have this problem in VLC, Totem, Banshee, SMPlayer (SMPlayer also causes to all screen became dark for 2 sec before play). If problem appear - all players except VLC and SMPlayer is crashing, VLC and SMPlayer just give no video.

---

### Post by _aleksandar_ on 2011-09-19
Try this. For VLC media player. Tools>Preferences>Video>Output>X11 Video output (XCB). Then restart VLC, and try to play movie in fulscreen mode. Don't run any other programs (such is firefox, and so on).

In the case that video isn't appear in fulscreen mode, don't turn off VLC but switch to Terminal (that is previously opened), and run following commands:

```
ps -e -orss=,args= | sort -b -k1,1n | pr -TW$COLUMNS
``````
top
```(Press q to stop running top command, and then paste here outputs of comands)

---

### Post by avi9526 on 2011-09-19
VLC with X11 (XCB) seems show video in full size even with firefox running, but video laging (not so visibly, but little annoying)
:-#

---

