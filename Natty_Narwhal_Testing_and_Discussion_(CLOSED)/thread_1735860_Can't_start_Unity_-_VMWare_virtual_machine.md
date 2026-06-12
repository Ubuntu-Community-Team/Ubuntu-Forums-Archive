---
title: "Can't start Unity - VMWare virtual machine"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by paulnorris2 on 2011-04-21
I don't know if the fact that I'm running 11.04 in a virtual machine has anything to do with it, but I can't get Unity to start.  No matter what I try, I still get the Gnome desktop.  I've checked that it's really 11.04 and I see Ubuntu as the session choice at the log-in screen.

This is an upgraded 10.10 installation.  Also, on first startup, I'd only allocated 512M and saw the message saying Unity had been disabled because I didn't have the appropriate hardware.  So I increased the allocation to 2G and tried again.  I've gone to terminal and entered unity --reset, all to no avail.

Help!  Any ideas?

Thanks,

Paul

---

### Post by jamesfgraham1 on 2011-04-21
I have just started Ubuntu in VirtualBox and have the same problem.I have installed the virtualbox guest additions and "Additional Drivers' window shows that the virtualbox drivers are active. When I log in I have selected Ubuntu, not Ubuntu classic. I have 3D video, 2 processors, hardware acceleration and 1GB of RAM selected. I have the same hardware selections that run compiz in other distros.
can I start unity after it's been rejected at installation. 
thanks for any help.

---

### Post by garvinrick4 on 2011-04-21
VMware does not support compiz very well at all and that would then mean Unity would not be
supported very well. I would suggest 10.04 or 10.10 if you want to use VMware and it works very nicely. In other words avoid compiz,  3D and such.
Saw my machine as having one processor and have 2, uses 1 processor in VMware for me. Uses RAM very nicely but eats up processor. Watch what
happens when you run flash!! I like to fool with it though, with all different distro's is interesting to play with.

---

### Post by paulnorris2 on 2011-04-22
Thanks, this makes sense to me.  I've been running Ubuntu in virtual machines for years, just recently upgraded one of my VMs to 10.10 and it seems fine.

---

