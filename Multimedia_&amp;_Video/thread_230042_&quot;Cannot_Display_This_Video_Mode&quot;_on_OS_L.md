---
title: "&quot;Cannot Display This Video Mode&quot; on OS Load/Unload"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by rgladwell on 2006-08-05
I'm running Ubuntu Dapper on my Dell Dimension 5150 with Radeon X600 256MB with Dell 1907FP Flat Panel Monitor. When I load or unload the operating system all I get is a "Cannot Display This Video Mode" error message.

I have configured my video card properly by installing the commericial flgrx driver. When I actually log into the GDM everything works fine at the correct resolution, but when I boot Ubuntu or shutdown I just get the black screen with the error message. What could be causing this.

I would be most grateful for any advice.

---

### Post by tseliot on 2006-08-05
Try point 13 of the Problems Section of this guide (even if it's for nvidia cards):
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

NOTE:
If that works you can then put "splash" back together with "vga=791" but this might not work

---

### Post by rgladwell on 2006-08-05
Thanks so much for that, adding the vga=791 to the kernel boot parameters did the trick and now Ubuntu displays the graphical boot/shutdown screens. Should I report this as a bug somewhere?

---

### Post by tseliot on 2006-08-05
Try on launchpad:
[https://launchpad.net/](https://launchpad.net/)

---

### Post by owenW on 2006-08-12
I too have encountered this problem when trying to run a live CD version of Kubuntu on a Dell Dimension 5150.  However, I'm completely new to Linux and so I didn't understand the solution that tseliot proposed.  I wonder if you could explain it in simple step by step terms for a complete newcomer.  I'm very keen to try out Linux but this problem is preventing me from getting it running on my PC.

---

