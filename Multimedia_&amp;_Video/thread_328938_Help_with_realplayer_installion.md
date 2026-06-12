---
title: "Help with realplayer installion"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by Gumper on 2006-12-31
I installed Realplayer10 according to the 6.10 edgy steps on [[COLOR="Blue"]Ubuntu's commnuity[/COLOR] ]("http://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods") site but when I try to run it from the command line i get the following message: 

error while loading shared libraries: libgdk-x11-2.0.so.0: cannot open shared object file: No such file or directory

could anyone point me in the right direction to correct this problem. Also, the installation placed a realplayer icon in "sound and video" but if i try to open from there, nothing happens.

During installation I'm also told the following:
Some required libraries seem to be missing from your system.  Installation
can continue without them, but you will be unable to run the HelixPlayer
without them.  You will need to install them (or if they are already present
you may simply need to update your system's library paths or LD_LIBRARY_PATH
environment variable.
        GTK+ 2.0 (libgtk-x11-2.0.so)
        ATK 1.0 (libatk-1.0.so)
        Pango 1.0 (libpango-1.0.so)
        PangoX 1.0 (libpangox-1.0.so)
continue with installation? [y/n]: 

I tried to find these in synaptics, but couldn't locate some of them. How do i install them if i cant find them?

This is on a 64bit machine.

Thanks for the help.

---

### Post by bruenig on 2006-12-31
You may not have a very good sources.list, perhaps paste that in here, it is located at /etc/apt/sources.list.

Besides that, I am not too sure on 64 bit and whether real player can run on it or not. But as for those libraries that it asks for, you can install those by copying and pasting the following code.

GTK+2.0
```
wget http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.10.6-0ubuntu1_amd64.deb
sudo dpkg -i libgtk2.0-0_2.10.6-0ubuntu1_amd64.deb
```

ATK 1.0
```
wget http://mirrors.kernel.org/ubuntu/pool/main/a/atk1.0/libatk1.0-0_1.12.3-0ubuntu1_amd64.deb
sudo dpkg -i libatk1.0-0_1.12.3-0ubuntu1_amd64.deb
```

Pango 1.0
```
wget http://mirrors.kernel.org/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.14.5-0ubuntu1_amd64.deb
sudo dpkg -i libpango1.0-0_1.14.5-0ubuntu1_amd64.deb
```

These are all for amd64 but again I am not too sure on realplayer for amd64 if it is even possible. Hopefully these things that I posted don't have unsatisfied dependencies themselves, dependency hell is no fun. Paste your sources.list regardless because it would seem that you should have these things in synaptic.

---

