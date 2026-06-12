---
title: "Lost screen resolution"
date: 2008-12-12
forum: Multimedia Software
---

### Post by carlosjoan91 on 2008-12-12
Hi, I'm running Ubuntu 8.04 Hardy Heron, and a Dell Dimension E521, a friend of mine used the computer and he saw the updates available icon and ran it, but said no too the license of the jre, so the updates halted there, I told him to leave it like that and i would finish updating later, anyway, when i rebooted, the drivers for my GForce 6150 were gone (and with that i lost my resolutionto 640x480), then i thought maybe if i finish installing updates, so I did and reooted, the i recovered the drivers but not my screen res, and if i go to the configuration menu (both the nvidia one and the ubuntu one) the maxium res they let me choose is 640x480,(funny thing is it detected my monitor, and even compiz is working but not the maxium resolution) I wanna know if i can set it manually in xorg.conf and if so, how, the resolution I want is the one usually after 860,  think is 1048 or something like thata, I don't remember exactly.

Ps.: I'm really sorry if this has been posted before, but I searched, and in the current status of my screen couldn't read many posts, sorry

---

### Post by wolfen69 on 2008-12-12
in terminal: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot or restart x.

---

### Post by carlosjoan91 on 2008-12-12
Thanks a lot, that fixed it for me, however now i have a smaller problem, if i leave compiz activated, my windows lose the title bar, along with the close, minimize, maximize buttons, and disappear from the taskbar, I tried selecting Compiz as desktop manager, and GTK Windoews decorator for decoration, bu8t that doesnt work either, I have to select metacity instead of compiz for it to work, any idea of what might it be? Thanks

---

