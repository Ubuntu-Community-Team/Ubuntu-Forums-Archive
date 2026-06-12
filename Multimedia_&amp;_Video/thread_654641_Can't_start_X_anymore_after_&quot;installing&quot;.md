---
title: "Can't start X anymore after &quot;installing&quot; nvidia's latest driver"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by vexorian on 2007-12-31
I am using feisty not gutsy so I don't have bullet proof X.

I installed nvidia's drivers from their homepage, and things seemed to go ok, the problem is that after restarting X cannot start, it says that the nvidia kernel module version is not the same as the one in xorg.conf, which is strange since the driver installer compiled a kernel module at the same time as configuring its stuff.

Right now what I do to begin ubuntu correctly is see the X errors, install the nvidia driver again and do a startx , it seems to work fine and even though I am not sure if it is using the driver it looks so and I can run nvidia-settings . But once I reboot X begins to complaint about the mismatch again, looks like there is some rogue kernel module that refuses to uninstall.

Any insight?

---

### Post by taurus on 2007-12-31
Any reason why you don't want to use the nvidia driver from the repos?  What model of nVidia card do you have?

---

### Post by vexorian on 2007-12-31
Yeah well, I was trying something. But regardless I fixed this problem by uninstalling nvidia-glx and disabling "nv nvidia_new" in the restricted manager configuration file.

This was hard, and I can confirm it wasn't worth it.

---

