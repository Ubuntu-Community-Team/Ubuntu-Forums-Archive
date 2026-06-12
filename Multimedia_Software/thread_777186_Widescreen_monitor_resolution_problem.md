---
title: "Widescreen monitor resolution problem"
date: 2008-05-01
forum: Multimedia Software
---

### Post by Mark Phelps on 2008-05-01
My "old" 20" flat panel went out and I replaced it with a new 24" widescreen Samsung.  When I hooked it up to my system (Ubuntu 7.10, ATI X1600 card), it would not give me the max 1920x1200 resolution.  The highest it would go is 1920x1080.  Running xrandr, that shows as the max resolution.

I used the screens dialogue to select a monitor, but my model (245BW) is not listed. I selected LCD panel, and was able to get 1920x1200 but the fonts are so bad that they are unreadable!

I manually edited the xorg.conf file to add 1920x1200@60 to the display section, but still, the max I can get is 1920x1080.

Suspecting the monitor, I booted into Windows -- 1920x1200 no problem! 

Suspecting Linux, I booted into a LiveCD of 8.04 -- came up 1920x1200 by default, fonts are OK!  In 8.04, xrandr says that 1920x1200 is the max resolution

So, how do I get my 7.10 installation to recognize the max resolution of the monitor -- with decent fonts?

---

### Post by Mark Phelps on 2008-05-03
2 days now and not a single response -- thanks a lot!!

---

### Post by Sqwishy on 2008-05-03
Are the drivers installed? If so you could try manually editing the xorg.conf so you can get the resolution you want.
This is for feisty, but it sounds like your having the same problem.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support)

---

### Post by Zorael on 2008-05-04
> **Mark Phelps said:**
> 2 days now and not a single response -- thanks a lot!!
[quote=Linux is not Windows]If a "3a" user runs into trouble with Linux, he'll complain: The software hasn't met his standards, and he thinks he has a right to expect that standard. His mood won't be improved when he gets sarcastic replies like "I'd demand a refund if I were you"

So, to avoid problem #3a: Simply remember that you haven't paid the developer who wrote the software or the people online who provide the tech support. They don't owe you anything.[/quote]
See [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm). Notably section 3a.


That said, try this in a terminal. You'll likely lose some videocard settings, and if so, we'll just restore those.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xserver-xorg
```
Then restart X with Ctrl+Alt+Backspace.

---

### Post by Mark Phelps on 2008-05-04
I tried adding the resolution manually to the xorg.conf file.  Linux conveniently ignored it and came up in 1600x1200 mode.  I then removed ALL resolutions from the xorg.conf except the 1920x1200.  Linux ignored that and came up in 800x600 mode.

I ran the dpk-reconfigure xserver-xorg not once, but over a half-dozen times!

Each time, it appeared to create a proper xorg.conf file; each time, Linux ignored the settings and came up in whatever resolution it wanted.

So, I opened up the Xorg.0.log file, found the lines where the monitor is interrogated for resolution modes, copied off the modelines I needed, manually added them to the xorg.conf file.  And once again, Linux ignored the file and came up in a different resolution!

Every time that xwindows started the desktop, I ran xrandr; and every time, it claimed the max resolution was 1600x1200 or less!

As I may have mentioned before, I rebooted using a hardy heron LiveCD, and it found the 1920x1200 resolution with no problems.  So, it's not a monitor problem.

OK, so you can flame me for complaining, but I worked at this nearly nonstop for over eight hours -- into the early hours of the morning, with absolutely no success.  None of the old, saved, xorg.conf files worked.  Noe of the generated files worked.  None of the hand-edited files worked.

Next day, got up, did a complete restore of my root partition (I do make backups periodically), and went through the diag steps once more:
1) reran the dpkg-reconfigure xserver-xorg again
2) hand-edited the xorg.conf file to add the screen size, the horizontal sync, and the vertical sync
3) restarted the xserver
4) re-enabled the fglrx driver (ATI restricted)
5) rebooted (and held my breath ...)

Surprise!! When it restarted, I had 1920x1200 resolution using the ATI restricted driver!

So, what did I do different?? Nothing.  I restored my machine to a state several weeks back, and redid the same steps, in the same sequence, that I had been doing for over eight hours.  But this time, it worked.

I posted the message because I had been doing, AFAIK, the "right" things and nothing was working.  I was hoping that someone knew some obscure stuff that would work. So, sorry if I bashed your sacred Linux, but I did everything the "book" says to do regarding xorg.conf files, and everything I could find in HOURS of reading post after post on the Ubuntu forums -- and absolutely nothing worked!!  So, if my frustration got the better of me, sorry about that.

---

### Post by randallecook on 2008-05-05
Mark,

I think you and I are in similar boats, except I have an nVidia card. Our monitors and trouble are the same, however. I tried your steps and it did not work. I am stuck at the same 1600x1200 you were. Perhaps it is because I did not hold my breath. :)

If you could post your working xorg.conf, I would be most appreciative. There are so many defaults in xorg, it is hard to know whether one's xorg.conf is correct or not. TIA.

---

### Post by Mark Phelps on 2008-05-06
Here's my "working" xorg.conf ...

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "SyncMaster"
        HorizSync    30.0 - 81.0
        VertRefresh  56.0 - 75.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "EnableMonitor" "auto"
        BusID       "PCI:3:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "SyncMaster"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1920x1200" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

Hope this helps...

---

### Post by randallecook on 2008-05-07
Thanks, Mark. Unfortunately, it did not help. My system failed to recognize that the monitor supports 1920x1200 and reverted to failsafe. BTW, are you connecting with an analog or digital video cable? If digital, are you using a single link or dual link DVI connector?

Randall

---

### Post by Mark Phelps on 2008-05-07
Randall:

I'm using a digital cable, but how to I tell which kind?

---

### Post by randallecook on 2008-05-12
Mark,

I'm not sure either. All I know is that there seem to be two kinds of digital connection, and I have read that with the dual one it is possible for the computer to discover monitor resolutions greater than 1920x1600, while with the single type the limit is 1920x1600. Yes, that implies that either connection should work with my monitor, but I am hoping that the dual mode "works better".

Alas, while the nVidia docs suggest that my card supports both modes, it does not say which connector is which. In any event, I only get video at any resolution from one connector (the one closer to the s-video jack).

I have an identical monitor at home connected to an nVidia GeForce FX 5200, and ubuntu 7.04 was able to drive it at 1920x1600 after only running 'dpkg-reconfigure xserver-xorg' and restarting. I am afraid to try ubuntu 8.04 on that machine. :)

In any event, all this tells me that the monitor is OK. It must be the card. Admittedly, it is a relatively uncommon nVidia Quadra FX 3450. It came with the machine, which originally ran Windows XP.

I'll keep trying, perhaps in a more focused post. This one is veering off-topic. Thanks for all your help.

---

