---
title: "Link TV and PC through s-video"
date: 2013-12-09
forum: Multimedia Software
---

### Post by e.stipcakova on 2013-12-09
[COLOR=#333333][FONT=UbuntuRegular]I installed Ubuntu 13.10 and I have problem with TV connection. Graphic card is Radeon X1300/X1550 Series. When I plug in TV and type xrandr:[/FONT][/COLOR]
    ```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
DVI-1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 257mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1 
``` 
[COLOR=#333333][FONT=UbuntuRegular]I tried this - [https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI), section TV-out. But when I type last command[/FONT][/COLOR]
```
xrandr --output S-video --mode 800x600
```
[COLOR=#333333][FONT=UbuntuRegular]-> At this point you should see a 800x600 version of your desktop on your TV.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]There is nothing on TV and monitor turns black.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]File xong.conf is empty, I tried to generate it (sudo Xorg -configure), but:[/FONT][/COLOR]
```
(EE) 
Fatal server error:
(EE) Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) 
```
[COLOR=#333333][FONT=UbuntuRegular]Could anyone please help me? (Sorry for my English, I'm not native speaker)
The connection worked before in windows, so there shouldn't be a problem.[/FONT][/COLOR]

---

