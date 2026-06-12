---
title: "Dual Monitors +Nvidia +Desktop Scrolling (too big?) +XRandR X Extension was not found"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by ryanlhjess on 2007-11-02
To further elaborate from my Title:

I have a dual monitor setup with an nVidia 6600GT,  
The two monitors both need to display 1280x1024

Problem:
The 'primary' monitor displays a desktop that is too big,  and therefore you have to scroll to see various parts of the desktop.  By simply moving my mouse off screen, my desktop will change focus to follow the arrow.   

I thought this was a resolution problem so i tried the following

'gksudo nvidia -settings'

I selected the X Server Display Coniguration,  however when i try to manipulate the resolution i get the following error

"The XRandR X extension was not Found..."

I am using nvida glx 'new' drivers.


Please Help!

---

### Post by teknorah on 2007-11-02
Try [Envy]("http://albertomilone.com/nvidia_scripts1.html"), it worked for me! :)

---

### Post by Eoghan Murray on 2007-11-19
With the same problem, I ran Envysuccessfully, but still have this problem

---

### Post by Eoghan Murray on 2007-11-19
Okay, I solved this by disabling 'Xinerama' (either by editing xorg.conf, or by ticking the box in the nvidia-settings app)

---

### Post by DaveLG on 2007-12-05
I haven't been able to disable Xinerama via the nvidia control panel. I installed via envy which has always worked for me.

---

