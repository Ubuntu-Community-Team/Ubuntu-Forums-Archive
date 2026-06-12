---
title: "Twinview configuration problem"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by doriard on 2008-01-21
I used to have Twinview configured so that each monitor had a separate background image, and the System settings showed two separate monitors, but not separate X screens.  I recently had to re-install Kubuntu Gutsy, and I lost the configuration.  How do I get back to separate monitor and backgrounds without going to separate X screens?  The nvidia-settings utility doesn't seem to do it?

---

### Post by chewearn on 2008-01-22
> **doriard said:**
>   The nvidia-settings utility doesn't seem to do it?

Why not?  I have used nvidia-settings, and it work fine.

---

### Post by doriard on 2008-02-08
Using nvidia-settings I am able to get separate screens (separate X windows) or a double wide view where the taskbar spans both monitors and wallpaper is centered between screens (Twinview), but I can't get separate screens with independent wallpaper, etc.  It used to work, but after re-installing Kubuntu I can't get it working again.

---

### Post by doriard on 2008-03-06
There seemed to be several querky problems in Kubuntu that caused it.  The fix involved several things:
Dual monitors: If the nvidia-settings won't accept multiple metamodes due to xorg.conf problems, just allow it to delete the duplicate metamodes (using "Ignore") until all the duplicate ones are deleted.  Also, Twinview spans both monitors it may be because the Linux system monitor settings isn't recognizing one of them (unknown monitor).  Change to system monitor setting to Samsung Syncmaster (ex.) or Plug-and-Play.  To display separate monitor backgrounds, just configure the desktop backgrounds (right click on desktop and configure).

---

