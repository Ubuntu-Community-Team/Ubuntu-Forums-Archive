---
title: "How to get a higher rez on my monitor"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by cynon83 on 2007-03-09
I have an nvidia 7800GT PCIe video card and am running Ubuntu 6.06.  I just bought a Dell 22" flat screen with a high resolution, but when I tried to adjust the screen resolution, the best resolution listed is 1024x768 -- not nearly high enough for the monitor, which wants to see 1680 x 1050 at 60 Hz.

I'm pretty sure I have the latest nvidia drivers, but perhaps I don't.  Has anyone else gotten this monitor to a high resolution?

Thanks!

---

### Post by williammanda on 2007-03-09
Make sure you know what driver you have...I use 1.0.9746. In the xorg.conf file use:
option "UseEDID" "True" (this is normally on but I found it is better to put it in) this will read your monitor for the proper resolution.

"nvidia-auto-select" this tells xorg to use the best resolution which should be the native resolution of your monitor.

I will post where to put these when i get home.
Thanks

---

### Post by cynon83 on 2007-03-09
Since that wasn't the monitor that was on the system when I installed it, I guess I should find a way to make it re-scan the hardware?  I mean, maybe I have the right driver, but it doesn't auto-detect the new monitor.

---

### Post by williammanda on 2007-03-09
Make sure you know what driver you have...I use 1.0.9746. In the xorg.conf file use:
option "UseEDID" "True" (this is normally on but I found it is better to put it in) this will read your monitor for the proper resolution.

"nvidia-auto-select" this tells xorg to use the best resolution which should be the native resolution of your monitor.

I will post where to put these when i get home.
Thanks

---

### Post by williammanda on 2007-03-09
Ok here is the xorg.conf

Section "Monitor"
  Identifier "Monitor0"
  VendorName "unknown"
  ModelName "unknown"
   Option "UseEDID" "true"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  DefaultColorDepth 24

  SubSection "Display"
  Depth 24
  Modes "nvidia-auto-select"
  EndSubSection
EndSection

Hope this helps! I have a westinghouse 42 lcd monitor and the native resolution is 1366x768. I can only get 1360x765 but that works great.

---

### Post by cynon83 on 2007-03-10
Okay, so now I feel like a complete idiot.  How do I tell what driver I'm currently using?  I looked in the device manager, and under the PCIE bridge is has an unknown listing.  The advanced tab for that, under info.linux.driver shows nvidia.  But I think that's the MB driver.

Looking at the xconf file, here is what I get:
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
 EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
EndSection

So... not to be too overly lame, but any idea where I migth find which driver is being used?  Or, perhaps theres a way to re-initialze the autodetect so that it knows which monitor I'm using, although I suspect that wouldn't help overly much.

Thanks!

---

### Post by cynon83 on 2007-03-10
Well, thanks to your advise, I modified my xorg.conf and now everything is way, way awesome!  Thanks a ton.

Just in case anyone else needs to know what I did, here it is:
First, I needed to install the nvidia driver.  I noticed that Automatix2 noted that I didn't have the nvidia driver installed, so I let it install it.  Note: It did not install the latest, but then, I don't have the latest video card, just a 7800GT, so the driver it installed worked find.
On reboot, I noticed that I was still not given the option for a higher resolution, so I went into the xorg.conf and found these lines and commented them all out:
SubSection "Display"
Depth 24
Modes "1024x768" "832x624" "800x600" "720x400" "640x480" "640x400"
EndSubSection
EndSection

I replaced the above lines with the lines suggested by williammanda:

SubSection "Display"
Depth 24
Modes "nvidia-auto-select"
EndSubSection
EndSection

That's ALL I did.  I rebooted and the monitor came up in its native resolution.

Thanks williammanda for your help!

---

### Post by enopepsoo on 2007-03-10
I found that I needed to restart the system to get the new resolution after editing my xorg.conf, but I am sure that doing the gdm restart thing should actually work fine.:KS

---

