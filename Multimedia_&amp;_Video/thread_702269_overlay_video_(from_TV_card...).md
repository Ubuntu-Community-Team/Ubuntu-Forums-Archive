---
title: "overlay video (from TV card...)"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by ptrxyz on 2008-02-20
Hey there :)

I have just installed Gutsy Gibbon (Gnome window manager) and nearly everything works good! I got the desktop effects running, installed fglrx driver for my ATI Radeon X1600, and installed latest drivers for my TV-card (Pinnacle PCTV Stereo). I am sure that its the right driver and set it up correctly (since i get correct sound + video in tvtime). But it seems that there is a problem with overlay. in XawTV i can set "capture" to "Overlay" -> bang, black screen. If i set it to "grapdisplay" it works. But grapdisplay is not what i want since it uses CPU too much. Is there a way to make overlay work? do i need any special dirvers? I already installed libxv1, v4l and v4l2 without any success.

Does someone of you know some hint? Please help me..... :(

Ah, i forgott to mention, that i already put these files in my xorg.conf (at the right place):

# === Video Overlay for the Xv extension ===
Option "VideoOverlay" "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
Option "OpenGLOverlay" "off"

---

### Post by erginemr on 2008-02-20
I have also sured XawTV and Zapping (Gnome TV app), both of which refused to work in overlay mode. So, I believe this is a limitation of either Xorg, v4l or NVidia (the one I am using). So, I will also eavesdrop on your thread.

On a side note, you should give a try to **TVTime **as well, which is a superior TV application. And to **GnomeRadio **if your card can also play FM radio.

---

### Post by ptrxyz on 2008-02-20
Afff...this means no TV overlay in Gnome? maybe it works in KDE? Does anyone know? Or maybe some other linux-pros here who might have an idea who to get TV overlay work in gnome and gutsy? C'mon, even MS Windows supports tv overlay XD

---

### Post by ptrxyz on 2008-02-22
bump. Still got the problem.

---

