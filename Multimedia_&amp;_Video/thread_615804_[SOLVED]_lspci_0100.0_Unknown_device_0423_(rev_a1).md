---
title: "[SOLVED] lspci 01:00.0 Unknown device 0423 (rev a1)"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by carlinuxlearner on 2007-11-17
Can't install Nvidia driver because "lspci" isn't detecting my device. Here's what "lspci | grep VGA" says "01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0423 (rev a1)"
How do I fix this?

C@RL

---

### Post by carlinuxlearner on 2007-11-17
Never mind, figured it out. "sudo update-pciids"

C@RL

---

