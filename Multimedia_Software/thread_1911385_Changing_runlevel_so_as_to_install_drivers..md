---
title: "Changing runlevel so as to install drivers."
date: 2012-01-18
forum: Multimedia Software
---

### Post by lovelyzoo on 2012-01-18
I've downloaded the nvidia linux drivers and I'm using their instructions, see here:
[ftp://download.nvidia.com/XFree86/Linux-x86_64/290.10/README/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86_64/290.10/README/README.txt)

In section 4A it says:
"You should also set the default run level on your system such that it will boot to a VGA console, and not directly to X."
I'd like to check if I've got this correct. Do I open /etc/init/rc-sysinit.conf and modify the line
env RUNLEVEL=

or will starting in single user mode be good enough?

---

### Post by Chronon on 2012-01-18
Can't you just do this?
[https://help.ubuntu.com/10.04/hardware/C/jockey.html](https://help.ubuntu.com/10.04/hardware/C/jockey.html)
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by lovelyzoo on 2012-01-21
> **Chronon said:**
> Can't you just do this?
[https://help.ubuntu.com/10.04/hardware/C/jockey.html](https://help.ubuntu.com/10.04/hardware/C/jockey.html)
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Thanks for your suggestion but 'System->Administration->Hardware Drivers' doesn't give me any recommendations.

I'm now trying to follow:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
but when I do so the command 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

won't execute, on account of xorg.conf not being present.

I've also tried running the second command
sudo apt-get install build-essential linux-headers-`uname -r`

which doesn't execute either ending with the message:
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any help much appreciated.

---

### Post by lovelyzoo on 2012-01-21
Ok, here are the results of my latest efforts:

Per this forum post I've tried to blacklist possible nvidia modules and uninstall existing ones:
[http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)
After doing so I do not get the option to boot to a terminal as the thread describes.

Next I try: 'jockey-text -l' which gives no output.

Finally I tried 'hwinfo --gfxcard' where I notice the following revealing lines:
  Driver Info #0:
    Driver Status: nouveau is active
    Driver Activation Cmd: "modprobe nouveau"

Ok, so nouveau is my driver. This is odd since as part of the blacklisting step above I added the line
blacklist nouveau
to /etc/modprobe.d/blacklist.conf

So, how can I prevent nouveau from running so that I can perform the graphics driver install?

---

