---
title: "TV-out Nvidia in Gutsy Gibbon"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by gobbomaster on 2007-12-04
Hi,
I installed Gutsy Gibbon yesterday and am glad to say it didn't have a lot of the problems I had in Feisty, I've got almost everything working great except for the tv-out. I struggled with this on Feisty as well messing up the xserver multiple times until I couldn't stand it anymore and stopped trying. I was really happy when I found the Screens and Graphics option in administration, I even got the tv working, only problem. The resolution of my laptop (normally 1280x800) dropped to 640x480 like my tv. When I tried to get it back to normal everything messed up and I was glad I could get rid of the nvidia drivers (via restricted drivers) and re-install them. It's working again but I really want tv-out.. I didn't do anything in xorg file and I'm still a complete noob at linux so I hope someone can help me out?

Thank you..

---

### Post by fenian on 2007-12-04
Use nvidia-settings to set up seperate x screens.Open nvidia-settings with this command...
> 
sudo nvidia-settings

Go to the X server display configuration,choose the tv icon (if its not there click detect displlays button),click the configure button and choose Seperate x screen click the save to xorg configuration file button and quit nvidia-settings.Restart the x-server  with ctrl+alt+backspace.
This willl give you two independent screens with different resolutions.You can perform seperate tasks on each screen:surf the web on the laptop screen while watching a video file on the tv.

---

### Post by gobbomaster on 2007-12-04
It worked right away, thank you so much!

---

### Post by gobbomaster on 2007-12-05
Euh, on second thought.. I discoverd that my visual effects were turned off again and when I tried to turn them on the menu bars of every window disappeared..? Is there an easy fix for that as well?

---

### Post by fenian on 2007-12-09
Try running the command...


> sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

