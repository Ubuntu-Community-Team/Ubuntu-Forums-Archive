---
title: "Ati driver messed up"
date: 2009-01-31
forum: Multimedia Software
---

### Post by Baby Boy on 2009-01-31
To cut the long story short:

-saw the thread in the Community Caffe about the new Catalyst 9.1 driver
-installed on my own, possibly overlooked an important step or did something wrong; had deactivated the default driver via Hardware Drivers beforehand
-couldn't enable Compiz ("Desktop effects could not be enabled" after some screen flickering)
-uninstalled the driver by doing something in /usr/share/ati (installation instructions that came with the drivers)
-went back to installing drivers via Hardware Drivers
-after a restart, a message greeted me listing three options (rollback changes, low-graphics mode and one other)
-Compiz doesn't work

How do I *clean* this mess up and restore the drivers to the default ones?

---

### Post by Baby Boy on 2009-02-01
Anyone, please? I didn't think this was that complicated...:(

---

### Post by ubersolid on 2009-02-01
run ```
sudo aticonfig --initial
``` and if that fails, try removing the xorg.conf file: ```
sudo rm /etc/X11/xorg.conf
```
Removing the file should tell X to use the ati or radeon driver, and you should be able to get to tour desktop then.

---

### Post by Baby Boy on 2009-02-02
Oh but I can get to my desktop, install the default drivers via Hardware Manager, even watch videos, I just can't enable Compiz again. So I'd say that takes some cleaning up of the drivers as evidently some of the 9.1's files are conflicting with default drivers or something.

---

### Post by Baby Boy on 2009-02-03
Last call for help guys...

I've done as ubersolid suggested, reinstalled the default Ati drivers and got to this situation right here:

-everything seems to be working but the Compiz: videos, games...
-no ati folder in usr/share/ati

And yet I continue getting the "Desktop effects could not be enabled" message even though it worked well when I first installed Ubuntu. It would just be a major PITA if I had to reinstall only for this now that I've got a nice set up (I'm too lazy for it anyway).

---

### Post by Baby Boy on 2009-02-03
Well I'll be darned, I had the Metacity Compositing feature on in Ubuntu Tweak I have recently installed. Having turned that off, Compiz works fine. :)

---

