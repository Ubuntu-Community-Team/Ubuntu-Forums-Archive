---
title: "After installing nVidia driver"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by Ophie on 2007-04-14
After I installed the nVidia driver with envy it asked for a restart so I did and upon returning ubuntu will only start in command line:confused: 
I want to install openGL as well if i get the system back up
Can anyone give me some pointers on how to resolve this issue? 
Thanks in advance!

---

### Post by tommcd on 2007-04-14
To get the GUI back up boot to recovery mode and run:

sudo dpkg-reconfigure xserver-xorg

Answer defaults to all questions if you don't know the answers.

What nvidia did you install with envy, the nvidia-glx or the driver from nvidia's website?
What nvidia card do you have?
You can probably just use the nvidia-glx driver from synaptic (real easy), but if you installed the driver from nvidia's website you will have to remove that first. Sorry, I never used envy, but it should have an unnstall method.

---

