---
title: "mpd won't start"
date: 2010-12-05
forum: Multimedia Software
---

### Post by Neon612 on 2010-12-05
After turning my laptop on and trying to run ncmpc, gmpc, or sonata, the clients start up without any problems except for the fact that they cannot recognize the mpd DB as running.

When I try starting mpd I get:
```
listen: Failed to listen on *:6600: Address already in use
Aborted
```

I have to stop mpd by running:
```
sudo /etc/init.d/mpd stop
```

before I can start it up again.

Is there anyway to get mpd to start up right the first time, maybe even at startup?

Thanks.

---

