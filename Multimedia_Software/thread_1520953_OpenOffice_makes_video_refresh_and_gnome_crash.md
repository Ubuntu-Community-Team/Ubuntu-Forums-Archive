---
title: "OpenOffice makes video refresh and gnome crash"
date: 2010-06-30
forum: Multimedia Software
---

### Post by danduq on 2010-06-30
Hi,

Since upgrading to Lucid a few days ago I'm having intermittent problems (90% of the time) with opening OpenOffice files.

When I open up a spreadsheet (.ods) in OO, (whether OO was already open or not) my screens go black, then flash on and off for 30 seconds (ish) as if trying to change the refresh rate.

Sometimes this results in Gnome crashing and restarting itself. Sometimes it settles down and is OK. On a few occasions I have had to change terminal and manually restart gdm.

Any help or advice you can give would be hugely appreciated!

Here's my environment;
Dell Latitude D620
nVidia GeForce Go 7300 (according to hwinfo)
Ubuntu Lucid 32-bit (upgraded from Jaunty)
2 GB RAM

I've got the recommended "NVIDIA accelerated graphics driver (version current)" hardware driver and the NVIDIA X Server Settings applet, which says my NVIDIA driver version is 195.36.24.

I'm running dual screens (1440x900 and 1280x1024) using TwinView.

After a flicker, here is what I find in the Xorg.0.log;

```

(II) Jun 30 12:17:42 NVIDIA(0): Setting mode
(II) Jun 30 12:17:42 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:43 NVIDIA(0): Setting mode
(II) Jun 30 12:17:43 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:45 NVIDIA(0): Setting mode
(II) Jun 30 12:17:45 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:47 NVIDIA(0): Setting mode
(II) Jun 30 12:17:47 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:48 NVIDIA(0): Setting mode
(II) Jun 30 12:17:48 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:50 NVIDIA(0): Setting mode
(II) Jun 30 12:17:50 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:51 NVIDIA(0): Setting mode
(II) Jun 30 12:17:51 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:53 NVIDIA(0): Setting mode
(II) Jun 30 12:17:53 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:55 NVIDIA(0): Setting mode
(II) Jun 30 12:17:55 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:56 NVIDIA(0): Setting mode
(II) Jun 30 12:17:56 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:58 NVIDIA(0): Setting mode
(II) Jun 30 12:17:58 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:17:59 NVIDIA(0): Setting mode
(II) Jun 30 12:17:59 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:01 NVIDIA(0): Setting mode
(II) Jun 30 12:18:01 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:02 NVIDIA(0): Setting mode
(II) Jun 30 12:18:02 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:04 NVIDIA(0): Setting mode
(II) Jun 30 12:18:04 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:06 NVIDIA(0): Setting mode
(II) Jun 30 12:18:06 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:07 NVIDIA(0): Setting mode
(II) Jun 30 12:18:07 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:09 NVIDIA(0): Setting mode
(II) Jun 30 12:18:09 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:10 NVIDIA(0): Setting mode
(II) Jun 30 12:18:10 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:12 NVIDIA(0): Setting mode
(II) Jun 30 12:18:12 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:14 NVIDIA(0): Setting mode
(II) Jun 30 12:18:14 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:15 NVIDIA(0): Setting mode
(II) Jun 30 12:18:15 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:17 NVIDIA(0): Setting mode
(II) Jun 30 12:18:17 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:18 NVIDIA(0): Setting mode
(II) Jun 30 12:18:18 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:20 NVIDIA(0): Setting mode
(II) Jun 30 12:18:20 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:21 NVIDIA(0): Setting mode
(II) Jun 30 12:18:21 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:23 NVIDIA(0): Setting mode
(II) Jun 30 12:18:23 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:25 NVIDIA(0): Setting mode
(II) Jun 30 12:18:25 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:26 NVIDIA(0): Setting mode
(II) Jun 30 12:18:26 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:28 NVIDIA(0): Setting mode
(II) Jun 30 12:18:28 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:29 NVIDIA(0): Setting mode
(II) Jun 30 12:18:29 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:31 NVIDIA(0): Setting mode
(II) Jun 30 12:18:31 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:33 NVIDIA(0): Setting mode
(II) Jun 30 12:18:33 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:34 NVIDIA(0): Setting mode
(II) Jun 30 12:18:34 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:36 NVIDIA(0): Setting mode
(II) Jun 30 12:18:36 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:37 NVIDIA(0): Setting mode
(II) Jun 30 12:18:37 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:39 NVIDIA(0): Setting mode
(II) Jun 30 12:18:39 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:41 NVIDIA(0): Setting mode
(II) Jun 30 12:18:41 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:42 NVIDIA(0): Setting mode
(II) Jun 30 12:18:42 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:18:44 NVIDIA(0): Setting mode
(II) Jun 30 12:18:44 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Jun 30 12:19:08 NVIDIA(0): Setting mode
(II) Jun 30 12:19:08 NVIDIA(0):     "CRT:nvidia-auto-select+1440+0,DFP:nvidia-auto-select+0+124"
(II) Jun 30 12:19:09 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Jun 30 12:19:09 NVIDIA(0):     enough to receive ACPI hotkey events.
(WW) Jun 30 12:19:09 NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
(WW) Jun 30 12:19:09 NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
(WW) Jun 30 12:19:09 NVIDIA(0):     respond to ACPI brightness change hotkey events.

```

I also get some errors in my .xsession-errors file, but I don't think they're related;

```

[Error 12:17:20.882] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:17:20.895] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:17:20.902] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:17:20.910] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:17:20.917] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:17:20.925] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:17:20.933] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:17:20.941] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:20.956] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:21.007] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:21.018] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:21.025] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:21.033] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:21.041] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:21.049] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:19:21.057] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.069] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.087] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.095] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.103] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.110] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.118] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.126] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop
[Error 12:21:21.134] Could not load desktop item: Unknown encoding of: file:///home/dan/.local/share/applications/Uninstaller-1249299489155.desktop

```

Here's my xorg.conf;
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1440+0, DFP: nvidia-auto-select +0+124"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Thanks!

---

### Post by danduq on 2010-06-30
Oh, I forgot to add, I completely removed OpenOffice and all mention of it I could find. I then re-installed it via the Ubuntu Software Centre and added all the Human theme stuff via Synaptic, and it still borks.

---

### Post by danduq on 2010-06-30
I have just completely removed OO again and installed from the tarball as described in this thread - [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Still causes my screen to go funky.

---

### Post by danduq on 2010-06-30
Well, I cleared out my xorg.conf, restarted x, re-instated the nvidia driver, restarted x, set up my monitors using nvidia-settings, restarted x. Everything is back to how it was before.

OpenOffice still breaking on accoasion. The rendering in the application is patchy too, see the attached screenshot - I have pixellated-out the contents of the file, but you can see rendering issues in the cell labels and menus.

Any help greatly appreciated at this point!

---

### Post by danduq on 2010-07-07
Can anybody help with this? I don't know where to go from here.

I tried going into the OpenOffice options to change the memory settings, but the dialogue boxes are utterly unreadable (see screenshot).

If anyone has any suggestions, please?!

---

### Post by scohar70 on 2010-07-19
I am having the same problem after upgrading to Lucid 10.4.  OpenOffice crashes on files opened over sshfs (fuse) mounts.

---

### Post by danduq on 2010-10-27
Well, I finally fixed this... By installing Maverick from scratch.

So I guess something in previous config was screwing up the video in certain applications. The system had only been upgraded the last few times, so I decided a full-on clean install was required (also because I wanted to switch to ext4 and a separate encrypted home partition).

---

