---
title: "fix for being stuck in 640 x 480 screen size"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by wallydallas on 2006-07-06
I was using ubuntu 6.06 for a week.  It installed and worked great.   My screen resolution was 1024 or larger.

A few days later when I turned on my computer the logon screen was 640x480 .    I logged on.   The control panel to change to a larger size offered me only one choice: 640x480.

The steps to fix this:
=========================
- start ubuntu in 640 mode, logon 
- open applications, accessories, terminal
- type the command below
sudo dpkg-reconfigure xserver-xorg
- you should see a blue screen and many questions
- just hit enter to go to each next screen
- don't change any default answers unless you know better
- hope that it can auto detect your video card and monitor
- you may have to hit tab to get to the default answer
- shut down
- restart, you should see a logon screen at 1024 pixel resolution or higher
- after you logon go to:  system-preferences-screen resolution
- set the screen size you need

This seems to be a very common problem.
Here are just a few who reported the same problem:
===============================
[http://www.ubuntuforums.org/showthread.php?t=46317](http://www.ubuntuforums.org/showthread.php?t=46317)
[http://www.desktoplinux.com/articles/AT3134398543.html](http://www.desktoplinux.com/articles/AT3134398543.html)
[https://launchpad.net/distros/ubuntu/+ticket/327](https://launchpad.net/distros/ubuntu/+ticket/327)

I've been unable to reproduce the bug again.  Here is my guess at a cause.   I used Ubuntu for a few days.   I disconnected my HardDrive and connected the harddrive that had windows2000 server.   I booted that for a few days.  Then I took out that hard drive and connected the hard drive with Ubuntu.   This is my safe way to boot many operating systems.  I have about 6 hard drives I use, one at a time, in my one machine.

I have ubuntu 6.06  Pentium 4  Nvidia Rage video card

---

### Post by raldz on 2006-07-06
I have experienced this same problem.. I have Windows XP ang Kubuntu on dual boot.. what I did was after dpkg-reconfigure xserver-xorg, i made a copy of my xorg.conf file..

to copy:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then if my display went wrong again at boot up, I just hit CTRL+ALT+BACKSPACE then:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

at this way, I wont have to configure the settings again....

---

