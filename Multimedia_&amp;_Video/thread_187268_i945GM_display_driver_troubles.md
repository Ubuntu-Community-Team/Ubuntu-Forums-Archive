---
title: "i945GM display driver troubles"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by charles.figura on 2006-06-02
Hi -

This is extended from [http://www.ubuntuforums.org/showthread.php?t=160679](http://www.ubuntuforums.org/showthread.php?t=160679)
thought I'd see if anyone on a different machine has seen this.

I've got a Dell D620 with a 1440x900 display and a i945GM display driver.  I've been running Dapper pretty successfully for about three weeks now, and I've been keeping the system upgraded.

I've noticed several odd things about the i945, and I've seen similar behavior on the i8xx that was on a Vaio B100 laptop.  The first thing is that when I try to use most of the GL screensavers, I only get display on the top 2/5 of the screen or so.  The rest of the screen is on but black.  There are a couple of GL screensavers that function properly - space and KPendulum, but the rest (Gravity, Solar Winds, Flux, etc.) give this weird upper 2/5 deal.  The display works pretty well the rest of the time, glxgears gives about 1800fps, which I'm happy with.  I'd say 'hey, it's just a screensaver, wo cares?', but I suspect that there's goofyness going on with the driver that may be reflected in the other problem.

The second problem is that when I try to suspend, the display doesn't wake up.  The back light doesn't turn on, the whole thing stays dark.  Keyboard seems active (lock lights toggle appropriately) but I can't see what I'm doing.

Third deals with compiz/XGL.  I tried installation, but I'm not getting any window frames or anything.  I can see some prettiness, but it's completely unusable.

So I don't know that these three items are connected in any way, except that they might all have to do with the display driver (the first two more than the last, perhaps...)

Has anyone else with the i8xx or i9xx chipset seen this behavior?  Any ideas for a fix?

---

