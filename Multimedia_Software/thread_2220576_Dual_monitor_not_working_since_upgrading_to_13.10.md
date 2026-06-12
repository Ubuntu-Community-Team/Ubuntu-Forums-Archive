---
title: "Dual monitor not working since upgrading to 13.10"
date: 2014-04-28
forum: Multimedia Software
---

### Post by hojjat on 2014-04-28
I upgraded a 12.04 LTS to 12.10 and then to 13.10. Once I upgraded to 13.10 I had some issues with the driver (the nvidia drivers were installed and caused a blank screen after logging in). I fixed it by removing the nvidia drivers. In that process I think my video config files were modified, so now I've lost my dual monitor capability.

This is a Radeon 4xxx HD series graphical card, with two DVI cables each connecting to one Dell monitor. It worked perfectly in 12.04 and 12.10. Right now, when I go to  System Settings > Displays  it only detects one display, named "Built-in Display" (it used to be able to detect two displays, named Dell XX where XX was their size in inches.

Since video drivers is not my strong suit, I thought I should ask here before trying to modify anything again. Any advice on how to make this work (i.e. make my OS detect the two displays) is highly appreciated. Should I delete xorg.conf for example?

---

### Post by hojjat on 2014-04-28
The answer was what I had gussed: I had to delete /etc/X11/xorg.conf

---

