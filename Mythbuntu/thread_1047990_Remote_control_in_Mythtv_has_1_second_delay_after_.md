---
title: "Remote control in Mythtv has 1 second delay after key"
date: 2009-01-23
forum: Mythbuntu
---

### Post by mathog on 2009-01-23
This I think belongs in a new thread.  However, the details of this problem are described in the last post here:

[http://ubuntuforums.org/showthread.php?t=1046371](http://ubuntuforums.org/showthread.php?t=1046371)

In brief, I have a remote working in Mythtv, but there is a 1 second delay between the button being pushed (for instance, an arrow), and Mythtv responding.  This is unacceptably slow for menu navigation using the arrow keys.

Any idea what might be causing it?

Thank you.

---

### Post by stronzo on 2009-01-23
might be the remote itself.
you can start "irw" in a console and see how fast it receives the remote signals if you push a button. then you know if its the remote - or the software. my remote has different speeds on different keys, no joke!

---

### Post by tbaca on 2009-01-23
I am seeing the samething (running fixes and a homemade serial interface).  IRW also shows the 1 second delay.  Not a hardware problem as the hardware has not changed.  I have not had much time to see if there is any pattern.  But I believe it is also effecting the blaster side as I am seeing many mis-cues in channel changing.

---

### Post by mathog on 2009-01-23
> **stronzo said:**
> might be the remote itself.
you can start "irw" in a console and see how fast it receives the remote signals if you push a button. then you know if its the remote - or the software. my remote has different speeds on different keys, no joke!

That test was mentioned in the link:

> irw has no delays between key presses and logging those events.

irw usually shows 3 identical lines per key press.

---

### Post by newlinux on 2009-01-23
Do you have the same problem when using LIRC with other applications, like mplayer? trying to see if it is an LIRC problem or a myth problem with LIRC on your system

---

### Post by mathog on 2009-01-24
This may be a related issue: when watching TV if the remote is used to get into the program guide, then a few arrow keys are pressed (it doesn't really matter which ones, up,down, whatever) the guide will track the first few but eventually lock and stop responding.  Once in this state it also ignores the keyboard.  It may time out eventually, but I never waited that long, and ended up using "kill -9" from a terminal in the other screen to kill the mythfrontend.  Oddly, if the exact same sequence is entered from the keyboard nothing bad happens.  Arrow keys can be pressed on the keyboard until the cows come home and it just does what is expected.

On the other hand, in the mythfrontend menu the arrow keys from the remote seem not to have this effect, and I have yet to see a lock up there.

Pretty annoying bug, since I'm pretty sure the family is not going to want to have to use a keyboard to watch TV!

---

### Post by newlinux on 2009-01-24
did you check if the problems happens with the remote and other applications?

---

### Post by mathog on 2009-01-25
A lot of variables here...

I changed the video playback profile from "normal" to "ch--" and that helped a bit.  But the primary issue seems to be one of focus.  My system has screen0 and screen1, the latter is TV-OUT and has the mythfrontend running on it.  If the focus is in screen1 then pretty much all of these issues go away:  up/down menu selections move quickly, and there are few if any lock ups.  However, click on a terminal in screen0 (for instance, to be able to run "top"), then the remote goes all to hell, with slow response, and lock ups in the mythfrontend.  Putting the mouse back on screen1, clicking the left mouse button, restores remote activity very rapidly.

So it looks like the solution would be to lock lirc "focus" to the desired screen.  Sadly, there seems to be no option to do so.  Disabling screen0 would do it I guess, but then all configuration would have to be done via an SSH session.

---

### Post by mathog on 2009-01-25
> **mathog said:**
>  But the primary issue seems to be one of focus.  

Also of CPU utilization.   System has:

  Nvidia 8400 GS
  Athlon64 64 X2 dual core 4000+
  Nvidia 177.82-0 (glx, kernel-source, modalias)

In screen0 open a terminal and start "top".
In screen1 start mythfrontend (TV-OUT 640x480)
Watch TV

  Xorg CPU utilization goes to 80-95% (SD or HD)
  mythfrontend CPU utilizating goes to 15-35%
  
  On remote:
Guide (enters guide)
Arrows up/down/right/left.
After a while it locks.  (If the focus had been in screen0 it would have locked almost instantly - it takes a while this way, but it happens sooner or later anyway.)

Once the guide stops responding BOTH screens lock.  The "top" in screen0 stops updating. But the cursor can still be moved.  As soon as the cursor moves from screen1 to screen0 "top" unlocks.  Very shortly thereafter the guide unlocks and rapidly goes through all of the missed remote control key presses.

Ugh.  So this could be a CPU utilization issue, interacting with a focus issue, interacting with who knows what else.  This graphic card can't be used with XvMC.  Anything else I can do to drop the CPU utilization?  Here is the xorg.conf, is there something that could be put in here to drop the CPU utilization:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-420GS"
    HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0; CRT: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

THanks.

---

### Post by newlinux on 2009-01-26
For CPU usage decrease try putting
```

Option "UseEvents"  "on"

```

in your nvidia device sections and restarting X

---

### Post by mathog on 2009-01-26
> **newlinux said:**
> For CPU usage decrease try putting
```

Option "UseEvents"  "on"

```

in your nvidia device sections and restarting X

No difference.

Went into setup for tv-playback, guide, and unchecked EVERYTHING on the first page, set shading to ECO, reduced channels to 4 and increased slots to 5.  No difference.  (The guide interface is dumb about centering channel information with no icons, it offsets to the right leaving space, even though there is no icon ever going to be shown.)  Also, when channels shown is set to 5, only 4 are shown, when 7, only 5.

Went into mythtv-setup, to channel editor, and had a look at icons.  There were none.  Tried to download some through that interface.  Still none.  The source is Schedules Direct.  

Went manage recordings -> schedule recordings -> program guide.  This one is just like the TV one, except it has more channels and no live TV show at the top.  Pushed remote keys up/down/left right until I got bored - no glitches.  Also virtually no CPU usage.

Finally, in "Watch TV", used the up/down keys on the remote to move channels, and then Enter to set it.  Did that for a very long time without it locking up.


In the /var/log/mythtv log files the only errors are a few about "joystock disabled", and what looks like one of these for each mythfrontend, or maybe backend, start:

mythbackend.log:2009-01-26 20:23:57.641 Preview Error: Previewer file '/home/mythdbstorage/1504_20090126202355.mpg' is not valid.

So, still a complex issue.  The guide itself, at least in the recording variant, has no issues, it is only when the guide and the reduced TV live feed are both on that it hangs up.  And that combination "smells" of an nvidia driver interaction, since that is when the CPU usage for Xorg goes super high.

---

### Post by mjmos on 2009-01-27
For me, killing the screensaver process made my streamzap working.

---

### Post by mathog on 2009-01-27
This evening's "entertainment" trying to squish this bug:

1. Sure, I'll grasp at that straw
> **mjmos said:**
> For me, killing the screensaver process made my streamzap working.

killed gnome-screensaver
Result: no difference.
2. increasing tv-out size 640x480 -> 720x480
Result: MUCH worse.  this locked up even with the keyboard.  CPU higher.
3. general theme QT -> OpenGL:
Result: No change.

The CPU usage is definitely a video issue.  When the TV image is static for a second or two the CPU usage drops down to just a few percent.
Maybe VDPAU will help?  I really don't want to be using experimental code in the living room DVR though.

I'm running out of options here.  Hmm, I suppose maybe only using TV-OUT,
no monitor.  (One screen/display).  I'll try that later.

---

