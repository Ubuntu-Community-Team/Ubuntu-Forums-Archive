---
title: "My HDMI display will not standby, how to force DVI?"
date: 2009-07-03
forum: Multimedia Software
---

### Post by zurcherart on 2009-07-03
Is there a command I can issue from the command line to force the display drivers to operate in DVI mode instead of HDMI mode?

Or is there and xorg configuration that will accomplish this?

(I prefer a command so I can put it into a script--but at this point I'll accept any solution.)

Background:
I am running Jaunty 9.04 latest patches.
I have an NVidia 8400 GS graphics adapter.
I am using the recommended Nvidia 180 drivers.
My monitor is connected via a DVI-HDMI cable (which appears to be the only option for connection--so swapping cables is not a solution).

My wide screen HDMI capable monitor will not enter standby.  Instead of powering down to standby it displays a shocking electric blue as soon as the computer stops sending it signals.  Apparently it doesn't recognize the standby signals and searching for an HDMI source.

With DVI signalling there is no problem.

However. the installed Nvidia drivers/card seem to automatically detect that the monitor is HDMI capable then automatically provides HDMI signalling.

When going to standby the monitor is still expecting HDMI signalling and will not standby.

But, while the system/Ubuntu is starting up or shutting down the adapter provides DVI signalling.  While the monitor is expecting DVI signals everything works as I'd expect.  As soon as X and/or the Nvidia drivers reach a certain state during startup the adapter switches to HDMI signalling and then the problems begin.  (Related issue, the sound card is also disabled when the NVidia drivers switch to HDMI signalling.) 

If there is a command (or config) to force the adapter back to DVI signalling so I can work around this problem?  Then I can create my own script to send the monitor to standby after switching to DVI if that's what needs to be done.

Thanks in advance for any help!

---

