---
title: "How To: MythBuntu S-Video Output on Dell Inspiron 1525"
date: 2008-06-08
forum: Mythbuntu
---

### Post by danbodoh on 2008-06-08
Here's a few notes on how I got happiness with MythBuntu, using the S-Video output on a Dell Inspiron 1525 laptop.

The graphics are Intel X3100 (also known as GM965 or 965GM).  I'm running Mythbuntu 8.04 using the 
stock xf86-video-intel-2.2.1 driver.

xorg.conf: I wanted to clone the s-video, and that works with the auto-generated xorg.conf (which actually contains very little; the intel driver needs very little.)  I wanted to force 800x600, so I added "PreferredMode":

```

Section "Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Identifier      "Configured Video Device"
        Option          "monitor-TV" "TV"
        Option          "DPMS" "off"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Monitor"
        Identifier "TV"
        Option "PreferredMode" "800x600"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection

```

This works great for cloning the GUI, but any video only shows up on the LCD screen.  The LCD (known as LVDS to the driver) must be turned off to force video to the TV.  I'll show how to make this permanent later:

```
xrandr --output LVDS --off
```

You can turn the LVDS back on with

```
xrandr --auto
```

The default height and width does not fill the my TV screen, so I use xrandr to stretch it out.  Your values might be different.  Note that "TV" is the driver's name for the s-video port.

```

xrandr --output TV --set BOTTOM 0
xrandr --output TV --set TOP 0
xrandr --output TV --set LEFT 40
xrandr --output TV --set RIGHT 20

```


But, on my TV at least, the display is very washed out, and video is grainy.  I played with xgamma for a while, but that didn't fix the problem.  The real solution is to modify the contrast settings on the card.  There are two different settings: one for video and one for the GUI.

First, get xvattr and xcalib from the repo:

```

sudo apt-get install xvattr xcalib

```

xvattr sets contrast (and other things) for Xv, the video playback extension.  The best way I found to set this was to play a recording, then ssh to the mythmachine and experiment with xvattr remotely while watching the video.  A setting of 50 worked for me:

```

danb@remote$ ssh mythbox
danb@mythbox$ export DISPLAY=:0.0
danb@mythbox$ xvattr -a XV_CONTRAST -v 50

```

Now fix the GUI with xcalib. An easy way to do this is to look at pictures in MythGallery, which gives you a range of contrast.  Find one that is almost overexposed, but where you can normally see details in the bright areas.  If you can't see those details on the TV, the contrast is too high.  Again, use the ssh trick.  A setting of 55 works for me, but yours may differ.  Note that this contrast scale is different that xvattr:

```

danb@remote$ ssh mythbox
danb@mythbox$ export DISPLAY=:0.0
danb@mythbox$ xcalib -clear
danb@mythbox$ xcalib -contrast 55 -alter

```

Between each experimental contrast setting, use 'xcalib -clear' to reset, because xcalib commands are cumulative.

When you have your numbers, make it permanent.  It may be possible to put some of this into xorg.conf, but I couldn't figure out how.  Instead, I add it to the .bashrc for the user that runs the frontend.  Add this to the end of .bashrc:

```

if [ -f XRANDR ]; then
    xrandr --output LVDS --off
    xrandr --output TV --set BOTTOM 0
    xrandr --output TV --set TOP 0
    xrandr --output TV --set LEFT 40
    xrandr --output TV --set RIGHT 20
    xcalib -clear
    xcalib -contrast 55 -alter
    xvattr -a XV_CONTRAST -v 50
fi

```

Then 'touch ~/XRANDR'.  The XRANDR condition lets you turn this off my deleting XRANDR if you want to log into the system without it.

Now, to run the .bashrc when you log in, you'll have to autostart a terminal on login:

```

cd ~/.config/autostart
ln -s /usr/share/applications/xfce4-terminal.desktop ./

```

Hope this works for you!

Dan Bodoh

---

### Post by danbodoh on 2008-06-08
One more thing: by default, the video will blank when the lid is closed.  To prevent this:

```

sudo mkdir /etc/acpi/events/save
sudo mv /etc/acpi/events/lidbtn /etc/acpi/events/save
sudo /etc/init.d/acpid restart

```

Dan Bodoh

---

