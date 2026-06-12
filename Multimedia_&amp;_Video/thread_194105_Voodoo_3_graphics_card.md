---
title: "Voodoo 3 graphics card"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by andgeo000 on 2006-06-11
I've just installed the latest version of Ubuntu onto an old computer.  I have it running now, but the resolution is very low and can not be raised.  I've deteremined that the computer uses is 3dfx Voodoo 3.  I've searched, but I can't find a driver for it that works in Linux.
Please help me.  I am not sure what to do, have I missed something?

---

### Post by dermotti on 2006-06-11
Interesting :-)

---

### Post by mzembe on 2006-06-11
According to this [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-tdfx/+bug/35610]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-tdfx/+bug/35610")one guy, you need to find and install libglide3.

---

### Post by mzembe on 2006-06-11
There's a special mesa library too, for the glide cards. libgl1-mesa-glide3

---

### Post by andgeo000 on 2006-06-11
Ok, I've downloaded the libglide3, but when I run it, it says: "Error: Dependency not satisfiable: xlibs" for its status in the Package Installer.  What does this mean?

The package says "NOTE: You'll need the /dev/3dfx kernel driver to use this library."  Is this the problem?  Where do I get that?
Thanks.

---

### Post by Jonas54 on 2006-06-11
I had the same issue after installing Ubuntu on my old computer that has a Voodoo Banshee. This guide worked for me: [https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

Be forewarned though, I ran the autodetect script first and it resulted in my LCD not being able to display the output. I then had to reboot into the recovery console and edit the xorg.conf file following the instructions on that page to change my HorizSync and VertRefresh settings.

---

