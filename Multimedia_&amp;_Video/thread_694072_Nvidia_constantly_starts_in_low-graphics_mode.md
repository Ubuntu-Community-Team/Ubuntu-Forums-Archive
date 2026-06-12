---
title: "Nvidia constantly starts in low-graphics mode"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by thebigbread on 2008-02-11
I have a Nvidia Geforce4 MX440-SE.i went to nvidia.com and downloaded, then installed the driver. now it starts up in low-graphics mode without hardawre acceleration. i noticed there is a nvidia-glx driver in the repostitories, but even after uninstalling the old drivers then installing nvidia-glx it still refuses to work.

---

### Post by overdrank on 2008-02-11
> **thebigbread said:**
> I have a Nvidia Geforce4 MX440-SE.i went to nvidia.com and downloaded, then installed the driver. now it starts up in low-graphics mode without hardawre acceleration. i noticed there is a nvidia-glx driver in the repostitories, but even after uninstalling the old drivers then installing nvidia-glx it still refuses to work.

HI and you could look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by thebigbread on 2008-02-11
for some reason i though envy was only for ATI?... obviously not.

ill uninstall the old drivers then try this.

---

### Post by thebigbread on 2008-02-12
I found the problem: i had installed the drivers from nvidia.com in runlevel 1.

They are supposed to install in runlevel 3, so i logged in normally, then when to the terminal and typed:

sudo /etc/init.d/gdm stop

this puts you in terminal mode and in runlevel 3, i installed them according to nvidias website and now it works perfectly.

---

### Post by mattalexx on 2008-05-16
This is a driver conflict. Disable the other one:

[LIST=1]
[*]Install the correct driver from [nvidia.com]("http://nvidia.com"). You have to exit Gnome first.
[*]In /etc/default/linux-restricted-modules-common, add "nv" to DISABLED_MODULES.
[*]Restart.
[/LIST]

I wasted the whole day trying in vain to fix this problem, that that worked. Here's where I found it:

[http://quail.southernvaleslug.org/webblog/archives/48](http://quail.southernvaleslug.org/webblog/archives/48)

---

### Post by superbiskit on 2008-05-30
Something to check: this happened to me because the automatic configuration came up with bad info for the HorizSynch rate.
That caused X to disqualify the high-res modelines.

I checked the horizontal and vertical frequencies in the Monitor manual and entered them manualy.

My monitor is an HP PAVILION M50 (IIRC -- I'm not at home).

---

