---
title: "TV out working but need monitor output too"
date: 2008-06-21
forum: Mythbuntu
---

### Post by jwrudolf on 2008-06-21
I installed a Geforce4 pci graphics card into my mythbuntu box.  I set up the proprietary nvidia drivers in the installer and composite out works fine.  Unfortunately the resolution is low enough that I can't efficiently navigate menus (the text is too blurry).  I would like to enable a monitor in addition to the composite out so I can finish configuring the machine.  Any help in getting the onboard vga port or the graphics card vga port to output a signal in addition to the composite out would be a great help.  Thanks

---

### Post by bah1976 on 2008-06-23
I can't find the directions that I used to do it, but the keyword is twinview.  In the nvidia x server setup, "X server display configuration, there's a Configure button.  If both displays are detected, you can set it to twinview, which will mirror to both outputs.  This is obviously by no means a technical guide - just a pointer in the right direction.  I'd recommend googling for specific setup help.

Edit: Found the link for the directions I used.

[http://ubuntuforums.org/showthread.php?t=665704]("http://ubuntuforums.org/showthread.php?t=665704")

---

### Post by allene222 on 2008-06-24
I would advise against twinview.  Use separate desktops and set up two of them.  This gives you two independent desktops that you can switch between with the mouse.  Twinview has interactions between the settings that, in my case at least, did not allow me to acceptably set things  up.

Good luck,

Allen

---

### Post by jwrudolf on 2008-06-24
Thanks very much for the help.  I was able to switch to svideo out by manually modifying the xorg.conf (/etc/X11/xorg.conf).  That gave me a high enough resolution that I was able to do the rest of the setup (configure the remote and mount a second hard drive to record onto).  Since I'm up and going now I'm reluctant to tempt fate and try enabling the monitor concurrently with the tv.  But I'm going to keep this info in mind for later. I'll definitely try it sometime.  I might just image the hard drive and then start breaking/fixing settings to learn more about the system.

---

### Post by novellahub on 2008-06-25
Another option would be to enable VNC and connecting remotely. I do this quite frequently with my myth boxes.

---

### Post by Nate B. on 2008-07-28
> **allene222 said:**
> I would advise against twinview.  Use separate desktops and set up two of them.  This gives you two independent desktops that you can switch between with the mouse.

I'm in the same boat using a GeForce FX 5200 with S-Video and VGA outputs.  When installing Mythbuntu I selected the S-Video output only to realize when I rebooted that the display was on the TV!  My TV is a 15 year old Zenith that still works great, but it isn't clear enough to make using MCC possible.

While I am fairly experienced with Linux (predominantly Debian), I've not ever tried anything like setting up a second desktop in Xorg.  That would appear to be a very useful configuration so I'm curious if there is a pointer or HOWTO where I could do this easily.

I am able to SSH into the both and do sudo aptitude, etc. so I do have remote access to edit files.

---

### Post by Nate B. on 2008-07-29
Well, that was easy once I was able to run MCC using ssh forwarding (ssh -X) from my desktop.  Only thing is that once I reconfigured Xorg for a second display I lost the TV out.  D'oh!  Fortunately, it saved the previous xorg.conf so I'll tackle that later.  :)

---

### Post by Nate B. on 2008-07-29
A little bit of reading and fiddling with the original xorg.conf from the initial Mythbuntu install is working fine with the same output on the monitor as the TV.

First I brought my monitor's definitions over as so (lines in bold were added):

```

Section "Monitor"
        Identifier     "Generic Monitor"
[B]        Vendorname      "NEC"
        Modelname       "NEC MultiSync XV15+"
        Horizsync       31.0-65.0
        Vertrefresh     55.0-100.0
[/B]        Option         "DPMS"
**        modeline  "1024x768" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync**
EndSection


```

And then I modified the video card section as so:

```

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
[B]    Option         "TwinView"   "on"
    Option         "TwinViewOrientation"        "clone"
    Option         "MetaModes"  "1024x768, nvidia-auto-select"
[/B]#    Option         "UseDisplayDevice" "TV"
[B]    Option         "ConnectedMonitor"      "CRT, TV"
[/B]    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"

EndSection

```

Cloning suits me fine as I can use VNC or ssh to do what I need remotely.

---

