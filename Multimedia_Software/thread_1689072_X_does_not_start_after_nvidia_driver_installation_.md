---
title: "X does not start after nvidia driver installation on 10.10"
date: 2011-02-16
forum: Multimedia Software
---

### Post by toukip on 2011-02-16
Hello everybody,

I am trying to install ubuntu 10.10 on my new computer: an [Asus U33Jc]("http://uk.asus.com/product.aspx?P_ID=aMCVqkGz1jReppcv"). It is a 64bit machine.

Everything  seems Ok until I try to install the nvidia drivers. First, I tried to  install it through the graphical interface as it popped up shortly after  the install. Then, I tried to install the most up to date driver  (290.19.36) found on [nvidia's website]("http://www.nvidia.com/object/linux-display-amd64-260.19.36-driver.html"). In both cases I get the same problem.

When I boot the computer it freezes at startup typically at the stage:
"Checking battery state..." but not only (sometines before or after). In any case I never get to a graphical interface.

I looked at many forums on the web ([here]("http://ubuntuforums.org/showthread.php?t=1565176") [here]("http://rmic.be/ubuntu-maverick-nvidia-x-problem") [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=334") and [here]("http://ubuntuguide.net/ubuntu-10-10-fix-the-screen-messed-up-at-start-up-and-shutdown")  for instance). But no solution work so far. Apparently there is a  conflict with nouveau so I have blacklisted it. It seems the computer  does not send the information on the good output, so I tried to twick my  xorg.conf in different ways without any result.

Anybody would help me on this please?
Toukip

---

### Post by BicyclerBoy on 2011-02-16
This an Optimus laptop is it not  ?
If it is:
Optimus is a botch to get a nvidia GPU into a new gen i3 i5 i7 laptops while intel tries hard to shut nvidia out..
The optimus nvidia GPU has to output thru' the intel GPU framebuffer.

Search for "linux optimus" to find your answer...

You bought this laptop new & paid Microsoft for a windows OS, linux was never running on this hardware.
You may have to use windows for complete functionality.

Some optimus laptops can run discrete (nvidia GPU) only mode e.g. Lenovo thinkpad T510.
This is a good solution.
You need to check the BIOS setup options for GPU.

The best linux operation could be by using the intel GPU with i965 driver & leave the nvidia unused (still uses power).

This is not a personal rebuke but a general statement...
Purchasing this type of hardware sends all the wrong messages to the computer industry.
Asus & nvidia need to know that people will stop buying their stuff because it does not support an alternative OS.
We also need to buy hardware without any OS included, no bundles.

---

### Post by bbossola on 2011-07-20
Same issue here. However if I go to the command line, reinstall the driver, then use "gdm start" then it starts. After reboot, however, it will fail again

Any news?

---

