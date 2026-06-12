---
title: "[SOLVED] Attempting to manually install NVIDIA driver"
date: 2008-07-01
forum: Multimedia Software
---

### Post by FlyingWV on 2008-07-01
Hello folks, I would greatly appreciate any help I could receive on an issue that I am having. Due to having a Creative X-Fi sound card, I've had to recompile my kernel to get the Creative Audio driver to install properly. Unfortunately, this process breaks the restricted nvidia driver which is automatically installed by Ubuntu.

uname -r
2.6.24.3-custom

As you can see, my kernel is 2.6.24.3-custom. I've downloaded the 64 bit (I'm running x86_64 version of Ubuntu) driver from NVidia's website and placed it into my ~/ directory. I then ctrl-alt-F1 to drop to the terminal, at which point I sudo /etc/init.d/gdm stop to kill the GUI.

At this point I sudo sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run to run the installer. The installer initiates, gives me the license agreement, then it states this:

No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site?

If I select yes, that fails.

Can I get any advice regarding this issue? Thank you very much.

---

### Post by ibutho on 2008-07-02
Just choose "no" when you get asked to download a precompiled kernel interface. The kernel will then proceed to build the driver.

---

### Post by FlyingWV on 2008-07-02
Thank you, I'm pretty new to Linux and was worried that might interfere with what I did to customize the kernel to make my sound work. You were correct, letting it compile an interface worked fine, and my video is now installed.

Thanks again.

PS Could you advise me on how to mark the thread solved? Thanks again

---

### Post by ibutho on 2008-07-02
> PS Could you advise me on how to mark the thread solved? Thanks again
The thread already appears as solved.

---

### Post by FlyingWV on 2008-07-02
Ah, yes, after I asked I looked in thread tools, doh... Thanks again.

---

