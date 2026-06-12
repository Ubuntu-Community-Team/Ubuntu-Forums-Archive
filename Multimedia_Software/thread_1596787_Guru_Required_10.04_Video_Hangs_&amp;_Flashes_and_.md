---
title: "Guru Required: 10.04 Video Hangs &amp; Flashes and Resumes NVIDIA Driver Issue"
date: 2010-10-14
forum: Multimedia Software
---

### Post by rwmech on 2010-10-14
I have the most bizarre problem that started with 10.04.  Up until 10.04 I had zero problems with my setup.  I am convinced this has something to do with NVIDIA 7100GS and 10.04.

Here is the problem in a nutshell.

I have my home desktop, which I upgraded to 10.04 from 9.10.  Everything went just fine except when it booted up and I logged in, the video "shut off", the computer "hung" for about 10 seconds, then came back.  I'm able to use it for about 10 seconds then the same thing happens.  Video blanks, system hangs, comes back.

I've tried turning off compiz, no effect.  I've tried nvidia-current along with other versions (including the one from the website) and they ALL have the same problem. 

I know it's not a hardware issue as I can boot the live CD just fine.  I also upgraded to 10.04.1 and that worked fine until I installed the nvidia drivers. 

Here is what I dont understand either.  I did a apt-get remove --purge nvidia* and the problem still existed after that.

Something is seriously wonky.  I REALLY don't want to re-install the entire box.  

Now, here is something else that doesnt make sense.  I have 10.04 installed on my work box with a Nvidia 9800 graphics card and I have no issues at all.  

Granted I can buy a new graphics card but I really don't want to do that.  

Anyone got any idea what could be causing this?  I'm no newbie but this problem is just baffling.

---

### Post by amauk on 2010-10-14
This sounds like a video driver / x.org config issue

Make a backup of your xorg.conf
```
cp /etc/X11/xorg.conf ~/Desktop/xorg.conf
```


purge the nVidia binary driver
```
sudo apt-get purge nvidia-current nvidia-common
```


Delete xorg.conf
```
sudo rm -f /etc/X11/xorg.conf
```


Restart, and you should be using Nouveau
Double check you have no issues

Reinstall nvidia binary driver
```
sudo apt-get install nvidia-current nvidia-common
```


Run the nvidia xorg config thing
```
sudo nvidia-xconfig
```


Restart

You may wish to compare the new /etc/X11/xorg.conf file with the backup on your desktop, to see if you can spot any potential reasons for the issue

---

### Post by rwmech on 2010-10-14
I will give that a whirl, but I've done pretty much that already.  Maybe not in that order which is why I'll give it a go. :)

---

### Post by rwmech on 2010-10-21
No dice.

if I restart GDM, it works fine.  as soon as I run the nvidia-xconfig and restart GDM the same issue comes back.  Seems as soon as the nvidia drivers are involved this issue happens.  

This is wierd, pre-10.04 this worked PERFECTLY, no problems.

---

