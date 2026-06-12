---
title: "Kino can control camera but does not see output"
date: 2009-05-11
forum: Multimedia Software
---

### Post by serotta_rider on 2009-05-11
I have been working for a few days to solve a problem with Kino video Capture from a canon HV20. The camera and cable talks to windows with no trouble so I know its in the computer or software.

Kino is able to start, stop, pause my canon HV20 camera but I dont see the output on the screen. When I click capture, the camera hangs and I get a message at the bottom of the screen. "Waiting for DV 10 9 8 7 6..." until it shuts down.

I am running Kino as sudo to get around any permissions problems that I have read about on other posts. 

I am running ubuntu 9.04, Kino 1.30, and DVGrab 3.2-2

My lsmod output is below.


 lsmod | grep 139
raw1394                32732  0 
video1394              23740  0 
dv1394                 25948  0 
ohci1394               38576  2 video1394,dv1394
ieee1394               94660  4 raw1394,video1394,dv1394,ohci1394

---

### Post by fuwkej on 2009-05-14
I had same problem, fixed it by using Kdenlive.

Once you install (from add/remove) click on right side where it says Record Monitor. Click the little gear to configure and change the input to HDV instead of RAW dv. Worked like a charm after that. Great camera btw.

:D

---

### Post by bumanie on 2009-05-14
When I used kino, I found I had to open it by typing sudo kino in terminal. If it was started by GUI from the drop down list under Sound and Video, I found kino would not work. Not sure whether running it in super user mode is correct, but it is the only way I could get kino to work. It worked fine when I started it this way.

---

### Post by serotta_rider on 2009-05-19
Thanks [laverabe]("http://ubuntuforums.org/member.php?u=314948")

that did it!!!! I ended up needing to use dvgrab and specifying the format as a high def format but you put me on the right track after days of work.

thanks again.

---

