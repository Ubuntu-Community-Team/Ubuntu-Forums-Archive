---
title: "Glxgears"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by Jaxilian on 2006-09-16
I can't get any results from running:

```

glxgears

```

It just starts and run the gears with decent speed. It looks good, but no result in the terminal window.

any ideas? did I miss some switches to the command?](*,)

---

### Post by mitch.c on 2006-09-16
> **flodis said:**
> I can't get any results from running:

```

glxgears

```

It just starts and run the gears with decent speed. It looks good, but no result in the terminal window.

any ideas? did I miss some switches to the command?](*,)
FWIW..

I'm fairly new to ubuntu, and noticed the same thing immediatley after installing. X was configured using the stock ati driver. Then earlier this week I got around to installing the fglrx driver and guess what... results are reported to terminal when running glxgears!

Funny, I used Gentoo before and glxgears wrote to terminal with either driver. I'm not sure what the difference is.

---

### Post by Lord Illidan on 2006-09-16
Try ```
glxgears -printfps
```

---

### Post by Jaxilian on 2006-09-16
> **Lord Illidan said:**
> Try ```
glxgears -printfps
```

THANKS!:D :KS 

~$ glxgears -printfps
11608 frames in 5.0 seconds = 2321.586 FPS
11762 frames in 5.0 seconds = 2352.229 FPS
11751 frames in 5.0 seconds = 2350.008 FPS
11748 frames in 5.0 seconds = 2349.429 FPS
11761 frames in 5.0 seconds = 2352.101 FPS
11761 frames in 5.0 seconds = 2352.045 FPS
11760 frames in 5.0 seconds = 2351.942 FPS
11755 frames in 5.0 seconds = 2350.943 FPS
11755 frames in 5.0 seconds = 2350.839 FPS
11755 frames in 5.0 seconds = 2350.817 FPS

not so good, but I am happy anyways.
I am using ATi X600 mobility

---

