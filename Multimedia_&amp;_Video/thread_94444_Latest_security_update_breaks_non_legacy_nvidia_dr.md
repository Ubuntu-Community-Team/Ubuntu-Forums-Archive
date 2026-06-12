---
title: "Latest security update breaks *non legacy* nvidia drivers"
date: 2005-11-24
forum: Multimedia &amp; Video
---

### Post by Pausanias on 2005-11-24
I had a perfectly working setup on a Dell Precision M70 using the nvidia driver. I even wrote a how-to on installing Ubuntu on this mobile graphics workstation, given that the standard nv driver doesn't seem to work with this machine: 

[https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70](https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70)

Then I tried the latest security update, including all the kernel packages, and upon rebooting, was welcomed by an X11 crash and a "could not load NVIDIA driver" in the X log file.

Other people have reported this same problem with the legacy nvidia drivers. Their problem seemed to be solved by reinstalling the driver, as detailed in this thread:

[http://ubuntuforums.org/showthread.php?t=93617](http://ubuntuforums.org/showthread.php?t=93617)

However, the same crashing problem exists with the non-legacy drivers. And uninstalling and reinstalling nvidia-glx does **not** fix the problem. As that previous thread was marked "SOLVED," I am starting a new thread, asking for your help.

I have to express my sore disappointment that a security update would turn a working system into a non-working one. I realize that this is an all-volunteer effort, that it's all about community, etc. That notwithstanding, I am quite upset at this turn of events, and my respect for Ubuntu, which previously was very high, has just been lowered a few notches. I usually do quite a bit of advertising for Ubuntu to my family, friends, and coworkers. Please give me reason to continue doing so.

---

### Post by Pausanias on 2005-11-24
I should add that all my software installation (outside of /usr/local) has been done via apt. I have not recompiled the nvidia drivers or any another system component by hand.

---

### Post by EcliptuX on 2005-11-24
Hi,

I have the same problem with the non legacy driver.
After few tests, I discover than the X server startup correctly **one time** after reinstallation of the nvidia-glx driver.
But after a reboot for example, the X server doesn't start correctly and I have to redo the reinstallation driver.

Maybe it can help....
Thanks for your help

---

### Post by Kannisto on 2005-11-24
What version of the nvidia-glx are you using. Experiencing the same problems with the old Hoary-driver. The 7667-driver didn't work at all for me.

---

### Post by EcliptuX on 2005-11-24
I have the problem with the version 1.0.7667-0ubuntu25 and 1.0.7667-0ubuntu25.1

---

### Post by Pausanias on 2005-11-24
I have started a bugzilla entry on this topic.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=20027](http://bugzilla.ubuntu.com/show_bug.cgi?id=20027)

Please contribute your experience there.

---

### Post by EcliptuX on 2005-11-24
Thanks :)

---

### Post by McAviti on 2005-11-25
Hi there!

I had exactly the same problem - next restart worked, at the one but next X did not come up.
I did apt-get of the new kernel's source and header files, then reinstalled with nvidias shell binary. that fixed it for me. 

mca

---

### Post by teaker1s on 2005-11-25
install legacy glx mine had same problem and missed kernel restricted module and thats how I fixed it opengl etc working perfectly

---

### Post by EcliptuX on 2005-12-05
One week later, I ever have the same pb :(

I have to re-install nvidia-glx each 2 boots :(
Is every body solve the problem with the differents soluces posted here or is there somebody who is still confronting to the bug ?

---

### Post by Pausanias on 2005-12-07
[QUOTE=teaker1s]install legacy glx mine had same problem and missed kernel restricted module and thats how I fixed it opengl etc working perfectly[/QUOTE]

Let me see if I understand you clearly. Are you telling me to install the legacy drivers even though I never have needed them before? Is that the case for you, or did you already use the legacy drivers before the security update?

I have no desire to install the legacy drivers, as I have a relatively new graphics card.

---

### Post by Pausanias on 2005-12-07
[QUOTE=EcliptuX]One week later, I ever have the same pb :(

I have to re-install nvidia-glx each 2 boots :(
Is every body solve the problem with the differents soluces posted here or is there somebody who is still confronting to the bug ?[/QUOTE]

Check the bugzilla link above. I posted the bug, one of the developers asked a questions, someone else confirmed the bug, but it's still left as NEEDINFO. Any ideas how to prod people to look at a bug that they seem to be avoiding?

---

### Post by Sico on 2005-12-17
SOLUTION?

I had the same problem.  This worked for me.

[http://ubuntuforums.org/showthread.php?p=583728](http://ubuntuforums.org/showthread.php?p=583728)

---

### Post by Pausanias on 2005-12-18
[QUOTE=Sico]SOLUTION?

I had the same problem.  This worked for me.

[http://ubuntuforums.org/showthread.php?p=583728](http://ubuntuforums.org/showthread.php?p=583728)[/QUOTE]

That solution tells you to uninstall all the nvidia drivers and install the legacy drivers. 

This is the whole point of this thread: I am seeking for a solution **without** installing the legacy drivers.

I posted a bugzilla about this a month ago and it's still listed as NEEDINFO despite myself and another person having attached tons of logs. It seems that there is no interest in really fixing this bug.

Let me repeat: I have a brand new Quadro FX Go1400. My card has always worked fine with the latest nvidia drivers. I am not about to downgrade my drivers to legacy status just because someone at Ubuntu doesn't know how to package a driver. And worse, does not feel like fixing the problem they've caused: breaking a perfectly working system via a security update.

---

### Post by Pausanias on 2006-01-03
I found the solution, at least for my setup. The bugzilla entry has been updated.

I am using the 686 kernel. The security update did not pull up linux-restricted-modules-2.6.12-10-686. It took care of the 386 but not the 686. 

Installing linux-restricted-modules-2.6.12-10-686 fixed the problem for me. This will only work if you are using the 686 kernel.

Silly of me not to think of it, but it's even more silly of the update folks not to do so.

---

### Post by XPerienced User on 2006-08-30
](*,) As a newbie to Ubuntu 6.06, I tried the recommended approach in the help docs for installing the Nvidia drivers.  The installation appears to work, but when I try to run the drivers I get:

[B]Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.[/B]

WTF! How do I get them to work...](*,)

---

### Post by Anivair on 2006-11-14
Pretty much exactly as it said. 

Open the file  /etc/X11/xorg.conf.  there should be a driver line that has "nv" on it.  Just replace the nv with nvidia and save and reboot. 

And for those who's nvidia drivers break, changing the nvidia back to nv will at least give you a GUI till you can get at the problem (in theory).

---

### Post by Anivair on 2006-11-14
> **Pausanias said:**
> 
Installing linux-restricted-modules-2.6.12-10-686 fixed the problem for me. This will only work if you are using the 686 kernel.

Silly of me not to think of it, but it's even more silly of the update folks not to do so.

I wonder how one fixes this problem if they have the 386 kernel (as I do).  It happens a lot and I don't really MIND reinstalling the drivers, but it certainly seems like i shouldn't need to.

---

### Post by dannyboy79 on 2006-11-14
> **Anivair said:**
> I wonder how one fixes this problem if they have the 386 kernel (as I do).  It happens a lot and I don't really MIND reinstalling the drivers, but it certainly seems like i shouldn't need to.

so then install the 686 kernel, it's not going to hurt you any. and as the other guy stated, it'll fix your problem.

---

