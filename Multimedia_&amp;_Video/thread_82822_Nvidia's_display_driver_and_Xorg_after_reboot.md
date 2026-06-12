---
title: "Nvidia's display driver and Xorg after reboot"
date: 2005-10-27
forum: Multimedia &amp; Video
---

### Post by DeCrys on 2005-10-27
This might be a silly overlook by me, but still the problem persists on both 5.04 and 5.10.

I have a custom kernel (2.6.12), and there is seems to be a problem with NVIDIA's drivers (from NVIDIA). After installing the 7676 drivers, X starts up normally. After rebooting X won't start (libGL errors), the /usr/lib/tls is emptied, and the symlink from libGL.so.1 to NVIDIA's libGL is also deleted. This is trivial, but after restoring the tls folder and symlinking the libGL, Xorg still fails to start (this time without errors). Xorg.conf works and the required modules are loaded without errors. I compiled the kernel module with gcc-3.4 using the installer. 

The driver installer's sanity check does not find any problems either  (NVIDIA-Linux-x86-1.0-7676-pkg1.run --sanity).

The card in question is XFX GeForce 6800 GT, which works with the restricted-modules package and the first time before a reboot. I have only one kernel installed, so there should not be any conflicts between the GL libraries.

I also remember having this same problem with Debian a while back under a similar configuration, but on Fedora this has worked fine in the past (FC2). Using a stock kernel is not a preferred option.

A nvidia-bug-report can be found at [http://www.keen-edge.com/users/lropelin/nvidia-bug-report.log](http://www.keen-edge.com/users/lropelin/nvidia-bug-report.log)

Any ideas or prods toward my mistake will be welcomed.

---

### Post by marx1984 on 2005-10-30
check your /etc/init.d for nvidia-glx. if it's there remove it or remove execute permissions, chmod -x nvidia-glx and rebuild your nvidia driver. The reboot should sustain the nvidia driver and X should work. also remove nvidia-glx with apt-get and then do what i mentioned above.

Read this: [http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

---

### Post by DeCrys on 2005-10-30
The nvidia-glx was removed earlier with the former kernel. Strangely enough after disabling /etc/init.d/nvidia-glx, X started working after a reboot. I wonder what went wrong the last time I tried this, but now it works. Thanks anyway.

---

### Post by YetZero on 2005-11-02
This solution also applies to the binary called [FONT="Courier New"]nvidia-glx-legacy[/FONT], if that helps someone else. Anyway, I'd like to know what was the problem from the beggining, if someone knows.

---

### Post by tseliot on 2005-11-03
[QUOTE=YetZero]This solution also applies to the binary called [FONT="Courier New"]nvidia-glx-legacy[/FONT], if that helps someone else. Anyway, I'd like to know what was the problem from the beggining, if someone knows.[/QUOTE]
The problem should be a conflict between Ubuntu's nvidia-glx module and the one the nvidia installer compiles. For this reason I suggest to remove Ubuntu's one (as described in my guide).

---

