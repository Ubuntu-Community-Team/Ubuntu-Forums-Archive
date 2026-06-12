---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2012-02-23
forum: Multimedia Software
---

### Post by Tk007LwZFJW5ej on 2012-02-23
I have 11.10 x64. When I try to start quadrapassel from the command line, I get this error:

```

Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

```I have an nvidia video card. At some point, I had a proprietary driver installed for it. I tried to uninstall this driver a couple of times, but the uninstallation failed; I would still see the driver installed every time I went to Applications -> Settings -> Additional Drivers. The last time I tried was a few weeks ago. I looked again today, and, mysteriously, it's no longer installed  (I'm guessing it had something to do with the kernel being updated). I don't know if this is related to the glx problem or not; I'm bringing it up just in case. I was getting the same quadrapassel error when I had the driver.

From my searching so far, I know that I need to have "Load glx" and "Load extmod" in the modules section of xorg.conf.nvidia. They are already there, so I don't know what else to do.

Come to think of it, should the system be using xorg.conf or xorg.conf.nvidia? xorg.conf is nearly empty and doesn't have any load module statements in it.

---

### Post by IReadTheManual on 2012-08-06
You're out of luck

---

### Post by chkneater on 2012-08-15
your libglx.so file might be missing from your libraries.  Try: sudo apt-get install libglx.so

---

### Post by Tk007LwZFJW5ej on 2012-08-25
I forgot to mark this solved. I was able to get my games to start by deleting /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so and logging out/in. I had to go through the process again after my driver updated itself. I got the info from this thread: 

[http://www.linuxquestions.org/questions/linux-software-2/xlib-extension-glx-missing-on-display-0-0-a-930969/](http://www.linuxquestions.org/questions/linux-software-2/xlib-extension-glx-missing-on-display-0-0-a-930969/)

---

### Post by chkneater on 2012-08-29
Don't you need that extension in your Xorg.conf file?  I noticed it was in mine.

I wonder if sudo apt-get remove or purge would have fixed it by removing the config files, but you got it working so I wouldn't touch it!

---

### Post by Tk007LwZFJW5ej on 2012-08-30
> **chkneater said:**
> Don't you need that extension in your Xorg.conf file?  I noticed it was in mine.

I wonder if sudo apt-get remove or purge would have fixed it by removing the config files, but you got it working so I wouldn't touch it!

I think I said in the thread I linked that sudo apt-remove and purge didn't change anything? Too lazy to look. But I haven't had any problems since removing libglx.so.

---

