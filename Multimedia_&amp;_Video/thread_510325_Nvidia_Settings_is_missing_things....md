---
title: "Nvidia Settings is missing things..."
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by osxdude on 2007-07-26
I have nvidia-settings installed as part of the 9755 driver. One problem: there is no card configuration pages in the thing!

What can I do to get it back?

Attached is the terminal output and the nvidia-settings itself.

---

### Post by dabl on 2007-07-26
Yeah, I remember that happened to me once.  I think what you have is a half-installed driver. :(

You could try ```
sudo nvidia-xconfig
``` and see what happens, but probably you're back to removing and re-installing the driver. :(

If the newest driver (100.14.11) will run your card, using Envy might be the easiest way to get going again. It's in the repo for 64-bit, or else you can download the .deb file from here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by osxdude on 2007-07-26
I got it to show up...thanks. But I wanted to use it for seperate X screens...but it is not working still...

It does not seem to see the changes after an X restart.

---

### Post by dabl on 2007-07-26
To make changes in nvidia-settings permanent in xorg.conf, you have to run it in Super User (aka root) mode. In the console window, ```
sudo nvidia-settings
```

Now do "detect display", set your resolution and refresh rates, and whatever, then click "Save To X Configuration File" and click "save" in the little window that pops up.  Now it will stick! :popcorn:

---

