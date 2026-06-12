---
title: "Nvidia Advanced Timings"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by starfry on 2007-10-17
Hello,

How do I get to the "Advanced Timings" dialog of the Nvidia drivers?

On Windows there is an "Advanced Timings" button, but I can't see the same on the Linux version.

Or, is there a config file I can edit by hand?

Many thanks.

---

### Post by dabl on 2007-10-17
> **starfry said:**
> Hello,

How do I get to the "Advanced Timings" dialog of the Nvidia drivers? 

You don't, AFAIK.

> 

On Windows there is an "Advanced Timings" button, but I can't see the same on the Linux version.



The Windows driver is one thing (for the very large mass market), and the Linux driver is another thing  (for the few, the proud, the fearless, the advanced-timing impaired ....) :)


> 

Or, is there a config file I can edit by hand?



I suspect that's a "YES", but I only know how to enable overclocking, which you do by adding the following line in your "Devices" stanza of /etc/X11/xorg.conf:
```

Option         "Coolbits"         "1"
```


Good luck with it!  :)

---

### Post by starfry on 2007-10-23
Thanks, I'll take a look at the "coolbits"

---

