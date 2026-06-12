---
title: "Can't stop the mythbackend"
date: 2009-03-09
forum: Mythbuntu
---

### Post by worldwidewebb on 2009-03-09
Having got Mythtv 0.21 running smoothly as a single frontend/backend setup the next stage of my PVR project was to reconfigure my setup to also allow connections from a Windows XP laptop running XBMC.

I changed all the obvious settings on the frontend/backend box e.g. replaced ip addresses with the real (static) ip address, updated mysql to allow connections...
This all went smoothly and I'm now able to stream recordings & live TV to the laptop :D

There is one problem. When I start the backend setup a message is displayed telling me that the server is still running (even though it's just said that it needs to stop any backend processes). This didn't happen before I tried changing my setup.

I've tried manually running '/etc/init.d/mythtv-backend stop', but this just tells me that there are no processes running even though I can see that there is one using 'pgrep mythbackend'!?!?

The only way that I can stop the backend process is using a 'kill -9 <process id>' command.

Can anyone offer any suggestions on why this is happening and what I need to do to fix it?

---

### Post by novellahub on 2009-03-09
Try running the command as root:

```
sudo /etc/init.d/mythtv-backend stop
```

---

### Post by worldwidewebb on 2009-03-09
Yep, I've been running mythtv-backend as root (sudo /etc/init.d/mythtv-backend stop)

---

