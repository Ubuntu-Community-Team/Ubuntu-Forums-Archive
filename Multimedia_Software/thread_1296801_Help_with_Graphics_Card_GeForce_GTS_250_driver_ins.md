---
title: "Help with Graphics Card GeForce GTS 250 driver install"
date: 2009-10-21
forum: Multimedia Software
---

### Post by hucarlisle1 on 2009-10-21
Hopefully someone can help me. I havent been able to find anything in my searching. 

so this week i did two things, i switched to ubuntu :D and got a brand new graphics card :D, the Nvidia GeForce GTS 250 1gb. Unfortunately, I am having serious trouble installing this bad boy :( (the gpu not ubuntu). 

When i run my computer it looks fine, but when i try to look at screensaver previews it wont show them, and when i try to increase the visual effects (which are set at "None") i get "Desktop effects could not be enabled". I uninstalled the driver and ran ubuntu without it and there was a noticeable difference, and when i reinstalled it it did look better, but it still wont allow me to change the visual effects or play any 3d games. 

I have never installed one before but it doesnt seem like it should be rocket science.

I have tried everything I can think of to try to get the driver working properly. I have used synaptic, i have done it how nvidia says i should do it, i have tried using envy, i have tried it using nothing but terminal. Still no luck. Ive tried different versions (i think). Still no luck. 

Im really bummed because i just got this new card and cant use it.

Sorry i dont know what info might help so just let me know what specs you might need from my comp and we'll go from there. 

Thank you in advance! :)

---

### Post by jonasback on 2009-10-21
Congratz to the great choice of changing to Ubuntu. If you haven't made any foolish settings :D this should do the trick. Open up a terminal and type:

sudo apt-get install nvidia-glx-185

---

### Post by hucarlisle1 on 2009-10-22
thank you for the reply :) unfortunately no dice with that....i terminated my x server and ran the install...it said the install was complete...however, during the install it said:
"Unable to create 'usr/lib/nvidia/libnvidia-cfg.so.180.44' for copying (No such file or directory)"   
[press ok]

"Unable to restore '/usr/lib/nvidia/libnvidia-cfg.so.180.44' " 
[press ok]

(it then said the same things with 'usr/lib/nvidia/libGL.so.1.2.xlibmesa')

so i dont know if that is related to it at all...but it still only half works...the graphics are visibly improved but still wont allow me to run 3d graphics or enable the desktop effects

thank you for your help in advance :)

---

### Post by hucarlisle1 on 2009-10-22
> **jonasback said:**
> Congratz to the great choice of changing to Ubuntu. If you haven't made any foolish settings :D this should do the trick. Open up a terminal and type:

sudo apt-get install nvidia-glx-185

it says:

"Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nvidia-glx-185"

---

### Post by moe_syzlak on 2009-10-22
I'm on Kubuntu. How about you try the GUI tool that tries does it automatically for you. I think the name of the app is called "Hardware Drivers." It's in the main menu, "up top," System > Admin. > Hardware Drivers.

Normally this is the recommended route.

If it doesn't work with your card by taking that route, then you probably won't get it working for a while because Nvidia often neglect desktop graphics vs workstation graphics.

---

### Post by Zeenomorph on 2009-11-13
I have a GeForce 250 as well.  I was running a 8800gt, but it fried.  I went to pick up a new video card and go the 250.  I checked the forums, and also the Nvidia howto.  It seems as though there isn't a solution at this point. 

Are we to just wait for Nvidia?  

It's frustrating.  I use my computer to show people the "eye candy" of Linux.  Now I have 0 graphics.  No cube, no screensaver, crappy resolution.  I feel helpless.

Would I be doing any better if I installed 9,10?   I'm currently in 8.04.

---

### Post by moe_syzlak on 2009-11-21
> **Zeenomorph said:**
> I have a GeForce 250 as well.  I was running a 8800gt, but it fried.  I went to pick up a new video card and go the 250.  I checked the forums, and also the Nvidia howto.  It seems as though there isn't a solution at this point. 

Are we to just wait for Nvidia?  

It's frustrating.  I use my computer to show people the "eye candy" of Linux.  Now I have 0 graphics.  No cube, no screensaver, crappy resolution.  I feel helpless.

Would I be doing any better if I installed 9,10?   I'm currently in 8.04.

Yea graphics are still one of the banes of Linux. There are certain grade of graphics cards that are sure to work in Linux: workstation graphics cards. You can get them online for cheap, a decent on around $100 on NewEgg. 

The reason why they work better with Linux is that Nvidia put more dev time into workstation graphics. Workstation graphics is where all the high-end professional user apps like AC3D, Houdini, Maya, SolidWorks, and Zbrush that run on Linux. Nvidia provides better support as to keep it's image as an industry leader and enabler. While, there are no top-selling desktop 3D games like on Windows. That, and the NVIDIA driver team is small, under 50 if I remember from the article, and on top of that they are stretched thin by developing drivers for *BSD, *Nixes (AIX, Solaris, SCO Unix..etc,), and of course LINUX! So the devs prioritize and put most of their hours into workstation graphics cards QUADRO. ATI does similar with its FIREGL support.

There was a /. article on it -> [http://tech.slashdot.org/story/09/10/20/1948237/NVIDIA-Driver-Developer-Discusses-Linux-Graphics?from=rss](http://tech.slashdot.org/story/09/10/20/1948237/NVIDIA-Driver-Developer-Discusses-Linux-Graphics?from=rss)

---

