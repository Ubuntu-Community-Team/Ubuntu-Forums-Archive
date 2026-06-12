---
title: "refresh rate for monitor is too high in X according to manual.  set at 85Hz need 76Hz"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by TOPPEL on 2006-06-14
refresh rate for monitor is too high in X according to manual.  set at 85Hz need 76Hz

using Ubuntu Dapper Drake.  resolution is 1280x1024.  wont let me set higher.  thats ok -- but need to get the refresh rate down to 76 according to the manual i have in PDF form.  its a Sun GDM-5410.  

thank you

:confused:

---

### Post by TOPPEL on 2006-06-14
[QUOTE=TOPPEL]refresh rate for monitor is too high in X according to manual.  set at 85Hz need 76Hz

using Ubuntu Dapper Drake.  resolution is 1280x1024.  wont let me set higher.  thats ok -- but need to get the refresh rate down to 76 according to the manual i have in PDF form.  its a Sun GDM-5410.  

thank you

:confused:[/QUOTE]

i'm using nvidia-glx driver.  

thanks. .  (same poster)

---

### Post by taurus on 2006-06-14
Can you edit your /etc/X11/xorg.conf (from a terminal, Applications -> Accessories -> Terminal)
```

sudo gedit /etc/X11/xorg.conf

```
or you can configure your X again by running (from a terminal again)
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by TOPPEL on 2006-06-14
[QUOTE=taurus]Can you edit your /etc/X11/xorg.conf (from a terminal, Applications -> Accessories -> Terminal)
```

sudo gedit /etc/X11/xorg.conf

```
or you can configure your X again by running (from a terminal again)
```

sudo dpkg-reconfigure xserver-xorg

```[/QUOTE]
what do i change ?  i saw no reference to 85Hz in xorg.conf.  i dont know what to change :(

---

### Post by taurus on 2006-06-14
Do the horizontal and vertical refreshing rates correct (HorizSync & VertRefresh) in the Monitor section?  Otherwise, you can always configure your X again with 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak <-- make a backup copy just in case you need to use it later...
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by TOPPEL on 2006-06-14
i was able to enter the two essential parameters.  i still was not able to lower the refresh rate.  oh, well.  hopefully its ok to run at this Hz.

---

### Post by taurus on 2006-06-14
Have you tried the method, reconfiguring your X over again, from above?
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg

```
You can run it at a higher frequency but you have to be careful because if you have one of those cheap monitors, it will smoke eventually...

---

### Post by TOPPEL on 2006-06-15
that i did not do.  would i be able to get a lower refresh rate that way ?   i have tried that reconfigure xorg by the command line once and failed.

---

### Post by longlegs on 2007-06-26
Hi ,
I'm a newbie too but had similar problem. The resolution I had was 1600xXXX
The solution is the same for resolution too low OR too high. You need to edit the xorg.conf file.
CAUTION MAKE NO TYPO"S. I can't tell you how to recover if xorg.conf is corrupted.
open a terminal. In Feisty you click on accessories=>terminal
at the prompt, type sudo gedit /etc/X11/xorg.conf
thats a capital X one one
press enter then enter your password. The text editor 'gedit' will open the xorg.conf for editing.
You will look for a series of line similar to these
================================================== ==
Section "Monitor"
Identifier "PF790-2"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc 3D Rage Pro AGP 1X/2X"
Monitor "PF790-2"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

================================================== ========
the resolutions that you will have in System=>preferences=>screen resolution depend on the
resolutions in these lines. NOTE the I placed my desired default resolution first, and the others afterward. This causes my login screen to be the same as my working resolution. Enter the resolution choices that you want, in every line, TRIPLE CHECK that you have made no other changes.
Now look at the "Screen" section. you should change the sync and refresh rates to what your monitor and video card will support but not greater. In my case 60 is the max refresh rate.

When you are done, save the changes, overwriting the original.
reboot. CHeck system=>preferences=>resolution to verify that this fixes your problem.

Good luck,
longlegs
__________________

---

