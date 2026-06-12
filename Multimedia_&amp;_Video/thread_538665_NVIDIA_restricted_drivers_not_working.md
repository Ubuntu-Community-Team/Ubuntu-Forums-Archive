---
title: "NVIDIA restricted drivers not working"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by eqo314 on 2007-08-30
Hi, 
My NVIDIA drivers are not working and after enabling it in the restricted drivers manager, and restarting,  i get a "Failure to initialize the NVIDIA kernel module".

Here's some background:
The nvidia restricted drivers where initially installed into my machine and I was using beryl.  Yesterday, the screen would turn grey if i tried to use the desktop cube.  After tinkering with the beryl settings and shutting down and logging on several times, I thought it would be a good idea to reinstall the nvidia drivers (i just migrated to ubuntu from windows, and this was always a good idea in windows).  I went to the restricted drivers and disabled the nvidia drivers and restarted.

When it restarted, the i got that above "failure to initialize.." message and I could only run linux from the command line.  After some research, I had learned to use
code: sudo dpkg-reconfigure xserver.xorg, chose the vesa or "nv" driver so i can just get the desktop, then 
          sudo invoke-rc.d gdm stop
          sudo invoke-rc.d gdm start.

This caused the desktop to load but beryl wouldn't work anymore.  I would go to the restricted drivers manager, "enable" the restricted nvidia driver, get a successful post message and get a prompt to restart the computer.  I would restart the computer, get the "Failure to initialize the NVIDIA kernel module" and restart the whole process again of reconfigure, gdm stop, gdm start.  

I've also tried things like 
code: sudo apt-get install-glx nvidia kernel-common
sudo dpkg -r invidia-glx -> sudo dpkg -i nvidia-glx

I am at my wit's end.  

This is on my girlfriend's machine, and she is threatening to migrate back to windows if I can't figure this out.

our machine:
AMD Athlon 64 X2 3800+ Windsor 2.0GHz Socket AM2 Processor
ASUS M2NPV-VM AM2 NVIDIA GeForce 6150  (i'm using the onboard card)
1GIG DD2 400 RAM

---

### Post by OoooMatron on 2007-08-30
I'd remove all the nvidia **** and download the script from their site and isntall it manually. You will need to install a few things maybe (it tells you what when it fails to install) and providing you remove all the kernel modules and stuff related to the ubuntu install it will go without  a problem.

are you using the latest versions or the legacy? I find it safer with the legacy sometimes.

Also, I know how you feel when someone else gets uptight about it all for you :D

---

### Post by eqo314 on 2007-08-30
What's the best way to remove all the nvidia stuff?

---

### Post by eqo314 on 2007-08-31
ooomatron,

your suggestion worked perfectly, thank you.  I removed anything that said "nvidia" through the synaptic package manger.  I went to the nvidia website, downloaded the files there and installed via nvidia's utility.  

the desktop works again, and it seems to work better (no more grey screens when rotating the cube, for example).

I guess this topic is solved, how do i put a "solved" statement at the top of the thread?

the open issue that remains however, is why after initially removing the nvidia restricted driver, did reinstalling the nvidia drivers through synaptic or the restricted drivers manager fail? how do i open a bug report?

---

