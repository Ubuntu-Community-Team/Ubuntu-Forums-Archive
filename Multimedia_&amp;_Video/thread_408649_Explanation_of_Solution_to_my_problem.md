---
title: "Explanation of Solution to my problem"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by greg_g on 2007-04-13
Hello,

So, I have my ATI 9250 working on my Edgy installation.  That isn't the problem.  The problem is I would like to know what the solution to my original problem actually does.

So, after installing Edgy using the alternate cd (because I needed text based, the video output was not accepted by my monitor, ACER AL2016W) I had to follow a few steps to get video working (reproduced for others information also).

I had to:
(1) boot in recovery mode.

(2) Modify my xorg.conf to include (xorg.conf is located in /etc/x11):
Section "Extensions"
     Option     "Composite" "Disable"
EndSection

Section "SeverFlags"
    Option     "AIGLX" "off"
EndSection

(3) Enable the *restricted* repositories.
     sources.list is located in /etc/apt/
    
(4) sudo apt-get update
     sudo apt-get install linux-restricted-modules-$(`uname -r`)
     sudo apt-get install xorg-driver-fglrx

(5) sudo aticonfig --initial
     sudo aticonfig --overlay-type=Xv

(6) Reboot, and it should boot to graphical login

The part I don't understand is the lines added to the xorg.conf file.  I know that these steps work to solve my problem, I just don't know why.  And since I am going to be doing a fresh install of Fiesty in a week I would just like to know what is going on in case something is different in Fiesty.

I don't know if this is the correct way to do this either.  The output of fglrxinfo is
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

And from what I have read, the Mesa driver isn't really optimal.  I mean, I can get work done, I don't game (except the random nibbles game to pass the time), but I would like to have the most optimal solution.

Any input would be greatly appreciated.

Thank you,

Greg

---

