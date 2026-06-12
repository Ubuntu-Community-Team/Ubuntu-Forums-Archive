---
title: "dual monitor problem"
date: 2014-02-25
forum: Multimedia Software
---

### Post by Sietse on 2014-02-25
Dear users, 

Today i have installed ubuntu 12.04 on my office computer. I have 2x iiyama b2403ws (res:1920x1200) monitor. When i boot it sees one monitor as an iiyama like it should, but the other monitor show up like an old crt monitor with a max resolution of 800x600.

XrandR output:

```
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1920x1080      59.9     60.1     60.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       75.0     59.9  
   1440x480       60.1  
   1280x1024      76.0     75.0     72.0     60.0  
   1280x720       60.0     59.9  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9     59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 connected 800x600+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+
```



Can someone explain to me what i can do about this?

Sincerely,

sietse85

---

### Post by Bucky Ball on 2014-02-25
Have you tried installing arandr and tweaking with it in a GUI? It's in the repositories. Fairly flexible and can fix some things.

---

### Post by Sietse on 2014-02-25
i have tried it with xrandr but i wouldnt let me get a new mode into the DVI-I-3 it would give an error message. What is the difference between xrandr and arandr?

---

### Post by Sietse on 2014-02-25
when i try to run arandr it gives me an error message
```

Traceback (most recent call last):
  File "/usr/bin/arandr", line 25, in <module>
    main()
  File "/usr/lib/pymodules/python2.7/screenlayout/gui.py", line 302, in main
    force_version=options.force_version
  File "/usr/lib/pymodules/python2.7/screenlayout/gui.py", line 141, in __init__
    self.widget = widget.ARandRWidget(display=randr_display, force_version=force_version)
  File "/usr/lib/pymodules/python2.7/screenlayout/widget.py", line 32, in __init__
    self._xrandr = XRandR(display=display, force_version=force_version)
  File "/usr/lib/pymodules/python2.7/screenlayout/xrandr.py", line 26, in __init__
    raise Exception("XRandR 1.2/1.3 required.")
Exception: XRandR 1.2/1.3 required.

```

---

### Post by Bucky Ball on 2014-02-25
```
Exception("XRandR 1.2/1.3 required.")
Exception: XRandR 1.2/1.3 required.
```

Odd. What version of xrandr have you?

---

### Post by Sietse on 2014-02-25
```
xrandr program version       1.4.0
Server reports RandR version 1.4

```

Als nvidia-settings doesnt save anything if i try to change some settings.

---

### Post by Sietse on 2014-02-25
Also when i try to add the mode manually with xrandr i get this:
```

 xrandr --addmode DVI-I-3 "1920x1200_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34

```

---

### Post by Bucky Ball on 2014-02-25
*Thread moved to **Multimedia & Video**.*

You might get more help here. Well, at least we know why arandr isn't launching.

As for nvidia-settings, have you tried launching it from a terminal with:
```

gksudo nvidia-settings
```

---

### Post by Sietse on 2014-02-25
yes, and as soon as i click apply the program closed with this error:
```

The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 1016 error_code 2 request_code 155 minor_code 25)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by Sietse on 2014-02-25
is there someway i can force the EDID of the correctly recognized monitor to apply on the 'not recognized' monitor? Since they are exactly the same?

---

### Post by Bucky Ball on 2014-02-25
I'm using xfce4 and not Unity, but let's go for something much simpler to start, although you may have tried it. Can you go to Settings>Display, just in Ubuntu, not the terminal or nvidia-settings, and attempt to tweak the monitors to mirror?

The info in post #9 didn't look great, though.

---

### Post by Sietse on 2014-02-25
Mirroring only gives the low 800x600 resolution option, its just so weird it will not recognize my monitor. Both are connected trough hdmi cable to the same GPU

---

### Post by Sietse on 2014-02-25
anyway thanks for the help, i think i need to seek the solution in why the 2nd monitor is not correctly recognized

---

