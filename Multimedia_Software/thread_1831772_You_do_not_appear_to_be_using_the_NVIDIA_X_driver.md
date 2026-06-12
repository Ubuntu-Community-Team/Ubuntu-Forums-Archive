---
title: "You do not appear to be using the NVIDIA X driver"
date: 2011-08-23
forum: Multimedia Software
---

### Post by fester225 on 2011-08-23
Lucid 10.04

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run nvidia-xconfig' as root), and restart the X server."

Yes, I know. This problem has been posted to death, but now I've got it.

The nvidia-installer.log provides the following;

 Kernel messages: 
   [   15.006099] NVRM: API mismatch: the client has the version 280.13, but 
   [   15.006100] NVRM: this kernel module has the version 195.36.24.  Please 
   [   15.006101] NVRM: make sure that this kernel module and all NVIDIA driver 
   [   15.006102] NVRM: components have the same version. 


What is Nvidia's idea of a kernel? How do I install what it wants?

---

### Post by papibe on 2011-08-23
How did you install the proprietary Nvidia driver? From the Hardware drivers or from a Nvidia's site download?

Regards.

---

### Post by fester225 on 2011-08-23
> **papibe said:**
> How did you install the proprietary Nvidia driver? From the Hardware drivers or from a Nvidia's site download?

Regards.


I downloaded the driver from the website, and loaded it from a command line.

---

### Post by papibe on 2011-08-23
That requires a little more attention to your updates. Every time you upgrade your kernel, the nvidia driver may stop working and you'll have to fixed manually.

Here's a helpful [thread]("http://ubuntuforums.org/showthread.php?t=835573&highlight=nvidia+kernel") that can guide you to do that.

If don't want the hassle, or don't feel competent enough to keep up with that, I would recommend to install the driver maintained by Ubuntu (from the Hardware drivers). You would have to uninstall the one you have first.

Regards.

---

