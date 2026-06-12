---
title: "xorg.conf: Can't get TVOutFormat Component working"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by Levander on 2007-11-15
I'm using Ubuntu Gutsy, have a Leadtek A6200 nvidia based graphics card, and a Samsung Syncmaster 215TW monitor.

I got TV Out working pretty quickly for S-Video.  I've been working for days on Component, nothing.  I'm trying to get my desktop setup so that there are two monitors working.  One for a regular desktop, and another for television.  

Actually, both monitors are the same physical monitor.  It's just one Samsung Syncmaster 215TW that has a bunch of different inputs on it, including DVI, S-Video, and Component.  I press a button on the monitor to cycle through them.

On the back of my video card, I've got a S-Video/HDTV port.  There's this adapter that comes with the card that plugs into the card.  Hanging out the other side of the adapter are ports for an S-Video cable and a Component cable.

I hook the S-Video cable into the adapter on the video card and into the monitor, I have this in xorg.conf as my Screen section for my monitor:

```

Section "Screen"
        Identifier      "Television Screen"
        Device          "Television Device"
        Monitor         "Television"
        DefaultDepth    24
        Option          "TVOutFormat" "SVIDEO"
        Option          "TVStandard" "NTSC-M"
        SubSection      "Display"
                Depth           24
                Modes           "nvidia-auto-select"
        EndSubSection
EndSection      

```

and it works fine.

To try to get component TV Out working, I change two lines in that Screen section:

```

        Option          "TVOutFormat" "COMPONENT"
        Option          "TVStandard" "HD480i"

```

I leave the rest of xorg.conf alone.

Then, I unplug the S-Video cable, and plug a component cable into the adapter on the back of the video card and into the monitor, restart gdm, login, and I get a fine display on the regular monitor, and nothing on the television, just a black screen.

I'm thinking the problem is that somehow, the video card just isn't being put into some kind of COMPONENT or HDTV mode, because none of the documented HD modes are listed in this part of Xorg.0.log even when TVOutFormat is set to COMPONENT:

```

(--) NVIDIA(1): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): TV modes supported by this encoder:
(II) NVIDIA(1):   1024x768; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI,
(II) NVIDIA(1):     PAL-N, PAL-NC
(II) NVIDIA(1):   800x600; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   720x576; Standards: PAL-BDGHI, PAL-N, PAL-NC
(II) NVIDIA(1):   720x480; Standards: NTSC-M, NTSC-J, PAL-M
(II) NVIDIA(1):   640x480; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   640x400; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   400x300; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   320x240; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(II) NVIDIA(1):   320x200; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(1):     PAL-NC
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(--) NVIDIA(1): Samsung SyncMaster (DFP-0): Native FlatPanel Scaling is
(--) NVIDIA(1):     supported

```

Should I just be able to change S-Video to Component and NTSC-M to HD480i and get Component video working?

I know I've got the hardware that supports HDTV out.  The manual for the graphics card has pages on how to get it working under Linux.  So, does the fact that Xorg.0.log is not printing out any HDTV modes as being supported by my TV encoder really just mean that the nvidia driver isn't supporting it with my TV encoder?  That's what I'm thinking, but it is an NVIDIA TV encoder, so I would think the nvidia driver would support all modes of their own tv encoder?  

Or, am I reading that message wrong?  Maybe there's just something I have to do to put the driver into HDTV mode??

---

