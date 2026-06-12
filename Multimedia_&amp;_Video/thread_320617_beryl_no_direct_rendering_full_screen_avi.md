---
title: "beryl no direct rendering full screen avi"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by sivnik on 2006-12-17
well i have nvidia, i have installed the drivers, i have installed beryl and xgl, and everything works fine.
The problem is that in glxinfo it says "direct rendering: No"
and when i want to see a video in full screen the cpu is 100% and the video plays slower...

i guess the problem is direct rendering, what can i do???

---

### Post by x64Jimbo on 2006-12-17
have you turned on direct rendering in your xorg.conf?

---

### Post by sivnik on 2006-12-17
i have this:
    > Option         "RenderAccel" "true"  
in the screen section...
is it something else?

---

### Post by x64Jimbo on 2006-12-17
Try adding this:
[SIZE=-1]Option "DRI" "true"
[/SIZE]to your xorg.conf under Section "Device"
Make sure that you restart after you've changed this.

---

### Post by sivnik on 2006-12-18
i did that, but the problem remains... :S
(but you opened my eyes :P, i didn't have load dri in the section module, its better now, but i still have the problem with the full screen videos -thanx)

---

