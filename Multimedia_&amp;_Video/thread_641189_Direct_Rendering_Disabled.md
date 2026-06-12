---
title: "Direct Rendering Disabled"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by xerxesb on 2007-12-15
Howdy,

In my attempts to fix WoW to work under Gutsy, i think i've borked something in my 3d setup, but cant find a way to fix it.

glxgears reports that its rendering ~1000fps, but it looks like 1-2fps at best. Frets on Fire and TORCS also suffer the same kind of problems.

the key to the problem seems to be with the 965 DRI module, and if i run glxinfo with debug info i get the following error:

> xerxes@laptop-linux:~$ glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.8.0 i965 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL error: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i965_dri.so
libGL: XF86DRIGetClientDriverName: 1.8.0 i965 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL error: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i965_dri.so
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
s


My laptop is a Compaq 6710b (Santa Rosa) with an Intel integrated GM965 video chipset. 

happy to provide any other info - i've googled and turned up no luck. hopefully someone here has come across this problem or can suggest ways to investigate and fix

Thanks,
x

---

### Post by Stemp on 2007-12-15
Hi,

What about installing/reinstalling libgl1-mesa-dri ?

---

### Post by xerxesb on 2007-12-15
yep tried that.

used synaptic to do a complete removal of mesa-dri, restarted and then re-installed, restarted and still no luck

---

### Post by Stemp on 2007-12-15
And what about xserver-xorg-video-intel ?

---

### Post by xerxesb on 2007-12-15
yep - same thing too. uninstall video-intel, reboot into vesa, re-install video-intel and the problem still exists.

i just saw a thread which mentions something called AIGLX?

just more info in case it helps...here is the relevant output from my xorg.0.log

> (WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0


---

### Post by Stemp on 2007-12-15
No problems with AIGLX here, these warnings are common.
I'm sorry but I have no more ideas :(

---

### Post by xerxesb on 2007-12-15
i found  this link ([http://www.mail-archive.com/linux-users@it.canterbury.ac.nz/msg46589.html]("http://www.mail-archive.com/linux-users@it.canterbury.ac.nz/msg46589.html")) which indicates that the problem *might* be caused by a mismatched version of mesa-dri and mesa-glx....

how can i check, and if it is a problem rollback to a previous version of everything?

---

### Post by Stemp on 2007-12-15
```
stemp@caderousse:~$ apt-cache policy libgl1-mesa-dri
libgl1-mesa-dri:
  Installé : **7.0.1-1ubuntu3**
  Candidat : 7.0.1-1ubuntu3
 Table de version :
 *** 7.0.1-1ubuntu3 0
        500 http://archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status
stemp@caderousse:~$ apt-cache policy libgl1-mesa-glx
libgl1-mesa-glx:
  Installé :** 7.0.1-1ubuntu3**
  Candidat : 7.0.1-1ubuntu3
 Table de version :
 *** 7.0.1-1ubuntu3 0
        500 http://archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status

```

Check if it's the same versions

---

### Post by xerxesb on 2007-12-15
bugger. that's not the problem :(

> xerxes@laptop-linux:~$ apt-cache policy libgl1-mesa-dri
libgl1-mesa-dri:
  Installed: 7.0.1-1ubuntu3
  Candidate: 7.0.1-1ubuntu3
  Version table:
 *** 7.0.1-1ubuntu3 0
        500 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status
xerxes@laptop-linux:~$ apt-cache policy libgl1-mesa-glx
libgl1-mesa-glx:
  Installed: 7.0.1-1ubuntu3
  Candidate: 7.0.1-1ubuntu3
  Version table:
 *** 7.0.1-1ubuntu3 0
        500 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status


---

### Post by Stemp on 2007-12-15
```
stemp@caderousse:~$ ls -l /usr/lib/dri/i965_dri.so
-rw-r--r-- 1 root root 2402568 2007-10-13 02:38 /usr/lib/dri/i965_dri.so
```

or maybe intel driver ? 
```
stemp@caderousse:~$ apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installé : 2:2.1.1-0ubuntu9
  Candidat : 2:2.1.1-0ubuntu9
 Table de version :
 *** 2:2.1.1-0ubuntu9 0
        500 http://archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by xerxesb on 2007-12-15
```
xerxes@laptop-linux:~$ ls -l /usr/lib/dri/i965_dri.so
-rw-r--r-- 1 root root 2402568 2007-10-13 10:38 /usr/lib/dri/i965_dri.so

xerxes@laptop-linux:~$ apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: 2:2.1.1-0ubuntu9
  Candidate: 2:2.1.1-0ubuntu9
  Version table:
 *** 2:2.1.1-0ubuntu9 0
        500 http://au.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status
xerxes@laptop-linux:~$ 

```

:(

Looks like i'm no closer - they're the same settings as yours, stemp

---

### Post by Stemp on 2007-12-15
```
stemp@caderousse:~$ ls -l /usr/lib/xorg/modules/drivers/intel_drv.so
-rw-r--r-- 1 root root 300600 2007-10-15 12:39 /usr/lib/xorg/modules/drivers/intel_drv.so
```

The driver maybe ?

---

### Post by xerxesb on 2007-12-15
```
xerxes@laptop-linux:~$ ls -l /usr/lib/xorg/modules/drivers/intel_drv.so
-rw-r--r-- 1 root root 300600 2007-10-15 20:39 /usr/lib/xorg/modules/drivers/intel_drv.so

```

---

### Post by Stemp on 2007-12-16
Well, well, except you're not living in the same timezone as I do, I see no difference :D

You don't remember the documentations you used for WoW ?

---

### Post by xerxesb on 2007-12-23
FWIW, and for the future reference of other people, i managed to fix this problem by uninstalling the fglrx package.

i dont remember intsalling it myself, and cant udnerstand why it would be installed on my machine, but removing the package and then re-installing MESA-DRI worked a treat

thanks for your help, stemp!

---

