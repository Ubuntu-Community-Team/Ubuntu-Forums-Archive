---
title: "Remembering multiple monitor setup whenever switch"
date: 2012-07-16
forum: Multimedia Software
---

### Post by skunkwerk on 2012-07-16
Hi,
  I'm running ubuntu 12.04 with an nvidia GPU on a Thinkpad W520.  I have an external monitor at work, and one at home.  Whenever I move, I have to manually launch the nvidia x server settings program, detect the displays, click ok, click quit... and it's getting a bit tedious by now.  Is there any way to automate this?  I've heard xrandr could do this, but can't find much info on google or the man page.

thanks,
imran

---

### Post by lunatico on 2012-07-24
Have you tried using disper?

I use it, and I have keyboard shortcuts for each thing I want.

Example:
Ctrl+Alt+1 = Output only on laptop screen
Ctrl+Alt+2 = Output only on external monitor
Etc...

Install disper and have a look at it's man page.

Note: I'm running Linux Mint 13 but it should be the same.

---

### Post by GangstaMon on 2012-07-24
Hi,

I have the same problem but 10 times more difficult considering different monitor sizes and different projectors etc.

Laptop + none
Laptop + 24" LCD at home
Laptop + 27" LCD at work
Laptop + Projector at work in a conference room

For  each case I have to plug in the monitor/projector cable before I start  up the laptop. The on-the-fly plug in/out and auto detection is out of  question, it does not work.

After start-up and login I have to  run "sudo nvidia-settings" and enable and configure the the external  monitor even though all configs are saved and merged to xorg.conf.

At  first I had (and still have) different xorg files for different  monitors/projectors but I had no options to select one at the start-up  (encrypted disk, put passwd and it starts) so I logged in first and  copied proper xconf.24 or xconf.27 etc to xconf.org and restarted...

Actually  I run an Ubuntu 12.04 as a host and then run a virtual  W7 with VMPlayer. There are even more problems with sound and other stuff which I am  not going to write here.

I'm just thinking, the use of multiple  monitors at once and changing monitors while OS is running is not new  and it is very easy in other OS (you know which) so the smart architects  and developers of the community of Open Source Distros must already  have fixed it. I am the one who does not know how to do it properly ;)

Thank you all Gals n' Guys

---

### Post by skunkwerk on 2012-08-13
I've tried to get auto-disper to work by saving my configs when the displays are working, but it doesn't switch properly.  It manages to detect the attached monitor, but it doesn't turn it on:

$ auto-disper --change home
no resolutions found for display CRT-0, falling back to: 800x600, 640x480
home (detected)
Config already loaded

$ auto-disper --change work
no resolutions found for display DFP-2, falling back to: 800x600, 640x480
home
laptop
work (detected)
Config already loaded

any ideas?

thanks

---

### Post by rykel on 2012-10-10
I came here looking to find a way to make my PC automatically change resolutions with or without the projector turned on. This should be basic. Running Ubuntu 12.04.

---

