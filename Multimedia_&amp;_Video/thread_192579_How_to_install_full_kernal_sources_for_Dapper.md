---
title: "How to install full kernal sources for Dapper?"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by dan4444 on 2006-06-08
Just upgraded to Dapper successfully and am trying to get my realtek alc880 sound card to work (I have no sound whatsoever so far and zero sound cards showing up). In running sudo ./configure for the alsa drivers, I get

The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)

I have seen numerous posts on this error and even on this error specifically for the realtek alc880, but after searching high and dry, I cannot locate exactly how to "install the package with full kernel sources" for my distribution (Dapper). Does anyone know the command line(s) for this?

---

### Post by jobezone on 2006-06-08
Since you're compiling a linux module (a driver for linux), you'll need the linux headers installed as well, but you don't need it's sourcecode (I think!).
Install the package **linux-headers-2.6-686**, or **linux-headers-2.6-k7**, etc., depending on which linux you're using.

---

### Post by dan4444 on 2006-06-09
Between just a minute ago and previously, I have installed the following "linux-headers" packages via synaptic:

linux-headers-2.6.15-23
linux-headers-2.6.15-23-386
linux-headers-2.6.15-23-686

And I still receive the same error I mentioned in my original post when I run ./configure on the alsa driver. Could multiple headers cause a conflict? Or is there something else I am missing here?

---

### Post by jobezone on 2006-06-09
I'm not sure if they conflict. Run in a terminal:
```
uname -r
``` to know the the version of linux you're using. Then only install the headers for that one, and remove the others.

If this still doesn't work, then maybe I'm wrong, and you need the source.
Install the package linux-source-* , where * is your version.

---

### Post by dan4444 on 2006-06-09
Thank you for your assistance. I ended up getting ./configure on my sound card driver to run successfully by specifying the source directory as a parameter (in my case, usr/src/linux-source-2.6.15). Didn't know that directory was the same content wise as the usual usr/src/linux directory. 

Anyhow, I received a new error the very next command I ran in my sound card driver installation process (sudo make), oh joy! Guess I will post that one in a new thread.

---

