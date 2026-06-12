---
title: "Catalyst 11.1 and Radeon HD 6900 series"
date: 2011-01-28
forum: Multimedia Software
---

### Post by The_Fool on 2011-01-28
First problem is that there does not seem to be any Catalyst Control Center available for this driver.  Is there one anywhere for Linux for this driver?

The graphics card appears to be constantly at 99% usage at all times when simply sitting at the desktop.  Is there a way to bring this down to virtually no usage like it should be at?

The display area on my monitor does not extend to the edges.  In Windows, I can simply scale it to 0% to overscan in order to completely fill the screen inside the Catalyst Control Center; in Linux, I have been unable to do so with a monitor.  Is there any way to scale the display area to completely fill my screen?

---

### Post by The_Fool on 2011-01-28
Anyone have an answer to any of these questions?

---

### Post by Yellow Pasque on 2011-01-29
How did you install the driver? There is definitely a CCC with 11.1 just like there always is.

---

### Post by The_Fool on 2011-01-29
> **Temüjin said:**
> How did you install the driver? There is definitely a CCC with 11.1 just like there always is.
I downloaded the .run file from AMD's site, ran it from a prompt using: sudo bash ./blahblah.run, and I installed it.  Should I have installed it another way?

I have been trying to configure it using aticonfig, but I'm unable to extend the displayed area to fill my computer screen.  It also runs the GPU at 99% just sitting at the desktop.

---

### Post by The_Fool on 2011-01-30
Bump.

---

### Post by kulimazi on 2011-01-30
I posted a possible solution to the underscan issue to this thread earlier today ...

[http://ubuntuforums.org/showthread.php?t=1409508](http://ubuntuforums.org/showthread.php?t=1409508)

I cannot say much about the lack of CCC or 99% usage ... my HD6950 is working fine with the 11.1 drivers on Ubuntu 10.10. I simply ran this command and the installer took care of everything...

sudo ./ati-driver-installer-11-1-x86.x86_64.run

Good Luck ...

---

### Post by The_Fool on 2011-01-31
Thanks for the assistance with extending the display area to fill my screen.  Unfortunately, a couple problems still remain.

I am still encountering 99% GPU usage at all times which makes everything extremely slow.  Is there a way to get rid of this?

I am still unable to get the Catalyst Control Center working, although  it's not all that vital since just about everything can be done with  aticonfig.  Where is this program stored at so I can check to see if it  is installed?

---

### Post by kulimazi on 2011-01-31
Catalyst Control Center binary gets installed here:

ls -la /usr/bin/amdcccle 
-rwxr-xr-x 1 root root 6564840 2011-01-29 21:50 /usr/bin/amdcccle

which process is consuming 99% of your cpu?

---

### Post by Yellow Pasque on 2011-02-01
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

### Post by The_Fool on 2011-02-02
Success!  That website certainly helped me fix this after I upgraded from 10.04 to 10.10.  The installation of these drivers was more complicated than I initially thought.  Long story short, it appeared as if a previous Nvidia driver installation prevented the drivers from installing properly after I upgraded Ubuntu.  Normal GPU usage is back down to 0% at the desktop.  As far as I can tell, everything is now operating correctly including the CCC.  Thanks for the assistance, everyone.

---

