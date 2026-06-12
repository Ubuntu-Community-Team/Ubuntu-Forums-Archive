---
title: "No picture on HDTV after reboot"
date: 2008-09-09
forum: Mythbuntu
---

### Post by tshannon on 2008-09-09
I've got my mythbox hooked up to a Philips LCD HDTV through a DVI to HDMI connector on my GeForce 5200.

I've never had too much trouble with it, and have gotten 1080i working on the nvidia card, but for some reason when I take down the mythbox, and unplug everything (for instance to install an additional hard drive), I can't get a picture on my tv.  It looks like it sits there and tries to find the signal for a bit, but then fails.  If I VNC into the box, I get a 1920x1080 vnc image, but not on the tv.

The last time this happend, it eventually just worked, and I have no idea what I did to make it work again.  This last time, I can't get it to come back.  I've uninstalled the nvidia drivers and reinstalled them, and nothing changed, which makes me think it's something with the TV.  

Has anyone seen anything like this?

---

### Post by stevanbt on 2008-09-10
Hi,
Have you checked /etc/X11/ for a backup copy of you xorg.conf?  If something did change the config it may have created a backup copy before it saved the change.

Thanks, Steve.

---

### Post by tshannon on 2008-09-10
The last time my xorg.conf was modified was weeks ago, and I even tried using that backup, which looked exactly like my current xorg.conf, and still no picture.

---

