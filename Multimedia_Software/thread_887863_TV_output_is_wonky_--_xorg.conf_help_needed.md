---
title: "TV output is wonky -- xorg.conf help needed"
date: 2008-08-12
forum: Multimedia Software
---

### Post by toaster.waffle on 2008-08-12
I'm having some problems getting my TV output to work on my VIA EX15000G using the openchrome driver.

I get video on my TV, but it's slanty and off-colour (see attached photo).

The video is stationary: no scrolling horizontally or vertically.

Here is my attempt at an xorg.conf which is partially pre-generated and partially hand-crafted.

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us+inet"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "openchrome"
        # Let's see...
        BusID "PCI:1:0:0"
        Option "ActiveDevice" "TV"
        Option "TVOutput" "Composite"
        Option "TVType" "NTSC"
        #Option "VBEModes" "True"
        ##
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes     "ntsc_640x480"
        EndSubSection
EndSection

```

What need I add to correct the picture?

Also, I'd like this machine to plug into any TV and have it work (like one would expect from a Wii or other TV-attaching device).  Is this a pipedream?

Thanks,

---

### Post by toaster.waffle on 2008-08-12
I added a monitor section to try to force, perhaps, the refresh rate.

```

Section "Monitor"
        Identifier  "TV_NTSC"
        HorizSync   30-50
        VertRefresh 60
EndSection

```

And then added to the screen section...

```

Section "Screen"
        ...
        Monitor "TV_NTSC"
        ...
EndSection

```

This just made the slantiness less slanty.  Instead of two vertical splittings, there is one, down the middle.  Again, it's less slanty.

Any ideas?

---

### Post by toaster.waffle on 2008-08-14
I don't know how to move my thread to the MythBuntu forum, so I re-posted for simplicity's sake.

[http://ubuntuforums.org/showthread.php?p=5585315#post5585315](http://ubuntuforums.org/showthread.php?p=5585315#post5585315)

---

### Post by p_quarles on 2008-08-14
> **toaster.waffle said:**
> I don't know how to move my thread to the MythBuntu forum, so I re-posted for simplicity's sake.

[http://ubuntuforums.org/showthread.php?p=5585315#post5585315](http://ubuntuforums.org/showthread.php?p=5585315#post5585315)
You can't -- next time just hit the "Report" button on your own post and ask the staff to move it. We're happy to do so. 

Duplicate thread closed.

---

