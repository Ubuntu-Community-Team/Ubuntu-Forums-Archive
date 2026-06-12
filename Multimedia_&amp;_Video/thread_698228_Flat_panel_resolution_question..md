---
title: "Flat panel resolution question."
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by Baxter001 on 2008-02-16
I know this is a boring a very common query so apologizes in advance.

I have an LG Flatron M2343A Monitor/Tv connected to a an Nvidia GeForce4 graphics card via DVI connection, the trouble is that I know that the native resolution of this monitor is 1360x768 16:9 aspect ratio, I know that the graphics card and the monitor support this resolution,  but I can't seem to get this option to appear in the Screen Resolution Dropdown, I think the problem may be that the native resolution isn't be detected correctly because when i run "sudo nvidia-settings" it tells me the native resolution is 1280x1042 when i know that this is definitely incorrect, I did read that in some cases the detection of the native resolution has to be forced by an option in the xorg.conf, is there a reverse method whereby i can manually assign the correct resolution?

Almost bald now...Please help. :)

---

### Post by Baxter001 on 2008-02-16
"sudo dpkg-reconfigure -phigh xserver-xorg" brings no joy either.

---

### Post by hyperair on 2008-02-16
Have you tried using nvidia-settings? That usually works when it comes to these resolution issues.
EDIT: my bad, I didn't read the above post correctly. >.< I'll post back if I think of something.

EDIT: Please post your /etc/X11/xorg.conf file.

---

### Post by Baxter001 on 2008-02-16
Ah rubbish, after this being a major thorn in my side regarding converting to linux for months  find that sometimes the old ways are the best, by that I mean switching to VGA rather than DVI cable "sudo dpkg-reconfigure "phigh xserver-xorg" again and restarting fixes it all, perhaps it's worth noting if people have a choice of head to use that they try it with the VGA.

---

### Post by jelofson on 2008-03-05
> **Baxter001 said:**
> Ah rubbish, after this being a major thorn in my side regarding converting to linux for months  find that sometimes the old ways are the best, by that I mean switching to VGA rather than DVI cable "sudo dpkg-reconfigure "phigh xserver-xorg" again and restarting fixes it all, perhaps it's worth noting if people have a choice of head to use that they try it with the VGA.

I have had the same problems outputting to the 1360x768 resolution with DVI to HDMI. I have yet to find the solution. If I do, I will let you know.

---

