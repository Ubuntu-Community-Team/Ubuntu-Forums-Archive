---
title: "Loading Nvidia gamma by default"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by the_dark_light on 2007-09-23
I'm having a problem with the gamma setting on my nvidia card, using nvidia-settings

The tool works fine when adjusting the gamma settings, the only problem is that those settings aren't persistent.  Every time I log on, I have to load nvidia-settings again to get my old gamma back.  (After loading nvidia settings I don't need top make the adjustments again, they change automatically to the gamma settings I set)

It's not a big deal really, I was just wondering if there was a way to make the settings persistent so I won't have to load nvidia-settings

(failing that I can always add it to the programs loaded when I log in)

---

### Post by MCMcButtah on 2007-09-24
Have you tried running the config utility as root? That worked for me.

---

### Post by ahaslam on 2007-09-24
You have to make an executable script to run at boot for some options.

Use 'man nvidia-settings' to see what commands you need. Here's one that I use as an example:

```
#! /bin/bash
nvidia-settings -a FSAAAppControlled=0 -a FSAA=7 -a LogAnisoAppControlled=0 -a LogAniso=4 -a SyncToVBlank=1
```

Hope that helps.

---

### Post by ThrashJazzAssassin on 2007-10-09
To answer the original poster. The easiest way is to run this command at startup (preferences/sessions/new)
```
nvidia-settings --load-config-only
```

---

