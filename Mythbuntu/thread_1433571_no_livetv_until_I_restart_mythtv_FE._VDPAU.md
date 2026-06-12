---
title: "no livetv until I restart mythtv FE. VDPAU?"
date: 2010-03-19
forum: Mythbuntu
---

### Post by My Name on 2010-03-19
I'm sure I've read about this problem before, but I can't find the threads.
On a freshly rebooted remote frontend, livetv will just display a blank screen. I then need to kill it and restart mythtv. hey presto livetv works. This happens every time so I am confident it can be fixed.
if someone can point me to a fix I would be grateful.
I'm at work as well and can.t get to any logs.

I am using an acer revo, using vdpau normal playback profile if it helps

---

### Post by lank23 on 2010-03-19
what does the logs say
```

/var/log/mythtv/mythfrontend.log 

```

and

```

/var/log/mythtv/mythbackend.log

```

---

### Post by My Name on 2010-03-21
hmmm, seems that a reeboot of the backend has fixed it ;)

---

