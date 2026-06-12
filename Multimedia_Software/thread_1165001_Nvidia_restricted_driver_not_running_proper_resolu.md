---
title: "Nvidia restricted driver not running proper resolution"
date: 2009-05-20
forum: Multimedia Software
---

### Post by lrrodrig on 2009-05-20
I've just installed 9.04 from scratch. The machine previously ran 8.04. The video card is an Nvidia 62xx and the display is a Hyundai L90D+. Normally, this display runs 1280x1024x32bpp under Windows and under 8.04. Under 8.04 it won't go over 1024x768.

I'm running the restricted mode driver Ubuntu offered me during my first login. I tried to use the Nvidia control panel to adjust the resolution, but it refuses to let me. I decided to get all low-tech, crunchygeek and hit up /etc/X11/xorg.conf, and discovered it to be nearly empty, but for a suggestion I should leave it that way.

I did try specifying monitor details and specifying a modeline, but that failed.

Can anyone offer any suggestions?

---

### Post by renzokuken on 2009-05-20
one option would be to let the nvidia driver build the xorg.conf for you ..... although thinking about it, i've only ever done that when installing the latest driver from the nvidia website, not using the restricted drivers one

---

### Post by lrrodrig on 2009-05-20
I'd given that a thought too. Since the autobuild depends on having a good EDID from the display, I'm out of luck. Though now that you've made me start thinking that way, I wonder if my kvm switch might be in the way? Tomorrow evening I'll yank that out of the chain and retry the detection.

€hanks. :D

---

### Post by lrrodrig on 2009-05-21
Well that did get me a bit further: with the KVM out of the way, the driver will let me go all the way to 1152x864 (still not the 1280x1024 it *should* be). I'd be fine with that, were it not for the fact that the Windows box manages to drive the display at full resolution.

Given that the KVM is analogue and not digital, the panel settles with the picture in slightly different locations and I have to hit the autocalibrate every time I switch between machines.

Is there any special reason why the driver would continue to auto configure the driver and ignore the modelines I added to the xorg.conf? It isn't throwing any errors in the log file (Well beyond the errors about cyrillic being missing, etc).

---

