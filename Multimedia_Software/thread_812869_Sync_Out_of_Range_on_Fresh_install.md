---
title: "Sync Out of Range on Fresh install"
date: 2008-05-30
forum: Multimedia Software
---

### Post by Corrupter on 2008-05-30
Hey guys, I'm sorry that i dont know more about configuring the xorg.conf as it seems thats what i am supposed to do but let me explain my problem anyway and maybe you can help.

I have a Asus P5W-DH Motherboard holding 2 ATI Radeon 1800's atm, they dont need to be configured any special way as i use Linux on that machine for one video card use anyway, however i have a Compaq V710 monitor connected to it.  I installed the server edition of Ubuntu 8.04 and got it configured just how i like it... then released how nice it would be to have a desktop just in case i needed it so i apt-get install ubuntu-desktop

finishes fine, startx and i get sync out of range, rebooted, get sync out of range every time.  I'm sure someone knows where i went wrong... thoughts?

thankfully i can still SSH in, lastly what file do i configure to have the system boot to the CLI rather then the xdesktop, i'd prefer to be able to startx if i need the desktop.

thanks in advance.

---

### Post by Corrupter on 2008-05-31
bump

---

### Post by abhishekrane on 2008-05-31
Ok Maybe your resolution isn't working properly

```
sudo system-config-display --reconfig
```

If it doesn't work try without the reconfig flag 
Hope that works !

---

### Post by Corrupter on 2008-05-31
ok, going to do that, also someone told me this information is helpful...  

```

(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: CPQ  Model: 1382  Serial#: 1144336690
(II) RADEON(0): Year: 2000  Week: 24
(II) RADEON(0): Manufacturer: CPQ  Model: 1382  Serial#: 1144336690
(II) RADEON(0): Year: 2000  Week: 24
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.26
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) RADEON(0): blueX: 0.143 blueY: 0.062   whiteX: 0.281 whiteY: 0.311
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 65  vid: 17833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  306 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 85 kHz, PixClock max 170 MHz
(II) RADEON(0): Serial No: 024CG23SD512
(II) RADEON(0): Monitor name: COMPAQ V710
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff000e11821332313544
(II) RADEON(0):         180a01026820187eeabbb2a352469824
(II) RADEON(0):         0f484fa46380315945596159714fa945
(II) RADEON(0):         010101010101ea240060410028303060
(II) RADEON(0):         130032e61000001e000000fd0032a01e
(II) RADEON(0):         5511000a202020202020000000ff0030
(II) RADEON(0):         32344347323353443531320a000000fc
(II) RADEON(0):         00434f4d50415120563731300a200063
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "CPQ", prod id 4994

```

---

### Post by Corrupter on 2008-05-31
I know you are probably palming your face with me by now, im sorry... but heres what i got.

```
root@alter:/# vim /var/log/Xorg.0.log
root@alter:/# system-config-display --reconfig
-bash: system-config-display: command not found
root@alter:/# sudo system-config-display --reconfig
sudo: system-config-display: command not found
root@alter:/# system-config-display
-bash: system-config-display: command not found
root@alter:/# sudo system-config-display --reconfig
sudo: system-config-display: command not found
root@alter:/#

```

i tried without the sudo first cause im logged in as root..

also tried it with being a normal user same result.

---

### Post by abhishekrane on 2008-05-31
:( I didnt quite get that but have u tried the system-config thing? Does it work?

---

### Post by abhishekrane on 2008-05-31
Oh my mistake ubuntu does not havve system-config-display ...
try 
```
startx:0
```

i am lookin 4 it

---

### Post by abhishekrane on 2008-05-31
Ok there is a tool called displayconfig-gtk
try this
```
sudo apt-get install displayconfig-gtk
```

and run it

---

### Post by Corrupter on 2008-05-31
well when you install ubuntu-desktop it sets itself up to be ran automatically every time you reboot so i only have the ability to SSH in remotely and install things... if you could tell me how to prevent ubuntu-desktop from running at start-up the following error might not occur.

```
root@alter:/# displayconfig-gtk
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 71, in __init__
    gtk.init_check()
RuntimeError: could not open display

```

---

### Post by Corrupter on 2008-06-01
bump

---

### Post by Corrupter on 2008-06-02
ok, so i made a generic monitor with basic info about monitor and what it can handle, it allowed the desktop to load, however every time the desktop loads it brings up displayconfig-gtk and that gui doesnt save the changes i make.  Furthermore the desktop is then stuck in using 800x600 which isnt bad if i am just using the desktop for a few minor things, but i also wanted to be able to view certain web pages and at that low a res they look like crap.

any thoughts as to why its not saving changes?

---

