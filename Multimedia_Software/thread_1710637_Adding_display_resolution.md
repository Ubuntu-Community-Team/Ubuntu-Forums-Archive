---
title: "Adding display resolution"
date: 2011-03-20
forum: Multimedia Software
---

### Post by jdcjohn80 on 2011-03-20
Hi , I'm new to Ubuntu. The version I am using is Release 10.10 (Maverick), Gnome 2.32.0. 

My display card is ATI INC RV280 Radeon 9200 rev01 Pro.while monitor is LG W2043S capable of 1600X900 resolution.

Under monitor preferences, the highest resolution listed is 1360 x 768 . The second is 1024 x 768. I do not like this resolution as it appears 'big'.

Is there a possibility to add say, 1280 X 1024 or even 1600 X 900 if my display card is able to support it?

I tried to use the information provided under 
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions) 
but I received the following 

jd@jd-desktop:~$ cvt 1600 900
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
jd@jd-desktop:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27
  Current serial number in output stream:  27

I tried also with 1280 X 1024 but receive the same output as above. Could I get some help. Thank you in advance.

---

### Post by realzippy on 2011-03-20
maybe a 1600x900 mode still exists due to running command twice?
Anyway,post output from

```
xrandr

```
and welcome!

---

### Post by jdcjohn80 on 2011-03-20
hi realzippy, glad to get your reply

I got the following info
--------------------------------------------
jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0x11d)  119.0MHz
        h: width  1600 start 1696 end 1864 total 2128 skew    0 clock   55.9KHz
        v: height  900 start  901 end  904 total  932           clock   60.0Hz
  1280x1024_60.00 (0x12a)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
jd@jd-desktop:~$ 

----------------------------------------------

---

### Post by realzippy on 2011-03-20
please run:

```
xrandr --addmode VGA-0 1600x900_60.00
```

then again post output from

```
xrandr
```

---

### Post by jdcjohn80 on 2011-03-20
I ran 'xrandr --addmode VGA-0 1600x900_60.00' and the screen went freeze ..white with some lines in horizontal

Using this same code, I tried to add other settings such as 1280x1024 , 1400x1024 but could not. After restarting I found that in System-->Preferences-->Monitors that the setting 1152 x 864 is now available. Before none.

Then I tried again with another Resolution....1360x900. it works. But before I restart the computer to check if the setting stays, I post you the xrandr information

jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 2048
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

jd@jd-desktop:~$ cvt 1360 900
# 1360x900 59.90 Hz (CVT) hsync: 55.94 kHz; pclk: 100.25 MHz
Modeline "1360x900_60.00"  100.25  1360 1440 1576 1792  900 903 913 934 -hsync +vsync
jd@jd-desktop:~$ xrandr --newmode "1360x900_60.00"  100.25  1360 1440 1576 1792  900 903 913 934 -hsync +vsync
jd@jd-desktop:~$ xrandr --addmode VGA-0 1360x900_60.00
jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 900, maximum 2048 x 2048
VGA-0 connected 1360x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   1360x900_60.00   59.9* 
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$ 

I will now restart the computer

---

### Post by jdcjohn80 on 2011-03-20
... setting 1360x900 went missing after restart. Before the login , there was screen that appeared informing the setting cannot be applied.

I mention earlier the 1600x900 with the freeze screen...well I tried again:) just to test again..

Now it did not freeze white screen. 1600x900 is the screen I had before in Vista. It works well especially when I am able to read 2 pages side by side.

The only problem now I have is I am not sure it will save the configuration after I restart.

Thank you so much realzippy. Your a real help!

---

### Post by jdcjohn80 on 2011-03-20
Before I restart
There was a few resolution I tried before the second try of 1600x900 resolution

jd@jd-desktop:~$ cvt 1360 1020
# 1360x1020 59.99 Hz (CVT 1.39M3) hsync: 63.47 kHz; pclk: 114.75 MHz
Modeline "1360x1020_60.00"  114.75  1360 1448 1584 1808  1020 1023 1027 1058 -hsync +vsync
jd@jd-desktop:~$ xrandr --newmode "1360x1020_60.00"  114.75  1360 1448 1584 1808  1020 1023 1027 1058 -hsync +vsync
jd@jd-desktop:~$ xrandr --addmode VGA-0 1360x1020_60.00
jd@jd-desktop:~$ cvt 1500 844
# 1504x844 59.98 Hz (CVT) hsync: 52.55 kHz; pclk: 104.25 MHz
Modeline "1504x844_60.00"  104.25  1504 1592 1744 1984  844 847 857 876 -hsync +vsync
jd@jd-desktop:~$ xrandr --newmode "1504x844_60.00"  104.25  1504 1592 1744 1984  844 847 857 876 -hsync +vsync
jd@jd-desktop:~$ xrandr --addmode VGA-0 1504x844_60.00
jd@jd-desktop:~$ xrandr --addmode VGA-0 1600x900_60.00
xrandr: cannot find mode "1600x900_60.00"
jd@jd-desktop:~$ cvt 1600 900
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
jd@jd-desktop:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
jd@jd-desktop:~$ xrandr --addmode VGA-0 1600x900_60.00
jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 4096 x 4096
VGA-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
   1360x1020_60.00   60.0  
   1504x844_60.00   60.0  
   1600x900_60.00   59.9* 
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$

---

### Post by jdcjohn80 on 2011-03-20
Ok, when I logged out and then logged in
a screen appeared on the right and mention that it could not apply the store configuration

The screen is now 1024 x768 under monitor preferences

Xrandr information 

jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$

---

### Post by realzippy on 2011-03-20
...your last xrandr ouput:

```
jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 4096 x 4096
VGA-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1360x768 59.8
1024x768 60.0
800x600 60.3 56.2
848x480 60.0
640x480 59.9 59.9
1360x1020_60.00 60.0
1504x844_60.00 60.0
1600x900_60.00 59.9* 
```

says (*) you are running desired 1600x900.
Do you?

---

### Post by realzippy on 2011-03-20
Guess you do.
We were cross-posting;sorry for absence,was in real life..

The "addmode" ran successfully,1600x900 seems to be available.
Guess you set the 1600x900 with the monitor settings GUI (which just is a GUI for xrandr..)
Try to set it with

```
xrandr -s 1600x900
```

or if that not works

```
xrandr -s 1600x900_60
```

since this works (does it?) only for the current running session,
add the running command to
System/Settings/StartupApplications
so it should work after reboot..

---

### Post by jdcjohn80 on 2011-03-21
Hi Realzippy.

Wish you well. I apologize for the late reply. 

I tried both codes provided , all work ok, until I log off and log in.

The attachment are the PrtScn pics, Could you check, could be i made a mistake at the StartupApplications command box...

After restart, all settings come back as default 1024x768. The 1152x864 has made its own comeback, and it is default now when I restart or log off.

Best Regards,
John

---

### Post by realzippy on 2011-03-21
No,no mistake.
on my machine this startup application command (xrandr -s bla) works (but running an Intel graphics chip).Anyway...:

Can you check if there is a file:

~/.config/monitors.xml     ?

Probably it exists since it is created by the monitor-preferences GUI tool.
Delete the file:

```
rm ~/.config/monitors.xml
```

and restart.
Do not use the system/settings/monitors tool.

---

### Post by jdcjohn80 on 2011-03-21
After I entered '~/.config/monitors.xml'  this came out 

jd@jd-desktop:~$ ~/.config/monitors.xml
bash: /home/jd/.config/monitors.xml: Permission denied

I entered the delete code anyway and restarted

---

### Post by realzippy on 2011-03-21
*I entered the delete code anyway and restarted*

...and what happened after restart?

---

### Post by jdcjohn80 on 2011-03-21
After restart, I tried the following

cvt 1600 900
then
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
then
xrandr --addmode VGA-0 1600x900_60.00
then
xrandr -s 1600x900_60

In startup applications I inserted the command as in the pic before 'xrandr -s 1600x900_60'

I restart

Still came back to 1152x864

the latest  xrandr information :
jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 2048
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$

---

### Post by jdcjohn80 on 2011-03-21
After I deleted the code in msg 14, it came back to 1152x864. only then i tried the msg 15.

---

### Post by realzippy on 2011-03-21
You not need to run anymore:

cvt 1600 900
xrandr --newmode "1600x900_60.00" 118.25 1600 1696 1856 2112 900 903 908 934 -hsync +vsync
then
xrandr --addmode VGA-0 1600x900_60.00

If you ran those once,it is enough.
Please do exactly this:
1.Reboot
 Do **not** run any other commands or use the monitors settings GUI!!
 Run (again):
 ```
rm ~/.config/monitors.xml
```
 Since the file should not exist anymore,it should complain something like
 "*no file  ~/.config/monitors.xml*" or similar.**Does it?**
 Then run
 ```
xrandr
```
and post it's output.

---

### Post by jdcjohn80 on 2011-03-21
I get the following msg: rm: cannot remove `/home/jd/.config/monitors.xml': No such file or directory

then after xrandr

jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2048 x 2048
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$

---

### Post by realzippy on 2011-03-21
Ok,the problem seems to be that xrandr forgets the mode you have added.
Probably a bug,since it used to work before you upgraded.
Dirty workaround would be a script at startup that runs the 3 xrandr commands....wait a few minutes please.

---

### Post by jdcjohn80 on 2011-03-21
ok, thanks

---

### Post by realzippy on 2011-03-21
..not so easy.Tested it here...normally a script should run from
xinitrc,but for some raeson I it does not.
Also a generated .xprofile file containing the xrandr command
does not work at startup although it manually works.
quick googling finds others having problems running xrandr scripts at startup,so I discard this solution for the moment until I can make a xrandr script working here.
Anyway,as mentioned,this solution would be kinda dirty,so we should test if a xorg.conf file works:

1,Write this down since you won't be able to paste (mind capital "X"):
  sudo service gdm stop
  sudo Xorg -configure
  sudo service gdm start      

2.Press Alt+Ctrl+F2
  A shell opens,log in with username&password
  Type:
  ```
sudo service gdm stop
```
  ```
sudo Xorg -configure
```
  
a file xorg.conf.new should get created in your user's home folder.
  ```
sudo service gdm start
```
should bring you back.Post the content of created file,can use gedit:

```
gedit ~/xorg.conf.new
```

---

### Post by jdcjohn80 on 2011-03-21
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "dbe"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by realzippy on 2011-03-21
Ok,will reduce it and modify it to your needs,takes a few minutes.
Meanwhile:
Do you know how to start in recovery mode?
(If the xorg.conf we are going to test leeds to black screen at boot,
you have to delete the file from recovery mode..)

---

### Post by jdcjohn80 on 2011-03-21
the recovery mode can be selected at the bottom of the login screen right?

---

### Post by realzippy on 2011-03-21
No,when system boots press "shift"...you should get a few kernels to choose
and for every kernel a [recovery mode]("https://help.ubuntu.com/community/Grub2").
"*The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. ..bla*"

...when you got this,I 'll give you the 1rst version of the file to test  ;-)

---

### Post by jdcjohn80 on 2011-03-21
ok, got it

---

### Post by jdcjohn80 on 2011-03-21
Hi Realzippy, thank you so much for your help. Your a wonderful person, helping me all this way. I will test the file when I receive it. But I am sorry, I got to go now as I will be working in about 6 hrs time. Got to sleep:) sorry about that. Monday was 'Black Monday' as usual, and exhausting. Hopefully Tuesday will be better.
Have a wonderful day mate!

---

### Post by realzippy on 2011-03-21
run
```
gksudo gedit /etc/X11/xorg.conf
```

empty file opens (if not,stop here and post the output !)

paste in:

```
Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
Modeline  "1600x900_60.00" 118.25 1600 1696 1856 2112 900 903 908 934 -hsync +vsync
Option    "PreferredMode" "1600x900_60.00"
EndSection

Section "Device"
Identifier "Card0"
Driver "radeon"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Depth           24
Modes   "1600x900" "1024x768" "640x480"
EndSubSection
EndSection
```

close file saving changes.
Reboot,fingers crossed.
..if problems boot in recovery mode,log in at shell,run
```
sudo rm /etc/X11/xorg.conf
```
```
sudo reboot

```

or start low graphics session or kind of (have not been there for a while..)
and delete the file with file browser (nautilus): 
/etc/X11/xorg.conf 
and restart.

**BTW**:
Generally assuming your system is "vanilla",means,you have not e.g.:
-- added graphics PPAs (xswat eg)
-- blacklisted modules/disabled KMS
-- or tried other stuff
to solve your problem besides "xrandr" .. **?**

Also make sure the checkbox in system/settings/startupapplications/options (remember settings)is **not** set.

---

### Post by jdcjohn80 on 2011-03-22
Hi realzippy,

After I entered the code 
gksudo gedit /etc/X11/xorg.conf 
in terminal, it ask for password and then the file contents as:


Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2048 2048
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

---

### Post by realzippy on 2011-03-22
...there should be no xorg.conf.
So I guess you tried more stuff before xrandr....
Anyway..delete the stuff inside the file (backup we have here..),
and paste in the whole suggested content from post #28...

---

### Post by jdcjohn80 on 2011-03-22
I did the fingers crossed:) 

The results...it is still in 1152X864.

Can I enter the xrandr to show you the information?

---

### Post by realzippy on 2011-03-22
Good sign that it boots;no xrandr action needed now.
Now we add Hsync/vrefresh values to the file,which normally gives a wider range of resolutions.
To do this,we need to know the monitor you use,exact model name,if possible...

---

### Post by jdcjohn80 on 2011-03-22
Monitor: LG W2043S

Display Card: ATI INC RV280 Radeon Pro 9200 rev01

---

### Post by realzippy on 2011-03-22
The values for your model are:
H 30-83 Hz
V 56-75 MHz

again run:

```
gksudo gedit /etc/X11/xorg.conf
```

and make your "monitor section" look like this:

```
Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
HorizSync       30.0 - 83.0
VertRefresh     56.0 - 75.0
EndSection
```

close file saving changes;
reboot.
Now you should have more resolutions in xrandr or the monitor-settings GUI.

I have to leave the forum for 2 hours in 10 minutes,real life calling...

If it does not work,we will use a "dirty" script.Figured out last night how to do.So your problem will be solved today;just a little patience ;-)
cy

---

### Post by jdcjohn80 on 2011-03-22
simply superb ...you make my day

jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1792 x 1792
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x900       59.9 +
   1792x1344      60.0  
   1600x1200      65.0     60.0  
   1680x1050      74.9     69.9     60.0  
   1600x1024      60.2  
   1400x1050      74.8     70.0     60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0* 
   1024x768       75.0     70.1     60.0     59.9  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$ 


I will test by choosing the 1600x900 in GUI and restart. Is that ok for you?

After , when you are available, I have a small question, my Terminal seems to start after I login now.This happen when we ran some test yesterday here.

How do I stop that?

---

### Post by jdcjohn80 on 2011-03-22
something bad happen...cause of me. I went greedy. I was at the GUI...monitor preferences watching in happines all that resolution. Click on 1600x900...and I saw there was 1400x1050...what the heck...click that and 'apply' . Disaster all the way.

Monitor went blank, with small light blue screen showing' Out of range...64.7Khz max 60Khz'

Luckily you showed me the way to recovery mode.

I went there, still not able to to do anything, then i did the sudo rm /etc/X11/xorg.conf.

Then I still could not get back the resolutions. I went and repeated as far as thread 12.[FONT=monospace] [/FONT]rm ~/.config/monitors.xml


I got back all resolutions now, as before.

Then i did the test. I tried 1600x900 but 1440 X900 seems much better. I restart, and it started in 1440x900 :)

Only for the terminal starting auto now..how to kill that action?

Thank you so much

---

### Post by jdcjohn80 on 2011-03-22
Correction:
Then I still could not get back the resolutions. I went and repeated as far as thread 12.rm ~/.config/monitors.xml

Should be
Then I still could not get back the resolutions. I went and repeated as far as reply # 12.      rm ~/.config/monitors.xml

---

### Post by realzippy on 2011-03-22
I am back.
1. Your monitor's panel native resolution is 1600x900;
   normally this is the best for use...

2.Does the command created yesterday in startupapplications still exist?

---

### Post by jdcjohn80 on 2011-03-22
hi there:)

I have deleted the command during reply #32

---

### Post by realzippy on 2011-03-22
..asking because of up-popping terminal when system starts.
Have you just deleted the command inside or unchecked the checkbox?

---

### Post by jdcjohn80 on 2011-03-22
Unchecked the box:)

IF I reverse it like this, will it work? 

say since I have unchecked the box...I close the terminal and mozilla firefox...then I checked the box 'remember the currently running applications' and then restart.....will it do the trick?

---

### Post by realzippy on 2011-03-22
'remember the currently running applications'

has to be empty, means unchecked.

---

### Post by jdcjohn80 on 2011-03-22
its empty, unchecked

---

### Post by realzippy on 2011-03-22
So when you reboot now,no terminal pops up?

---

### Post by jdcjohn80 on 2011-03-22
when reboot, the terminal still pops up

---

### Post by realzippy on 2011-03-22
**?**

Can you make a screenshot (or 2 if you have to scroll down)
from your Startup Applications?

---

### Post by realzippy on 2011-03-22
***close the terminal** and mozilla firefox...then I checked the box 'remember the currently running applications' and then restart.....will it do the trick?*

Yes!
Just tested it here,it should work!

---

### Post by jdcjohn80 on 2011-03-22
sure thing , it is attached

---

### Post by jdcjohn80 on 2011-03-22
I will try #47 , give me a minute

---

### Post by jdcjohn80 on 2011-03-22
hi realzippy, it work....thank you so much

---

### Post by realzippy on 2011-03-22
...you solved it yourself.

back to topic (your resolution):

As you might remember,I was surprised that a xorg.conf file existed.
Nowadays the ati (radeon) driver you use should work without any xorg.conf..

So lets test this.
Open terminal,rename existing xorg.conf to xorg.conf.test,so
the system "thinks" there is none and the kernel sets the display modes:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.test
```

also (just to be sure) run
```
rm ~/.config/monitors.xml

```

Reboot.Then run xrandr or open monitor-settings GUI...

---

### Post by jdcjohn80 on 2011-03-22
jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$ 


Fyi,   my ati radeon driver was never installed

---

### Post by jdcjohn80 on 2011-03-22
sorry i was late

---

### Post by realzippy on 2011-03-22
...the radeon driver comes with the kernel.No need to install it.
Have you ever disabled KMS? (If you do not know what it is,you have not,I hope)...
Run
```
dmesg | grep drm
```
please

---

### Post by jdcjohn80 on 2011-03-22
I downloaded the driver from AMD-ATI website : [http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx) , the [X.Org 6.8 Drivers]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/fglrx64_6_8_0-8.28.8-1.x86_64.rpm") ,. Extracted it to the download folder. But I still have not found the method to install it. I tried to install it using the package manager, but got confused on the way....this was last week.

---

### Post by jdcjohn80 on 2011-03-22
KMS...never heard about it:)

jd@jd-desktop:~$ dmesg | grep drm
[   18.576306] [drm] Initialized drm 1.1.0 20060810
[   18.732127] [drm] radeon defaulting to kernel modesetting.
[   18.732135] [drm] radeon kernel modesetting enabled.
[   18.744204] [drm] initializing kernel modesetting (RV280 0x1002:0x5960).
[   18.751474] [drm] register mmio base: 0xF8030000
[   18.751480] [drm] register mmio size: 65536
[   18.753118] [drm] Generation 2 PCI interface, using max accessible memory
[   18.753201] [drm] radeon: irq initialized.
[   18.753347] [drm] Detected VRAM RAM=128M, BAR=128M
[   18.753353] [drm] RAM width 64bits DDR
[   18.761702] [drm] radeon: 128M of VRAM memory ready
[   18.761706] [drm] radeon: 128M of GTT memory ready.
[   18.761844] [drm] Loading R200 Microcode
[   18.778792] [drm] radeon: ring at 0x00000000E0000000
[   18.778813] [drm] ring test succeeded in 0 usecs
[   18.779189] [drm] radeon: ib pool ready.
[   18.779303] [drm] ib test succeeded in 0 usecs
[   18.779500] [drm] Default TV standard: PAL
[   18.779504] [drm] 27.000000000 MHz TV ref clk
[   18.779508] [drm] DFP table revision: 4
[   18.779587] [drm] Default TV standard: PAL
[   18.779590] [drm] 27.000000000 MHz TV ref clk
[   18.779631] [drm] Radeon Display Connectors
[   18.779634] [drm] Connector 0:
[   18.779636] [drm]   VGA
[   18.779639] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   18.779641] [drm]   Encoders:
[   18.779644] [drm]     CRT1: INTERNAL_DAC1
[   18.779646] [drm] Connector 1:
[   18.779647] [drm]   DVI-I
[   18.779649] [drm]   HPD1
[   18.779652] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   18.779654] [drm]   Encoders:
[   18.779655] [drm]     CRT2: INTERNAL_DAC2
[   18.779658] [drm]     DFP1: INTERNAL_TMDS1
[   18.779660] [drm] Connector 2:
[   18.779661] [drm]   S-video
[   18.779663] [drm]   Encoders:
[   18.779665] [drm]     TV1: INTERNAL_DAC2
[   19.152965] [drm] fb mappable at 0xE8040000
[   19.152972] [drm] vram apper at 0xE8000000
[   19.152975] [drm] size 3145728
[   19.152977] [drm] fb depth is 24
[   19.152979] [drm]    pitch is 4096
[   19.156938] fb0: radeondrmfb frame buffer device
[   19.156941] drm: registered panic notifier
[   19.165859] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor

---

### Post by realzippy on 2011-03-22
You cannot install the downloaded ATI catalyst driver,since it does not run under
the actual X server,ATI dropped support for old cards some time ago.If you run the installer,it messes up your system.

The output is fine,radeon is running as you can see;anyway,xrandr shows that your desired resolution is missing,so we should re-enable created xorg.conf file,but we should know which resolution you want.
As claimed 1600x900 is native and should look best,but you prefer
1440x900 ??
In this case we had to modify the modeline,no problem,just wondering..
so decision?

---

### Post by jdcjohn80 on 2011-03-22
1440x900 is better...so I will choose this

---

### Post by realzippy on 2011-03-22
```
gksudo gedit /etc/X11/xorg.conf
```

paste in: (should be empty!)

```
Section "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
HorizSync       30.0 - 83.0
VertRefresh     56.0 - 75.0
Modeline  "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
Option    "PreferredMode" "1440x900_60.00"
EndSection

Section "Device"
Identifier "Card0"
Driver "radeon"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Depth           24
Modes   "1440x900" "1024x768" "640x480"
EndSubSection
EndSection
```

reboot...
Hopefully it boots into that resolution,if not,post xrandr output (do not use monitors GUI...)

---

### Post by jdcjohn80 on 2011-03-22
Hi Realzippy,

I will be back today evening . Sorry, had to go sleep .... 4hrs to final countdown-work! :)

Have a great day ahead and thank you.

Best Regards,

---

### Post by jdcjohn80 on 2011-03-22
jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1792 x 1792
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1440x900_60.00   59.9 +
   1792x1344      60.0  
   1600x1200      65.0     60.0  
   1680x1050      74.9     69.9     60.0  
   1600x1024      60.2  
   1400x1050      74.8     70.0     60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9     59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0* 
   1024x768       75.0     70.1     60.0     59.9  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$ 

it boots into 1152x864

---

### Post by realzippy on 2011-03-22
..open xorg.conf again 

```
gksudo gedit /etc/X11/xorg.conf
```

and disable the modeline (since it does not seem to work),just put a "#" in front of it like:

#Modeline  "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

also change

Option    "PreferredMode" "1440x900_60.00"
to
Option    "PreferredMode" "1440x900"


Then reboot and show me xrandr's output again.........

---

### Post by jdcjohn80 on 2011-03-23
Hi realzippy,

Wish you well.

I did the editing,save, reboot....

then, xrandr info:

jd@jd-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1792 x 1792
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1440x900       59.9 +   59.9  
   1792x1344      60.0  
   1600x1200      65.0     60.0  
   1680x1050      74.9     69.9     60.0  
   1600x1024      60.2  
   1400x1050      74.8     70.0     60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0* 
   1024x768       75.0     70.1     60.0     59.9  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
jd@jd-desktop:~$

---

### Post by realzippy on 2011-03-23
Hi john,
so run in terminal
```
xrandr -s 1440x900

```
does it work?

---

### Post by jdcjohn80 on 2011-03-23
Yes, It changed to 1440X900 .

Should I reboot?

---

### Post by realzippy on 2011-03-23
Reboot,but the command is only for this running session,so it will reboot in your old resolution.
After rebooting open the monitor-settings GUI,choose the resolution,make it default,reboot again...
Normally this should work now.
If not,we add a xrandr command to startup-application.

---

### Post by jdcjohn80 on 2011-03-23
Yes, you are right, it was only for one session.

After reboot,  I open the GUI 'Monitor Preferences' and the 1440 X 900 was applied.

After reboot, it started in 1440 x 900 :)

---

### Post by jdcjohn80 on 2011-03-23
I will be right back...just received a visitor in 'real life' :)

---

### Post by realzippy on 2011-03-23
So I guess the problem is solved...please mark thread as solved (threadtools).

Offtopic:
..concerning your startup-applications screenshot I would suggest to
disable:

1.Check for new hardware-drivers(there will never be some for your machine)
2.Bluetooth manager (unless you use bluetooth)
3.Print queue applet (unless you have a printer)
4.Remote Desktop (security issue;or do you ever use it?)
5.Ubuntu One (unless you use it)
6.Update Notifier (prefer checking for updates manually;it is always a  
  good idea to wait with updates a few days,so bugs get fixed by the  
  community before they affect you.)

Won't promise your system boots faster,but  it would be kind of "cleaner"  ;-)

---

### Post by jdcjohn80 on 2011-03-23
Hi realzippy,

Done-startup applications

Thank you so much for your help.

Truly appreciate it. It was great following your directions. Learn lots:)

Best Regards

---

### Post by realzippy on 2011-03-23
This was interesting (the xrandr-forget-addded-modes-bug),also you were acting ubuntunoobunlike precisely,so I wanted you sometimes running xrandr commands where you could have used the GUI instead.Sorry for abuse,someone will benefit.
Maybe after the next kernel-updates you won't need the xorg.conf file no more to get all resolutions available...otherwise,as we say here,it "eats no bread"  ;-)
you are welcome!

---

