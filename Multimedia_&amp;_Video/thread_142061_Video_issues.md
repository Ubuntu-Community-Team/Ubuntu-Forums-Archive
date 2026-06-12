---
title: "Video issues"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by cabber on 2006-03-09
I have a GeForce 6600GT which has worked fine in the past.  I just recently re installed Ubuntu and all goes well until it starts loading into the splash screen.  I hear the music from the splash screen and my monitor shows all kinds of weird colors.  I cannot see anything except these jarbled colors. Is there something I can look at in the Recovery mode to assist with this issue?  I went in to recovery mode and was at the rootsystem and wasn't sure what commands to write.  Thanks.

---

### Post by Aine on 2006-03-09
hit ctrl+alt+f1 at the funky color screen.

Type 

```
sudo apt-get install nvidia-glx
```


Then do 


```
 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
 
sudo vim /etc/X11/xorg.conf

```
 
Look for the &#8220;Module&#8221; section and hit your insert key and make the following changes:

> 
#       Load    "GLcore"
#       Load    "dri" 
          Load "glx"


Then set the following

> 
Section "Device"
	Identifier- leave this line alone!
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection




When you're done hit escape, : then wq and hit enter.

Then do startx

---

