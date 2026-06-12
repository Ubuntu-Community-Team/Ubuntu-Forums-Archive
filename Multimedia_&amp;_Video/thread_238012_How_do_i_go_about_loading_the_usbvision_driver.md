---
title: "How do i go about loading the usbvision driver?"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by Hawkowl on 2006-08-17
I'm completely new to this stuff..
How do i install a tar.gz or whatever file after i download it to my desktop?
Thanks..

---

### Post by louis_nichols on 2006-08-17
Well... first you uncompress it with whatever method you find easier.

Next, you open a terminal window and navigate your way to the folder where all this is extracted.

Then, you issue the following commands, in order:

```
./configure
make
make install
```
Sometimes, the configure part might be missing, or replaced with an ./autogen.sh. Sometimes, all these commands are included in a script. But this is the general rule.

Of course, to be able to build applications, you need the tools, so you have to install the package build-essential from synaptic. Also, each source code requires some dependencies to be met. In your particular case, it would mean installing the package kernel-headers and maybe linux-source.

Now, the above is normally enough to install a package. This goes for usbvision too. Except you have to load the driver to be able to use it. This is done with the command:

```
sudo modprobe usbvision
```

---

### Post by Hawkowl on 2006-08-17
Thanks for the tips.
I'll give it a go

---

