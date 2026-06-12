---
title: "2 X Servers 2 Monitors HOWTO?"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by basgoossen on 2007-03-17
Hello,
Already since a long time i trying to get my normal PC running both my desktop monitor (KDE) and my TV (MythTV) as a media center. First i tryed this using XINERAMA  and MERGEFB, but without succes.
Now i'm wondering can't i just run 2 seperate x servers, one for my monitor and one for my TV (would be best if those could be run simultaneously). So i started trying that. And already got some of it to work. but i need some help now on getting it right.

my problem is that i can't get X to point at a certain monitor, so whether i do 
startx -- :0.0 or startx -- :0.1
X just starts on both monitors and using one as a clone.

I think there need to be some adjustments in my xorg.conf but i can't seem to get it right.

Could anybody help me with this problem?

---

### Post by rumli on 2007-03-17
Note that :0.0 and :0.1 refer to different screens (0 and 1) on the same X server (0).  
I'm assuming that that's what you actually want: 2 screens within a single X server.
If you want the 2 screens to act together as one virtual screen, then you should leave the "Xinerama" option in the example below at "true".
If you want the 2 screens to act independently, (i.e., each screen has it's own panels, and the apps on one screen can't be dragged to the other), then set the "Xinerama" option to "false".

I strongly encourage you not to give up on Xinerama yet.  You should be able to get it working using the example below, and it is so much nicer than having 2 independent screens.  You can drag windows from one monitor to another, have windows straddle the two screens, and still have fullscreen and maximization behavior work intuitively.  Using Xinerama, windows maximize or go fullscreen to cover only one of the two monitors, depending on the position of the window just before maximization.

As you rightly guessed, to achieve this, you have to edit your /etc/X11/xorg.conf so that it contains 2 Screen sections, 2 Monitor sections, and 2 Device sections.  If you have a single video card (e.g., a dual-head videocard), the BusID in both Device sections should be the same.
The Screen, Monitor, and Device sections are linked together in a straightforward manner as shown below.
This example shows the relevant pieces of the /etc/X11/xorg.conf that allow Xinerama to work with two monitors plugged into a dualhead nVidia card.

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Primary Screen" 0 0
    Screen      1  "Secondary Screen" RightOf "Primary Screen"
    ....
EndSection

Section "ServerFlags"
    Option         "Xinerama" "true"
EndSection

Section "Extensions"
    Option         "Composite" "false"
EndSection

Section "Device"
    Identifier     "Video Card DFP Connection"
    Driver         "nvidia"
    BusID          "PCI:2:0:0"
    Option         "UseDisplayDevice" "DFP"
    Screen          0
EndSection

Section "Device"
    Identifier     "Video Card CRT Connection"
    Driver         "nvidia"
    BusID          "PCI:2:0:0"
    Option         "UseDisplayDevice" "CRT"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Primary Screen"
    Device         "Video Card DFP Connection"
    Monitor        "Primary Monitor"
    ...
EndSection

Section "Screen"
    Identifier     "Secondary Screen"
    Device         "Video Card CRT Connection"
    Monitor        "Secondary Monitor"
    ...
EndSection

Section "Monitor"
    Identifier     "Primary Monitor"
    ...
EndSection

Section "Monitor"
    Identifier     "Secondary Monitor"
    ...
EndSection

```

An important part of all this is getting X server to link the right Screen section with the right video connection.  Different drivers (nVidia, ATI, etc.) require different techniques for doing this.  For nVidia cards with nVidia drivers, you should put the "UseDisplayDevice" option in each screen and set it to either "CRT" or "DFP" depending on whether the monitor for the appropriate screen is plugged into the card using a CRT connection or a DFP connection.  Note that the being a CRT or DFP connection is not a property of the monitor but of the slot on the video card that the monitor is plugged into (e.g., if a flat panel were plugged into the CRT slot of the video card, you would use the "CRT" value for the "UseDisplayDevice" option.)  If you have two DFP or two CRT connections, they can be differentiated by using "DFP-0", "DFP-1", "CRT-0", "CRT-1", etc.  

ATI drivers have a similar option called "MonitorLayout".  [This Gentoo Linux Wiki]("http://gentoo-wiki.com/HOWTO_Dual_Monitors") contains further information.

Good luck! :)

---

### Post by basgoossen on 2007-03-18
> 
Note that :0.0 and :0.1 refer to different screens (0 and 1) on the same X server (0).
I'm assuming that that's what you actually want: 2 screens within a single X server.
If you want the 2 screens to act together as one virtual screen, then you should leave the "Xinerama" option in the example below at "true".
If you want the 2 screens to act independently, (i.e., each screen has it's own panels, and the apps on one screen can't be dragged to the other), then set the "Xinerama" option to "false".


In fact that is not what i want, i want to do :0.0 and :1.1, two seperate x-servers for 2 seperate monitors.

---

### Post by majoridiot on 2007-03-20
run:

```
# gksudo nvidia-settings
```

and configure with the resolutions, etc. you want for each screen with **Twinview enabled** and
**Xinerama disabled**.  save the settings to your xorg.conf from nvidia-settings and then restart
X (ctrl-alt-tab).

you now have two "independent" desktops that you can drag windows between, etc.  

launching mythtv-frontend from the second screen will allow you to use myth fullscreen 
on that head while using the first monitor for regular desktop use at the same time.

this worked great for me when i was running 2 heads.

---

