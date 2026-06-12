---
title: "Nvidia installed but not found."
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by flebber on 2007-11-05
I have the nvidia driver installed and according to the Restricted Driver it is enabled and in use.

However when trying to start nvidia-settings i get this ```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```
Or nvtv I get this ```
flebber@flebber-desktop:~$ nvtv
Fatal: No supported video card found.
flebber@flebber-desktop:~$

```

so from this post [http://ubuntuforums.org/showthread.php?t=573982]("http://ubuntuforums.org/showthread.php?t=573982") I did this > sudo dpkg-reconfigure xserver-xorg and select vesa  then I used Envy into install the drivers.

And then again went and confirmed that it was enabled in restricted drivers it is but the same errors still persist. 

My card is a 6200.

---

