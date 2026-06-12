---
title: "Loading source code or installing video/audio drivers"
date: 2010-02-01
forum: Mythbuntu
---

### Post by Caps18 on 2010-02-01
So, I upgraded my system, but am running into the same problems that I have had with my previous motherboard.  I am running 7.10, but am now using the old-releases.ubuntu.com/ubuntu to allow apt-get to run.  However, I'm not doing the auto builds since I am still running 7.10 since I like it and it works.


The issue now is that the nVidia installer from their website wants the source code to build the right packages for this machine, however, I do not have the src directory with the source code that it is looking for.  Is there some way to give this too it now?

And I'll have to look arond for how to get the bilt-in audio card loaded.  Any tips would be healpful though.  It is a ASUS M4N78 Pro board.

Thanks

---

### Post by klc5555 on 2010-02-02
> **Caps18 said:**
> So, I upgraded my system, but am running into the same problems that I have had with my previous motherboard.  I am running 7.10, but am now using the old-releases.ubuntu.com/ubuntu to allow apt-get to run.  However, I'm not doing the auto builds since I am still running 7.10 since I like it and it works.


The issue now is that the nVidia installer from their website wants the source code to build the right packages for this machine, however, I do not have the src directory with the source code that it is looking for.  Is there some way to give this too it now?

And I'll have to look arond for how to get the bilt-in audio card loaded.  Any tips would be healpful though.  It is a ASUS M4N78 Pro board.

Thanks

You likely need the "linux-source" package and the "linux-headers" package from 7.10 for whatever the exact version is of the kernel you happen to be running. If you've never compiled anything on your 7.10 Mythbuntu installation, these packages would not have been installed by default.

Also, from what little I remember, the Asus mobo has a Via AC97 audio chip on it, which 7.10 supported out-of-the box. However, I remember that at installation 7.10's Alsa would always default to the wrong sound device (one of the sound chips on a tuner card), and so the system would have no sound until the correct default Alsa device (the "via" chip) was set from the command line.

---

### Post by Caps18 on 2010-02-02
Where do I find  the linux-source package and the linux-headers package?  Are they on the CD that I can copy to /usr/src (is that the right place...)?  Or do I need to download them from the old-releases.ubuntu.com site?

Thanks

---

### Post by klc5555 on 2010-02-02
[http://old-releases.ubuntu.com/ubuntu/pool/main/](http://old-releases.ubuntu.com/ubuntu/pool/main/)  will have the exact antiquated packages you need in there somewhere. Just have to dig around for them.

But again, you'll need to use the linux-source- package and linux-header- package that correspond to the exact version number (and architecture) of the kernel you happen to be running.

---

### Post by Caps18 on 2010-02-02
[http://old-releases.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/](http://old-releases.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/)

I found the linux-source package for my kernel, but I do not see the linux-header package anywhere?

Can I just download all those files into /usr/src ?  Or is there some other way to do this?

---

### Post by Caps18 on 2010-02-02
Update...

If you put this in the "software sources" application, URI =[http://old-releases.ubuntu.com/ubuntu/pool/](http://old-releases.ubuntu.com/ubuntu/pool/) Distribution = gutsy (for 7.10) 
Components = main restricted universe multiverse

(I also made another one with the same URI and Distribution but the components = free non-free )

It will find it and download what you need.

Thanks!

---

### Post by Caps18 on 2010-02-03
One more thing to fix now...

I have tried to download the soundcard drivers from ASUS's website.  I run the install.sh script, and I get this error message.

You haven't installed the kernel source.

nVidia didn't seem to have a problem locating the source.  Is it looking for a newer source/kernel version than the one I have?  Or is it looking in the wrong place?  The source code is in /usr/src, the install script is looking in /lib/modules/$KERNEL_VER/source and /lib/modules/$KERNEL_VER/build

Thanks

---

### Post by klc5555 on 2010-02-03
> **Caps18 said:**
> One more thing to fix now...

I have tried to download the soundcard drivers from ASUS's website.  I run the install.sh script, and I get this error message.

You haven't installed the kernel source.

nVidia didn't seem to have a problem locating the source.  Is it looking for a newer source/kernel version than the one I have?  Or is it looking in the wrong place?  The source code is in /usr/src, the install script is looking in /lib/modules/$KERNEL_VER/source and /lib/modules/$KERNEL_VER/build

Thanks

I'm surprised you have to compile anything for via ac97 support on a 2.6.22 kernel. But that said, your choice is evidently to modify the shell script to point to your actual source directory, or to simlink the directory name the script is looking for to your actual source directory.

---

