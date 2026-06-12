---
title: "Changing Video Cards on Working System"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by pmgant on 2006-09-14
I have a hardware fault on my video card  (built in to the Intel chipset) so I want to install a new NVidea card. As all the video drivers, video settings and X Windows settings are for the Intel chipset I'm assuming that X will crash as soon as I make the hardware change.

How do I change over the drivers and X Windows settings on a working system?

PM Gant

---

### Post by yota on 2006-09-14
When the system starts with the new graphic board, probably will complain that is not able to launch Xserver.

Just switch to a text terminal (press ctrl+alt+f1) and log on.
Then issue this command to reconfigure xorg, a wizard will guide you.
```

sudo dpkg-reconfigure xserver-xorg

```

---

