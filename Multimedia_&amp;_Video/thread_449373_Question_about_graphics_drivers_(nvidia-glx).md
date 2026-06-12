---
title: "Question about graphics drivers (nvidia-glx)"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by PartisanEntity on 2007-05-20
I would like some clarification concerning the nvidia-glx package, let me give you some background info:

In Edgy, I used Alberto Milone's Envy script to install the latest Nvidia drivers, namely 9755. Then I upgraded to Feisty, in Feisty I was informed that there were updates available for the nvidia-glx package however I was offered the old Nvidia drivers, namely 96xx.

I ignored the update icon therefore since I wanted to keep my newer drivers. However yesterday in a moment of brightness I deleted the nvidia-glx package thinking I would not need it since I have the latest drivers. Of course after rebooting X server did not work.

So my question is as follows, are all Nvidia drivers installed *inside* the nvidia-glx package, i.e. **even** if I use the Envy script? And is that why X server could not load after I deinstalled nvidia-glx?

I was always under the impression that nvidia-glx was itself a packaged driver and that if I used the Envy script the driver inside nvidia-glx would be ignored in favour of the newer one?

---

### Post by x64Jimbo on 2007-05-20
The package is a metapackage. it includes several packages. You can get your desktop back by reinstalling the nvidia-glx package at the command line:
sudo aptitude install nvidia-glx

---

### Post by PartisanEntity on 2007-05-20
Thanks for your input, my question wasn't about getting my desktop back though as I did that already.

---

### Post by x64Jimbo on 2007-05-20
The reason it would not load is because your xorg.conf file was telling the X server to use a driver module that did not exist. When you uninstalled the nvidia-glx package, it uninstalled the nvidia Xorg driver with it. The fact that you previously used a script doesn't make a difference - it's only the most recent version of the package that you have installed.

---

### Post by PartisanEntity on 2007-05-20
> **x64Jimbo said:**
> The reason it would not load is because your xorg.conf file was telling the X server to use a driver module that did not exist. When you uninstalled the nvidia-glx package, it uninstalled the nvidia Xorg driver with it. The fact that you previously used a script doesn't make a difference - it's only the most recent version of the package that you have installed.

Thanks very much, that is exactly what I wanted to know.

---

