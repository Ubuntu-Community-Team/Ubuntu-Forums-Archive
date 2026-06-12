---
title: "VNC access to my backend stopped working--how to reset it?"
date: 2013-10-29
forum: Mythbuntu
---

### Post by ceenvee703 on 2013-10-29
This is with a fairly new install of a backend-only server, running 0.27.

VNC was running great, which was highly useful as I don't have a monitor hooked to the backend. Now, however, when I try to connect to the backend, all I get (via TightVNC) is "Failed to connect to server."

I've rebooted with no change. I'm not even sure what mythbuntu's default vnc server is, or where to check for logs. or what service to kill/restart, or basically where to start. It's a real hassle to hook a monitor to this machine, so connecting via VNC would really help. I can ssh in to the machine no problem.

Any help would be really appreciated. Thanks.

---

### Post by GaryP2 on 2013-10-30
On my backend/frontend system in my theatre room, if I don’t have have my Onkyo amplifier turned on when I reboot the system(connected via HDMI), the system doesn’t detect a monitor and I’m never able to VNC in. If it’s on when I reboot, I can then turn it off and it continues to work. I think it’s because the Xserver desktop environment is never started without some sort of display attached.

You may wish to explore this thread for help.

[http://ubuntuforums.org/showthread.php?t=1297815](http://ubuntuforums.org/showthread.php?t=1297815)

---

### Post by ceenvee703 on 2013-10-31
OK, this makes sense. 

Well, it doesn't make sense since VNC is ideal for headless systems, yet it gets mad when you don't have a monitor attached. But it makes sense why it was working (I had a monitor hooked up for initial setup in place) but doesn't now (I've rebooted since then).

I tried the fix mentioned on the first page of that thread but it didn't work. However, now I see that subsequent pages have other fixes that might work. And now that I know to search for "headless VNC" I might have luck finding other solutions. 

Thanks very much for your reply.

---

