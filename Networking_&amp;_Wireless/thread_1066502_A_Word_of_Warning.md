---
title: "A Word of Warning"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by 5BallJuggler on 2009-02-10
I have just spent the best part of 4 hours trying to get my network connection on my Acer Aspire One back up and running, and I don't know why it went down in the first place.

I have re-ran the set up to get Atheros cards working to no avail, 

I have changed countless settings in order for this to work, all to no avail.

I have restarted the netbook........LOTS

and you know what fixed it?

Shutting down the netbook completely.

So...
I have a question...

When you reboot, are there things that stay resident in the memory that only disappear when you do a complete shutdown? 

If so what?

If not, then what could my problem have been? it has never failed to connect in all the times I have booted up previously, and know when I reboot it works fine.

When I was checking things, the "sudo lshw -C network" command was telling me that the AR242x (Atheros) was DISABLED.

ie.
*-network DISABLED
description Wireless interface

Now I've got
*-network
description Wireless interface

---

### Post by Iowan on 2009-02-11
> **5BallJuggler said:**
> When you reboot, are there things that stay resident in the memory that only disappear when you do a complete shutdown?  I've read of similar problems when restarting from Windows to Ubuntu - ethernet card is non-responsive unless machine is powered completely down.

---

### Post by Tarvok on 2009-02-11
I remember, back in my earliest high school CSci classes, being told that there were problems that a warm boot cannot solve at times, but a cold boot can. IIRC (and it's been a LONG time) the RAM doesn't actually lose its state for something like ten or eleven seconds after losing power. This can, at times, affect things you are trying to reset by resetting the machine if the RAM doesn't remain depowered for that period of time. Probably your machine was, for some reason, reading a residual state that only went away when you cold booted it.

---

### Post by 5BallJuggler on 2009-02-11
Thanks for the explanation.

---

### Post by udimtu on 2009-02-11
my issue is the other way around. everytime i go to ubuntu.. its always connected. but if i switch back to windows (without the cold boot), LAN is not connected. only tried the cold reboot once though as ive only installed ubuntu last night.

---

### Post by lswb on 2009-02-11
I've seen similar things with various hardware would not reset to the same state from a warm boot vs. a cold boot. I also have an old laptop that dual boots Win XP and linux. Windows will not run after a warm reboot if linux was running first. It needs a power off shutdown first.

---

