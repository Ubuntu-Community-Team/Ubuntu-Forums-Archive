---
title: "API mismatch, X server doesn't start"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by ulpiano on 2007-08-04
Hi:
I was trying to solve a problem with Beryl. I installed nvidia-glx-new package and when I restarted my computer the Xserver didn't start. The message is "Error: API mismatch. The nvidia kernel module has the version 1.0-7184 but this X module has the version 1.0-9631" I tried to reinstall the nvidia-glx package via apt-get. When it was ready, I restarted my computer but the X server didn't work again. How can I restore the X server from console? Please, I don't want to reinstall all.
I use a nvidia geforce 440 MX (64 Mb RAM), and I use Festy.
Thanks.

PD: Sorry, English is not my mother tongue.

---

### Post by benx009 on 2007-08-04
do you know whether or not you were using the nvidia-legacy drivers before you had this problem?

---

### Post by ulpiano on 2007-08-04
No, I don't. Before the problem started, I was using nvidia-glx and the restricted kernel modules. Thanks anyway.

---

### Post by ulpiano on 2007-08-04
Hi:
I can X server work. I change the device section of xorg.conf. Instead of "nvidia" I put "nv" in driver line. It worked, but I don't have 3d acceleration. When I use the restricted drivers manager to activate the nvidia driver, the problem returns: the X server doesn't work with the same error message. I was searching for the right package using Synaptic, but I don't know which is the right one. My video card is a GeForce4 MX 440 AGP 8x with 64Mb.

---

### Post by ulpiano on 2007-08-04
Well, I can solve the problem partially. I installed the legacy-nvidia-glx package and I got the 3d acceleration, but I didn't get GLX extension. Any idea?

---

### Post by benx009 on 2007-08-04
what do you mean by the GLX extension?  are you talking about the glx extensions you see when you type "glxinfo" in a terminal?

---

### Post by ulpiano on 2007-08-05
No, the gears you get when you type "glxgears" in a terminal. Some hours ago, I got the GLX extension work. I had to modify xorg.conf to get it. I've been searching about the mismatch issue. This was reported en launchpad as a bug. Tomorrow I will try again.
Bye

---

### Post by ulpiano on 2007-08-11
I want to thank to Alberto Milone. Envy was the solution to the API mismatch. Thanks very much. The link to the Alberto Milone's blog is in one of the sticky forums.
Bye.

---

