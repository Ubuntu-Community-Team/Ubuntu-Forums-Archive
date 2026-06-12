---
title: "Rhythmbox crash"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by voided3 on 2007-04-28
Hello, when I play an audio file with rhythmbox, it crashes immediately. This is the terminal output when I run it:

```
 /bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found

(rhythmbox:5432): Rhythmbox-WARNING **: Couldn't find an x overlay
Segmentation fault (core dumped)
```

How should I go about troubleshooting this? Thanks!

---

### Post by voided3 on 2007-04-28
Whoops, never mind. I went through the plugin list and disabled everything but the iPod plugin and it is running smoothly. I assume it was either the album art or visualizer plugin, but I hope this helps someone!

---

### Post by maliath on 2007-05-14
It is the visualization plugin. As soon as I enable it, it crashes. Are you using an ATI vid card by any chance?

---

### Post by Daedalus on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151188](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151188) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Please, look at.

---

