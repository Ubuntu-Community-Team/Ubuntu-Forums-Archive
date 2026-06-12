---
title: "Video playback only solid colors or multicolor pattern fixes itself on reboot."
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by radradrobotanks on 2008-01-19
Hello,

Occasionally when I fire up a DVD or watch live tv or a  tv recording in myth tv the image shows as either a solid color or a pattern of a few colors.

[IMG]http://i268.photobucket.com/albums/jj37/radradrobotanks/solidGreenDVD.png[/IMG]

[IMG]http://i268.photobucket.com/albums/jj37/radradrobotanks/multiColorDVD.png[/IMG]

A reboot fixes the problem.

It never seems to happen straight after a reboot. It seems to happen only after I've played another media file. It happens often but I can't seem to find anything that triggers it reliably.

I am using the proprietary nvidia drivers installed by the restricted driver gui tool.

The videos sound still works.

The mythtv OSD does not display when changing channels but when I hit exit the mythtv menus still display.

I hope thats enough info Thanks in advance :)

---

### Post by chrono13 on 2008-01-29
This has hit me too.

This is the bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455)

The most important detail:
> 
...this has been declined for Gusty.
Anyways, this bug seems fixed as nvidia-glx-new 169 was pushed into the Hardy repos today. I am marking this as 'fix released'.


So it is the nvidia drivers. Update them (envy perhaps?) or wait until Hardy : (

---

### Post by eye208 on 2008-01-29
You can work around this bug without reboot by switching to a tty and back to X (press e.g. Ctrl-Alt-F1, then Alt-F7).

I wonder why the driver update doesn't hit gutsy-backports. What is the purpose of gutsy-backports anyway? I received three updated packages of Gnome desktop games today. How about getting priorities straight?

---

### Post by chrono13 on 2008-01-30
Thank you very much for the tty workaround!

---

### Post by radradrobotanks on 2008-02-04
> **chrono13 said:**
> This has hit me too.

This is the bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455)

The most important detail:


So it is the nvidia drivers. Update them (envy perhaps?) or wait until Hardy : (

Whats the best way to update the nvidia drivers?

---

