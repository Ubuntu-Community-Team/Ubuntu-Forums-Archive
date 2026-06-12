---
title: "NVIDIA problems"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VMC on 2011-03-25
I have been sing the 3D proprietary drivers instead of the nvidia-current for a couple of weeks without issue.

I decided to make things interesting [I succeeded] and install nvidia's own driver "NVIDIA-Linux-x86_64-270.30.run". It worked but the graphics on Lbreakout2 was very unresponsive. so I then decided to try nvidia-current. That was no better.

After all that I wanted to go back to the 3D version. Its the best of the bunch. That's when all H broke loose. First no display. Then deleting "/etc/X11/xorg.conf" got me a display, albeit 1024x768, instead of the usual 1280x1024.

Where might I look to get back to the original 1280x1024 using 3D?

The monitor can't be changed above 1024x768 right now.

Interesting how ""NVIDIA-Linux-x86_64-270.30.run" runs Lbreakout2 very fast on Lucid. I'm guessing its the new xorg causing the slowdown.

Thanks for any help.

this is for future reference, as of tomorrow this will all go away, I just want to know where Linux keeps its video drivers stored or what folders to examine.

---

### Post by cariboo on 2011-03-26
The drivers themselves are in /lib/modules/<kernel version> in my case it's /lib/modules/2.6.38-7-generic/updates/dkms. The reason they are in that particular directory is the are created on the fly when a new kernel is installed.

**Note:** the above info only pertains to nvidia-current, the nvidia driver may be in a different directory.

---

