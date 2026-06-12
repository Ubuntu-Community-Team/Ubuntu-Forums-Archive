---
title: "Problem w/ Myth and dist-upgrade"
date: 2009-11-17
forum: Mythbuntu
---

### Post by mbobak on 2009-11-17
Hi all,

So, periodically, I do a 'sudo apt-get update && sudo apt-get dist-upgrade', and usually, there's not a problem.

Today, I did the same and I got:
mjb@jupiter:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-x
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.


So, having seen odd dependency problems like this before, I tried 'sudo aptitude dist-upgrade', and I got:
mjb@jupiter:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libvdpau1 
The following NEW packages will be installed:
  nvidia-185-libvdpau{a} 
The following packages will be upgraded:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg 
  libxine1-misc-plugins libxine1-x 
6 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,376kB/4,140kB of archives. After unpacking 1,782kB will be used.
The following packages have unmet dependencies:
  libvdpau1: Conflicts: nvidia-libvdpau which is a virtual package.
The following actions will resolve these dependencies:

Install the following packages:
nvidia-185-libvdpau [185.18.36-0ubuntu1~karmic~ppa1 (karmic)]

Score is 20

Accept this solution? [Y/n/q/?] 

So, I'm not sure what's going on here.  Clearly, there's some kind of dependency problem, and it appears to have something to do with the NVidia 185.xx driver, but that's the extent of my knowledge.

Anyone else seen this?  Have any ideas?

Thanks!

-Mark

---

### Post by mbobak on 2009-11-17
Any ideas or suggestions, anyone?

---

### Post by Fire_Chief on 2009-11-17
If this is a dedicated Myth box and it's working well, I would not mess with any upgrades to the system.
It looks like the *BROKEN* Nvidia VPDAU component will be updated with a working version (handles offloading much of the decoding to the GPU in a much more efficient way than previously done). You may want to check your Myth config to see if you have it set to use VPDAU for the decoding. If so, you'll probably have to update for Myth to keep working as configured.

Cheers!

---

### Post by mbobak on 2009-11-17
> **Fire_Chief said:**
> If this is a dedicated Myth box and it's working well, I would not mess with any upgrades to the system.
It looks like the *BROKEN* Nvidia VPDAU component will be updated with a working version (handles offloading much of the decoding to the GPU in a much more efficient way than previously done). You may want to check your Myth config to see if you have it set to use VPDAU for the decoding. If so, you'll probably have to update for Myth to keep working as configured.

Cheers!

Yes, I'm definitely configured to use VDPAU, and CPU usage levels would suggest that it is being used.

---

### Post by Nobodyspeshul on 2009-11-17
> **Fire_Chief said:**
> If this is a dedicated Myth box and it's working well, I would not mess with any upgrades to the system.


I learned this after my sound stopped working after an upgrade once.  Learn this lesson, don't upgrade unless you are prepared to deal with components no longer working.

---

