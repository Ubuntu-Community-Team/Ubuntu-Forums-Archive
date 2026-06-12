---
title: "Xinerama and TwinView"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by comrade.bronski on 2007-03-16
I am trying to get three identical ViewSonic VP2130b monitors to work with a couple of 7300GTs. I've successfully got the all working but with the following two problems:

1/. 3D rendering is extremely slow - maybe about 1 frame a second

2/. The two monitors running with TwinView are seen by the windows manager as a single screen and expand window across both.

According to an Nvidia readme.txt (here: [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7667/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7667/README.txt)) Xinerama is not provided by the Nvidia driver if Xinerama is enabled in your xorg.conf. 

Is there a way around this and can I get both problems resolved?

Thanks in advance for any advice.

---

### Post by lledurt on 2007-04-24
Let me know if you figure it out.  I have the same problem all 3 are working but 2 are viewed as 1 monitor stretching my windows.  Also I can no longer start terminal?  GO figure.
P.J.

---

### Post by lledurt on 2007-04-24
Check out my too many monitors thread.  I used Xinerama and dumped the twinview option altogether.  It supported 3 monitors.  I am sure there are issues with your speed for this, but at least you will have the desired effect for the monitors.  Let me know if you need my xorg.conf.

My issue is that gnome-terminal doesn't work on any of my configurations using Xinerama.  

P.J.

---

