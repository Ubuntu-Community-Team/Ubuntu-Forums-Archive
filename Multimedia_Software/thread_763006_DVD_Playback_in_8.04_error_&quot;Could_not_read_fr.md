---
title: "DVD Playback in 8.04 error: &quot;Could not read from resource&quot;"
date: 2008-04-22
forum: Multimedia Software
---

### Post by diablo75 on 2008-04-22
I just finished installing the mediabuntu sources and used synaptic to install the libdvdcss2 package after.  I have one PC that plays no problem, but another laptop that says "An error occurred: Could not read from resource"

I've tried reinstalling libdvdcss2 but it didn't help.

What should I try now?

---

### Post by cor2y on 2008-04-22
In windows the dvd playback worked correct?
Try installing libdvdread libdvdnav and replace totem-gstreamer with totem-xine see if that helps.
You will have to remove totem-gstreamer manually since in 8.04 you can have both installed at the sametime now.

---

### Post by flerchjj on 2008-09-07
It looks like the Restricted Format installation and libdvdcss2 were broken at some point in 8.04 (among other things). Mediabuntu has a libdvdcss that appears to fix the problem with DVD playback.

It looks like you will have to go to Medibuntu and/or follow the instructions at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

basically you must type the appropriate statements below in the Terminal

# for i386:

```
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

# for amd64:

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

# for powerpc:

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_powerpc.deb
```

---

