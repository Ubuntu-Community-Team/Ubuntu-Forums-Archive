---
title: "ghosts on my monitor"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by vvangelovski on 2007-08-26
Every time I install feisty on this machine the edges of windows, text and cursors have a ghost on their right side. It's like everything with edges is transposed a bit to the right. I didn't have this problem on other configurations but I also don't have this problem with other OSes on the same configuration.
My graphics card is GeForce 5500 FX and monitor 19" MAG innovision.
I installed the nvidia drivers but couldn't notice any improvement, the controls on the monitor don't help either.
Could this be an issue with Gnome or something else? Any suggestions?

---

### Post by kissg1988 on 2007-08-26
I'm not a monitor professional, but it may be a problem with the horizontal or vertical refresh rates. Check the manual of your monitor, and set the frequencies according to it.
Open a terminal, then type:

```
sudo vi /etc/X11/xorg.conf
```

Check the config file, look for something like this:

```
Section "Monitor"
        Identifier      "Generic monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection
```

Change the options "HorizSync" and "VertRefresh" to the values, you found in the manual. Once you set the correct frequencies, restart the X server, by pressing the Ctrl + Alt + Backspace keys together.

I hope, this will help you.

---

