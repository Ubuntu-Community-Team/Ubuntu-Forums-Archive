---
title: "NVidia 7200, no display on TV"
date: 2008-02-02
forum: Mythbuntu
---

### Post by RichardA on 2008-02-02
I've set up Mythbuntu, and it works really well... on my monitor.
I have an Nvidia 7200, a breakout connector and an S-Video to Scart cable, but I can't get any display on the (CRT) TV.
I've tried many of the xorg.cong options I've seen on the web, I can get the log file not to show any errors, but still no picture.

Not sure if this is relevant, but when I run "Screen and Graphics Preferences" to set the second screen as a clone of the first, the 'OK' button does nothing and 'Test ' is greyed out. Also, if the TV is connected on boot, I get nothing on the monitor.

Does anyone have an xorg.conf which does what I want? Or is this a hardware/cable issue?

---

### Post by gsrcrxsi on 2008-02-02
do you have the proprietary drivers installed? do you have the s-video output enabled?

---

### Post by RichardA on 2008-02-03
Proprietary drivers, yes.

S-Video enabled... do you mean something in xorg.conf like:

Option "TVStandard" "PAL-I"
Option "TVOutFormat" "SVIDEO"

.. or something else?

---

### Post by RichardA on 2008-02-03
Progress, sort of Instead of Scart, I plugged in to the composite input on the TV. I ran 'sudo nvidia-settings' and saw both displays be recognised for the first time. I set the displays to clone and saw a brief flash of something on the TV. That's the best I can get, though.

So I have issues with the Scart input on my TV?
How can I get a picture using the Composite input (I don't really want to use this, as it's at the front and my 18 month old son will unplug it, but if this is the best I can do..).

---

### Post by RichardA on 2008-02-04
I tried an S-Video cable instead of Scart, used nvidia-settings and saw a picture on the TV! It doesn't fill the screen, but I can mess about with overscanning and resolutions to fix that.

So it turns out the problem was either cables or my TV, not Mythbuntu...

---

