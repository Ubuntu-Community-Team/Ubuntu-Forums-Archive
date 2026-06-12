---
title: "X doesn't start after installing nvidia-glx in kubuntu feisty"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by Wubanga on 2007-04-23
Hi guys

I installed Feisty Fawn yesterday and have tried to get my graphics card to work optimal with the nvidia driver.

I installed the nvidia-glx with adept, and after that I did

sudo nvidia-glx-config enable

Then I rebooted the computer.

When it booted it started with the kubuntu screen but before starting the X, the screen turns black and I only got an underscore in top left corner. I tried to reboot, but it happened the same.

I booted in rescue mode but couldn’t copy the old conf file so I did a new fresh install, now I’m running with the “nv” driver not “nvidia”, and the system is a bit sluggish and the RAM memory goes up fast.

I never had any problem with my card and the nvidia drivers before, and I’ve been with ubuntu since warty. It seems that the problem has happened to some more people in other forums, but no answer yet. Is it a reported bug in feisty? Any possible solution? Thxs in advance.

Wubanga

---

### Post by Arun985 on 2007-04-23
I'm having the same problem. I installed the new nVidia driver from the nVidia website and when I rebooted, X-Server didn't start. I got the blue screen saying X-Server couldn't start my GDM. So I had to reconfigure x and reboot again, using my onboard graphics. Any help to this problem would be greatly appreciated.

---

### Post by peebly on 2007-04-23
Hi

Have you tried using envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

never fails on my computer.

---

### Post by Wubanga on 2007-04-23
> **peebly said:**
> Hi

Have you tried using envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

never fails on my computer.

The page is down now, but I'll give it a try. Thxs.

Also check this thread, I won't be able to test in a few weeks (job issues), but if any of you do it, please inform us how it went.

[http://ubuntuforums.org/showthread.php?t=419738](http://ubuntuforums.org/showthread.php?t=419738)

Thxs.

---

### Post by joriad on 2007-04-23
I had the exact same problem. I resolved it by editing the xorg.conf to read "nvidia" instead of "nv" after installing nvidia-glx. Now i have screen resolution 1280x1024 instead of the 800x600 default.

---

### Post by Wubanga on 2007-05-05
> **joriad said:**
> I had the exact same problem. I resolved it by editing the xorg.conf to read "nvidia" instead of "nv" after installing nvidia-glx. Now i have screen resolution 1280x1024 instead of the 800x600 default.

Yup, totally right. I tried to install the drivers again and got the same problem.
This time I installed nvidia-glx-new and after trying nvdia-glx-enable i got this prolem:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

So, easy as pie. I edited xorg.conf, changed "nv" with "nvidia", booted and everything worked!
Then you can nvidia-settings and configure the video card resolution or whatever.
Thxs dude!

---

