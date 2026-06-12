---
title: "Ubuntu 11.10 Upgrade ATI / AMD Graphics Problems"
date: 2011-10-15
forum: Multimedia Software
---

### Post by david_1989 on 2011-10-15
Hi everyone,

I upgraded from 11.04 to 11.10 on a 64-bit system this morning in eager anticipation. The upgrade went well and the ATI proprietary drivers for my 5770 1GB were already installed. I had a few problems however in that window shadows didn't look right, in fact they looked awful. Performance was also a bit sluggish and windows were all active even when not actually the active window.

I then tried to install the post release drivers, the installation kept failing, which from a quick Google search seems to be very common.

I then removed the ATI drivers that came with Ubuntu and manually installed the latest proprietary drivers from the AMD website. This installed fine and I rebooted. I am still having graphics problems and performance is shocking. I have disable sync to v-blank in the Compiz settings under opengl which did the trick in 11.04 with issues before.

I have now tried to reset Unity and Compiz. After doing the later when I now make any changes in the Compiz settings manager, my session crashes and I am returned to the login screen which is incredibly annoying.

I've tried numerous things and so far nothing has got my system running nicely as it was before. It's so bad that I am writing this post from Windows 7 which works beautifully. So far I am incredibly disappointed with Ubuntu; I have had bad upgrade experiences before, but this is definetly the worst.

Any help would be much appreciated.

Thanks,
David.

---

### Post by rmcnamara on 2011-10-15
I hear your pain. I am new to ubuntu as well and i have had to reinstall twice with video and other problems. If the system crashes i get the blank screen with "ok" upon reboot. I really like ubuntu and all. but the issues are extremely annoying.

---

### Post by jmate24 on 2011-10-15
go to [http://http://support.amd.com/us/Pages/AMDSupportHub.aspx]("http://http://support.amd.com/us/Pages/AMDSupportHub.aspx") select Desktop graphics on the right side of the window and select your product line then your model then Linux_x86 or Linux_x86_x64. and go in to a terminal and type: (for x86 systems. enter the version of the driver in where the x's are)

```
cd ~/Downloads && sudo sh ati-driver-installer-xx-x.x86.run
```

for 64-bit:

```
cd ~/Downloads && sudo sh ati-driver-installer-xx-x-x86.x64.run
```

follow instructions on how to install your driver by either installing it directly or by creating a .deb file to install with your package manager.

---

### Post by rmcnamara on 2011-10-15
I tried that way as well. It installed correctly. But upon reboot I had a blank desktop with just a menu in the top left of the screen. I didn't know where to go from there. So I reinstalled. As of right now I'm using the default driver that ubuntu installs during setup

---

### Post by david_1989 on 2011-10-16
> **jmate24 said:**
> go to [http://http://support.amd.com/us/Pages/AMDSupportHub.aspx]("http://http://support.amd.com/us/Pages/AMDSupportHub.aspx") select Desktop graphics on the right side of the window and select your product line then your model then Linux_x86 or Linux_x86_x64. and go in to a terminal and type: (for x86 systems. enter the version of the driver in where the x's are)

```
cd ~/Downloads && sudo sh ati-driver-installer-xx-x.x86.run
```

for 64-bit:

```
cd ~/Downloads && sudo sh ati-driver-installer-xx-x-x86.x64.run
```

follow instructions on how to install your driver by either installing it directly or by creating a .deb file to install with your package manager.

I have already done this. Improves things a little.

---

### Post by orkineric on 2011-10-17
I've been having major trouble with this as well. I have an ATI Radeon HD 4250, and it worked great under Ubuntu 11.04. After the upgrade, and after successfully installing the updated driver (which was quite a pain), I have it working, but my screen is a bit blurry now, and when I try Savage 2, it fails to render the sky. Everything else seems to be running now, but I'd really like to understand better how to resolve these driver issues, if there is indeed anything I can do at this point.

david_1989, have you had any further luck with this one?

---

### Post by spreeker on 2011-10-20
Yes I have the exact same problems and issues. Why show me those upgrade screens when my display driver probably will crash..

this is soo annoying. :(
we probably have to wait a few days/weeks. before ati/amd comes up with a new catalyst version.

right now the standard login does not work. I got to the terminal with cntr-alt-F1 and kill 

```
$sudo service lightdm stop 
```

and 

```
startx
``` this gives me a "workable" environment..

---

### Post by david_1989 on 2011-10-24
> **orkineric said:**
> I've been having major trouble with this as well. I have an ATI Radeon HD 4250, and it worked great under Ubuntu 11.04. After the upgrade, and after successfully installing the updated driver (which was quite a pain), I have it working, but my screen is a bit blurry now, and when I try Savage 2, it fails to render the sky. Everything else seems to be running now, but I'd really like to understand better how to resolve these driver issues, if there is indeed anything I can do at this point.

david_1989, have you had any further luck with this one?

In the end I gave up and reinstalled. This time I have not installed the ATI Proprietory drivers and everything is working well. Generally performance is good with the open source drivers, though I think it is a bit worse for games etc, but I can live with that. I may later try installing the proprietory drivers on my flash drive.

---

