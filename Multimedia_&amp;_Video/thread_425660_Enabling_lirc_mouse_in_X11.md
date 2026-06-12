---
title: "Enabling lirc mouse in X11"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by mvsjes2 on 2007-04-27
I'm trying to enable my remote control to emulate a mouse in X11. I'm very close but can't get around the last problem.

The problem is (from xorg log):
(**) Option "Protocol" "IntelliMouse"
(**) Remote: Device: "/dev/lircm"
(**) Remote: Protocol: "IntelliMouse"
(**) Option "SendCoreEvents"
(**) Remote: always reports core events
(**) Option "Device" "/dev/lircm"
(EE) xf86OpenSerial: Cannot open device /dev/lircm
        No such file or directory.
(EE) Remote: cannot open input device
(EE) PreInit failed for input device "Remote"
(II) UnloadModule: "mouse"

xorg does accept my definitions:
(==) ServerLayout "DualLayout"
(**) |-->Screen "Monitor Screen" (0)
(**) |   |-->Monitor "DELL M992"
(**) |   |-->Device "Video Port 0"
(**) |-->Screen "TV Screen" (1)
(**) |   |-->Monitor "Toshiba TV"
(**) |   |-->Device "Video Port 1"
(**) |-->Input Device "Keyboard"
(**) |-->Input Device "Mouse"
(**) |-->Input Device "Remote"

lircmd is running and the device is there:
sh-3.2$ ps -e | grep lirc
 4929 ?        00:00:00 lircd
 4931 ?        00:00:00 lircmd
 5389 ?        00:00:00 lircrcd
 5458 ?        00:00:00 lircrcd

sh-3.2$ ls -l /dev | grep lirc
drwxr-xr-x 2 root root          60 2007-04-27 20:13 lirc
srw-rw-rw- 1 root root           0 2007-04-27 20:14 lircd
prw-r--r-- 1 root root           0 2007-04-27 20:15 lircm

Is this a timing problem? Is X coming up before lircmd is started?

Any suggestions?

---

### Post by mvsjes2 on 2007-06-06
I fixed this by:
sudo update-rc.d -f lirc remove
sudo update-rc.d lirc start 50 S .
so that lirc initializes before X.

Was this the correct solution? Is there a better way to solve it? Should I report this as a bug?

---

### Post by brazzmonkey on 2007-06-18
yes, i guess this is some sort of bug... i've got similar lirc behaviour : it works fine once i restart X.
(personal) curiosity, could you please post your xorg.conf and any other relevant file ? i can't figure out how to get my remote control act as a mouse, though it seems to be properly detected.
thanks.

---

### Post by mvsjes2 on 2007-06-18
It tunrs out I used a script that I wrote a while ago to install lirc, and part of it was to start it too late in the process. I thought the lirc install had done that, not me. I'm not sure if there's an "approved" position for starting lirc, but the above works for me.

```

# xorg.conf for dual head dell m992 and toshiba tv

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Remote"
    Driver         "mouse"
    Option         "Device" "/dev/lircm"
    Option         "Protocol" "IntelliMouse"
    Option         "SendCoreEvents"
    Option         "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "DELL M992"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Toshiba TV"
    VendorName     "Toshiba"
    ModelName      "30HF84"
    DisplaySize     665    385
    HorizSync       14.0 - 46.0
    VertRefresh     56.0 - 61.0
              #Modename    clock  horizontal timing  vertical timing
   #Modeline "1280x720@60" 74.25 1280 1312 1592 1624 720 735 742 757
    Modeline "1280x720@60" 75.25 1280 1320 1600 1624 720 735 742 757
EndSection

Section "Device"
    Identifier     "Video Port 0"
    Driver         "nvidia"
    BusID          "PCI:7:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Video Port 1"
    Driver         "nvidia"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Monitor Screen"
    Device         "Video Port 0"
    Monitor        "DELL M992"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       24
#        Modes     "1280x1024" "1024x768" "800x600" "640x480"
        Modes      "1024x768" "800x600"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "TV Screen"
    Device         "Video Port 1"
    Monitor        "Toshiba TV"
    Option         "UseEDID" "False"
    DefaultDepth    24
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1280x720@60" "1280x720_60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "DualLayout"
    Screen      0  "Monitor Screen" 0 0
    Screen      1  "TV Screen" RightOf "Monitor Screen"
    InputDevice    "Keyboard"
    InputDevice    "Mouse"
    InputDevice    "Remote"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

/etc/lirc/lircmd
```

# 
# lircmd config file
# 

PROTOCOL IntelliMouse

# ACCELERATOR start max multiplier

ACCELERATOR 2 30 5

ACTIVATE * Clear

MOVE_N  * 2
MOVE_NE * 3
MOVE_E  * 6
MOVE_SE * 9
MOVE_S  * 8
MOVE_SW * 7
MOVE_W  * 4
MOVE_NW * 1
MOVE_IN * ChanUp
MOVE_OUT * ChanDown

BUTTON1_TOGGLE * OK
BUTTON2_TOGGLE * Down
BUTTON3_TOGGLE * Home

BUTTON1_CLICK * 5
BUTTON2_CLICK * Star
BUTTON3_CLICK * Hash

# BUTTONx_CLICK, BUTTONx_UP, BUTTONx_DOWN are also possible

```

In this config I enter the "Clear" button on my remote to switch to X11 lirc mouse mode.

---

### Post by brazzmonkey on 2007-06-19
thanks a lot, that actually helped me (i don't have so many button on my RC, so i had to tweak lircmd a bit).
what does your trick actually does ? make lirc start at runlevels S, 0 and 5 ?

---

### Post by mvsjes2 on 2007-06-19
I starts lirc as part of system initialization. Instead of starting it in a specific run level, it starts it in /etc/rcS.d.

Glad I could help a bit.

---

### Post by brazzmonkey on 2007-06-19
> **mvsjes2 said:**
> I starts lirc as part of system initialization. Instead of starting it in a specific run level, it starts it in /etc/rcS.d.
ok, so that's basically what i did using sysv-rc-conf.
thanks again.

---

### Post by brazzmonkey on 2007-06-19
> **mvsjes2 said:**
> I starts lirc as part of system initialization. Instead of starting it in a specific run level, it starts it in /etc/rcS.d.
this does not work for me. i still have to manually launch sudo /etc/init.d/lirc start so that i'm able to use my RC in KDE.

---

### Post by mvsjes2 on 2007-06-19
cd /etc/rcS.d
ls -l | grep lirc

You should see something like "S50lirc -> ../init.d/lirc". This will confirm that you are asking for it to be started when you start your system. Make sure its startup is before the x11-common script.

If you don't see lirc in that library, try entering the commands above and see if that fixes it.

---

### Post by brazzmonkey on 2007-06-20
i get :```
$ ls -l | grep lirc
lrwxrwxrwx 1 root root  14 2007-06-19 22:21 S81lirc -> ../init.d/lirc
``` so it seems it actually start after X11.
now, when i run your commands, i get ```
$ sudo update-rc.d lirc start 50 S
update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
```
is there a typo or something ??

---

### Post by mvsjes2 on 2007-06-20
You need a "." at the end of the command (it's in the command I posted above). Since lirc is already there, you will probably have to run the remove command too. Before you choose "50", list what's in /etc/rcS.d and make sure that position makes sense for your system. It should start a little before x11-common startss. I don't know enough about linux to assume that startup positions for individual products would be the same for your and my systems.

---

### Post by brazzmonkey on 2007-06-20
damn, now i see the whole point of using ```
 tags ! :)
[code]sudo update-rc.d lirc start 50 S .
```
"50" is OK for me as x11-common start at "70", so it should do the trick.

thanks again, and sorry for wasting your time with my stupid questions...

---

### Post by mvsjes2 on 2007-06-20
No problem, glad I could help.

---

