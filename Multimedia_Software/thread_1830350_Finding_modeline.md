---
title: "Finding modeline"
date: 2011-08-21
forum: Multimedia Software
---

### Post by pgpoulsen on 2011-08-21
Hi

I have an Asrock 152D with a NVidia ION graphics chip. It is connected to my TV using HDMI<->HDMI and I only get a black screen when X comes up. There are lot of posts on this issue and they all say that it is a modeline problem.

Now, if I attach my monitor to the DVI, the TV works (the monitor is black *shrug*). I have started X with -logverbose 6 to get the modeline that the monitor uses (as I assume they should work with the TV as they do the magic trick to get the TV working), however, I'm completely lost when it comes to understanding the log file. Any chance there are some X experts that can help me out and explain to me what I should write in my xorg.conf to get it working?

My log file is here: [http://pgpoulsen.dk/startx.log]("http://pgpoulsen.dk/startx.log")

Thanks in advance.

Yours
/peter

---

### Post by BicyclerBoy on 2011-08-21
The TV HDMI monitor is returning valid EDID data (modelines).

There is an internal contradiction with 1920x1080p60 & hort freq range.
The X server is ignoring the hortizontal freq error & the mode is set as valid.

So it is possible your TV can not actually support 1080p60..but..

The error is:
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1. (EE) NVIDIA(1): No display devices found for this X screen.

You could try 
Option "ConnectedMonitor" "DFP-1"
possibly just[FONT=Verdana]
[/FONT]Option "ConnectedMonitor" "DFP"

Are you using the PC input HDMI or the digital video AV inputs ?
This could change the EDID & overscan settings..

---

