---
title: "ATI card isn't recognized by 2.6.24-20-generic kernel"
date: 2008-08-12
forum: Multimedia Software
---

### Post by hughc1 on 2008-08-12
Since downloading 2.6.24-20-generic my ATI card won't work.  The ATI card isn't recognized by the new kernel.  The ATI card works fine on the same system with 2.6.24-19-generic kernel.  
The ATI video card is RADEON 9600 series, this id is from the ATI Catalyst control center.
When the 2.6.24-20-generic kernel is run in recovery mode a different setting is detected and the video configs change.
I don't have a solution, just a report.

---

### Post by fmartinez on 2008-08-12
Did it previously work with a different kernel? If so you should be able to reboot into that kernel. That usually happens when the kernel update is issued without an update to the restricted modules leaving out the support for the proprietry cards. That's happened to me a couple times and reverted back to the previously working kernel until the updates to the restricted modules were issued out worked for me. You can also use the "sudo aptitude" command and search for the latest kernel installed and verify if the restricted modules are available for download... hope this helps.

---

### Post by hughc1 on 2008-08-13
Yes, previous kernel versions work with on the same system that can't work the 2.6.24-20 kernel.  Trying the 2.6.24-20 kernel again didn't correct the problem.  
I looked at the aptitude command and do not know how to use it.

---

### Post by markbuntu on 2008-08-13
The problem is that the -20 kernel has issues with loading the fglrx kernel modules. You can reinstall the driver and that should fix your problem. The newer -20 kernel from Hardy Proposed has maybe fixed thier problem. I got both the kernel and a new fglrx at the same time yesterday from Hardy Proposed and it worked just fine on my Ubuntustudio install.

A previous update to -20 on my 386generic install did not load the fglrx kernel modules and I had to load them by hand since I was using the 8.7 driver from ati.

Which driver are you using?
The one from the repos or one from ati?

---

### Post by hughc1 on 2008-08-14
Where did I get the driver???  Probably from the repository.  Here is the data from the Catalyst Control center-

Graphics card  ati radeon 9600 series
bios           bk-ati ver008.015.58.000
driver version 8.47.3
OpenGl Provider Ati technnologies inc
opengl version   2.1.7412 Release

How do you get the proposed releases? 
I'm running 8.04/Hardy from April.

---

### Post by markbuntu on 2008-08-14
To get the proposed releases, some of which will have bugs so beware, Synaptic/Settings/Repositories/Updates, check:

Pre-released updates (hardy-proposed)

Then reload. The next time update manager runs it will include a section in the update package list called Proposed (probably a very long one for you). These are generally packages that have been fairly well tested but may still have a few bugs so they are in put in proposed, if there are no bug reports from users, they move into the main distribution as regular updates. I personally have had very few problems with hardy-proposed but the -20 kernel update was one of them.

---

### Post by hughc1 on 2008-08-14
I have the proposed updates selected(checked).
So, the new kernel didn't fix the problem.
My boot directory has
/boot/abi-2.6.24-20-generic  28/JUL/2008
/boot/config-2.6.24-20-generic  28/JUL/2008
/boot/System.map-2.6.24-20-generic 28/JUL/2008   
/boot/vmlinuz-2.6.24-20-generic   28/JUL/2008
/boot/initrd.img-2.6.24-20-generic  6/Aug/2008

I may have the new kernel.

---

### Post by hughc1 on 2008-08-15
Installing the  2.6.24-21 kernel fixed this problem.
Thank all of you for your input and assistance.

---

