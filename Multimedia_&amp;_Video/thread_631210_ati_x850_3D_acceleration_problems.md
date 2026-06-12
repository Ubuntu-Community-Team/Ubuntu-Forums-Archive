---
title: "ati x850 3D acceleration problems"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by gurth4ng on 2007-12-04
Hello. I'm having problems enabling 3D acceleration on my ubuntu 7.10 and despite trying everything found on howtos etc i cant seem to fix it. I'm using a ATI Radeon x850 card with the fglrx driver version 8.37.6 (the version automaticly installed by default after enabling the restricted drivers).

I've gotten compiz-fusion to work after installing xgl, and it's pretty smooth.

The problem is, i cant get 3d acceleration to work. when i try to open something that uses 3d acceleration (for example world of warcraft run through CrossOver) i'm getting an error that the application wasnt able to start 3d acceleration.

Here are some things i thing might be helpful:

> gurth4ng@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X850 XT Platinum Edition
OpenGL version string: 2.0.6473 (8.37.6)
> gurth4ng@ubuntu:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
> gurth4ng@ubuntu:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
50104 frames in 5.0 seconds = 10002.915 FPS
50520 frames in 5.0 seconds = 10103.994 FPS
50455 frames in 5.0 seconds = 10068.282 FPS
Any ideas? it's really annoying :(

---

### Post by gurth4ng on 2007-12-08
/bump

 :(

---

### Post by melojo on 2007-12-08
Post your /etc/X11/xorg.conf so users can take a look at it.

I have a x850 pro and it works great with ubuntu's restricted driver.

---

### Post by Yellow Pasque on 2007-12-08
XGL is preventing you from running direct rendering. I'd recommend removing xserver-xgl and xorg-driver-fglrx, and then installing the latest ATI driver and using AIGLX if 3D is really important to you. Beware the bugs though :(

---

### Post by melojo on 2007-12-08
If you do decide to use the 7.11 drivers this is a howto guid the worked for me.
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

my system seemed to run slower with compiz enabled though so I reverted back to the default driver.

---

### Post by gurth4ng on 2007-12-08
thx for the replies, i'll try removing XGL and install the latest drivers (7.11) tomorrow, i'll tell you how it goes :)

---

### Post by gurth4ng on 2007-12-17
Sorry it took me so long, i was kinda busy and i didnt have much time for testing ;) thx again for the replies.

I removed xserver-xgl and xorg-driver-fglrx, and then i installed the lastest ATI drivers (7.11) using the manual install guide.

I now finally have 3d acceleration (yay!), but compiz isnt working properly. if i enable it, when i login my desktop has nothing on it, just a white screen. I can see compiz is working (i can use the cube etc) but i just have a white screen on each workspace.

Any ideas?

EDIT: fixed the white screen temporarily by disabling Visual Effects from the Appearance Preferences window. Now my desktop is working fine without compiz, but when i try to enable it again from the Appearance Preferences i'm getting the following error:
> Failed to execute child process "compiz" (Permition Denied)
Also if i try to start compiz from the command line i get
> gurth4ng@ubuntu:~$ compiz
bash: /usr/bin/compiz: Permission denied

here's my xorg.conf:

```

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

#       Load            "GLcore"
        Load  "glx"
#       Load            "dri"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
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
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc R481 [Radeon X850XT-PE]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc R481 [Radeon X850XT-PE]"
        Monitor    "SyncMaster"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

---

### Post by Tarmael on 2007-12-17
Did you whitelist and blacklist the drivers from Compiz?

It's listed in the wiki melojo posted. I'll copy and paste the code if you like.
```

sudo gedit /usr/bin/compiz

``````

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

``````

# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""

```

This could fix the problem.

---

### Post by gurth4ng on 2007-12-18
yea i did, no luck...

---

### Post by gurth4ng on 2008-01-04
any ideas? i cant seem to figure out what's wrong :(

to sum things up, i'm getting an error when trying to enable visual effects in Appearance, saying:

Failed to execute child process "compiz" (permition denied)

---

### Post by gurth4ng on 2008-01-25
I thought of trying again with the 8.01 fglrx driver, this is where i am atm.

From a Gutsy system running the original (from the repos) fglrx with no Direct Rendering but running Compiz perfectly (with XGL) i did the following:

1. I installed fglrx folowing the instructions found here
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)

2. I uninstalled XGL (since the new drivers have AIGLX and dont need XGL)

3. i followed the instructions here, under the 3d desktop effects section
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)

At this point, after restarting, i had direct rendering, with lower framerate than before (glxgears give me around 8000 frames while it used to give 10500), but no compiz.

Running **compiz --replace** gave me this error:
```
/usr/bin/compiz: 379: /usr/local/bin/compiz: not found
```

I read here about someone that had a similar problem
[http://forum.compiz-fusion.org/showthread.php?t=6385&page=2](http://forum.compiz-fusion.org/showthread.php?t=6385&page=2)
on topic #18, he was adviced to try this
```
$ sudo cp /etc/xdg/compiz/compiz-manager.ubuntu /etc/xdg/compiz/compiz-manager
```

After this, when i run **compiz --replace ccp** from a terminal i'm getting Compiz to run (finally!), with the following worning:
```
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Things seem to be working fine at first, but they're not. While Compiz now works with decent framerate on most effects and i can run programs that need direct rendering, these programs are flickering like crazy.

Also, when i try running a video, it flashes on my screen for half a second and then then it remains black.

Also some Compiz effects are slow, while most (the cube for example) are working right.

[I]

If only i had bought an Nvidia.... :mad:[/I]

---

