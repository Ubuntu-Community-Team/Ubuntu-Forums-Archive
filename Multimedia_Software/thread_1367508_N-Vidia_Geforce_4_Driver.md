---
title: "N-Vidia Geforce 4 Driver?"
date: 2009-12-29
forum: Multimedia Software
---

### Post by Unix-Man on 2009-12-29
Hello, I just got Ubuntu installed on my new/used computer. 
It's running a dreaded Nvidia [GeForce 4 MX 440] And there is no drivers under System > Administration > Hardware Drivers

I open Hardware drivers and it says   

"No proprietary drivers are in use on this system."  
I've heard rumors these cards are "Bad" with Ubuntu but im not sure what to do. 

I tried 

"sudo aptitude install nvidia-glx-96" it said...


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "nvidia-glx-96"
Couldn't find any package whose name or description matched "nvidia-glx-96"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


Kinda need a driver :confused:
Looking forward to setting up Compiz! 

Cheers!

---

### Post by HappyFeet on 2009-12-29
You probably need to enable a repo first. Go to system>administration>software sources and see if everything is checked off. Also check the sources in the "other software" tab. Then reload and try again.

---

