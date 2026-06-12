---
title: "TV output is wonky -- xorg.conf help needed"
date: 2008-08-14
forum: Mythbuntu
---

### Post by toaster.waffle on 2008-08-14
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
toaster.waffle

P.S.

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

This just made the slantiness less slanty.  Instead of two vertical splittings, there is one, down the middle.

Any ideas?

---

### Post by toaster.waffle on 2008-08-26
*bump*   Sorry.	 ](*,)

---

### Post by toaster.waffle on 2008-09-13
Reinstalled and cleared CMOS.  Fudged some things in BIOS setup and changed the default Driver "vesa" to Driver "via" in xorg.conf.  Failed to work, but the Ubuntu thing came up (low-video settings?) and I selected the openchrome driver and 720x420 resolution.

Now that video works, I have to move onto solving "Watch TV" not working despite being able to watch streamed video from Apple.com.

---

