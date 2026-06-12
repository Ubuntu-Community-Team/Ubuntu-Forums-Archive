---
title: "All Multimedia stopped working"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by skotadi on 2007-10-03
Sound and video worked fine.  I installed libdvdcss2 so I could make a backup of a DVD using dvd::rip.  After rebooting, I think gstreamer is broken.  

Here's what happens:
1. I log in and the login sound plays as usual
2. I open a media player (gxine, totem, miro, etc)
3. most of them hang on startup.
4. if the program successfully loads (xmms, rhythmbox), it hangs when trying to play the video or audio (any format).  

I have no idea where to start.  I uninstalled libdvdcss2 but nothing changed.  Please Help!!

---

### Post by rsambuca on 2007-10-03
Start one of the programs from a terminal and then see if any error messages are spit out.

---

### Post by skotadi on 2007-10-03
I actually got everything working again by rebooting after uninstalling libdvdcss2.  But that means I can't rip my backups.  Does anyone know of a way to have my cake and eat it too?

thank you!

---

### Post by RomeReactor on 2007-10-03
Hi. Try running the problematic applications from the terminal (Applications->Accessories->Terminal), and post the output--if any--here. To run an application from the terminal, enter it's executable's name  (in this case, **totem** or **rhythmbox**) and press enter. It might be useful to diagnose the problem.

Edit: Too slow...

---

### Post by rsambuca on 2007-10-03
How did you install it the first time?

---

### Post by skotadi on 2007-10-03
I had to try a few times.... I think what finally worked was this (followed the instructions on this page: **[link]("https://help.ubuntu.com/community/Medibuntu")**):

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb
```

---

### Post by rsambuca on 2007-10-03
I have never installed it that way, but it should definitely work.  Sorry, not much help here.

---

