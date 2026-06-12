---
title: "ATI releases 10.1 driver"
date: 2010-01-28
forum: Multimedia Software
---

### Post by markbuntu on 2010-01-28
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by markbuntu on 2010-01-29
Packaging scripts fo karmic are broken in this release but the installer works.

If you want to build packages for karmic you need to do it this way:
```

chmod +x ./ati-driver-installer-10-1-x86.x86_64.run

./ati-driver-installer-10-1-x86.x86_64.run --extract

cd fglrx-install.xxxx/arch/x86_64/usr/lib64/
(Replace "fglrx-install.xxxx" with the name of the directory that the installer created on your system)

ln -s libatiuki.so.1.0 libatiuki.so.1

cd ../../../..

sudo ./ati-installer.sh 10.1 --buildandinstallpkg Ubuntu/karmic


```

Don't forget to 

aticonfig --initial -f

If you want to learn more about that you can go here:

[http://www.phoronix.com/forums/showthread.php?t=21739&page=6](http://www.phoronix.com/forums/showthread.php?t=21739&page=6)

---

### Post by Icarus315 on 2010-01-29
Thank you for the tip!  Already done :)  By the way, your avatar shows you are an avid GIMP user!  Heheh, joke, but you won't accept PM's so I had to post it here! ;)

---

### Post by markbuntu on 2010-01-29
Yes, I am the gimp master...

btw, do not forget to uninstall old drivers before installing new ones or kernel updates will leave you in driver hell.

---

### Post by Icarus315 on 2010-01-29
Oh noes.  I did the build and install routine without uninstalling the previous (didn't know you could, doesn't package manager take care of that?).  Will I regret it too bad?  Anything I should do?

---

### Post by markbuntu on 2010-01-29
What you can do is just remove all fglrx with apt-get purge fglrx* or something ike that (it has been a long time since I got into that trouble) and then reinstall the latest driver.

The problem is that old version kernel modules are lying about and that confuses the new kernel build because it sees multiple versions so it does not build them at all. It is possible to just purge the kernel modules but I don't know how you do that. This will only show up when a new kernel comes down as an update.

Anyway if you used hardware manager to get the old driver you can use Synaptic package manager and search fglrx and choose remove completely for all the fglrx packages it finds. If you got the driver from ati site then there is a script usr/share/ati/fglrx-uninstall that works very well.

sudo sh /usr/share/ati/fglrx-uninstall

(If the Unbuntu packagers left this in it would make upgrading the driver a little easier) The reason that the package manager does not take care of this little problem is because the new drivers are not packaged in a way that is trackable by apt. ie not in a repository (a ppa could fix this but the ubuntu packagers seem oblivious) Anyway, the installer notes specifically tell you to remove old drivers before installing new ones... so everyone's *** is covered for that.

---

### Post by Icarus315 on 2010-01-29
Ok excellent.  Thank you for the advice.  What I will do is clean up my packages if it is a matter of new kernels being confused as to which to use.  Synaptic here I come!  Also, it sound like *if* I don't do it right then I can in the future when the day comes just boot into the recovery console and command-line install the driver at that time?!  Thank you for giving me a bit more knowledge: at the very least if it goes south in the future I'll have somewhere to start with Google ;)

---

### Post by Icarus315 on 2010-01-29
Well, I went into synaptic and only saw *current* fglrx packages so I left those alone.  Then used Ubuntu Tweak to clean up all caches and such including extra kernels.  I now have 1 kernel (+recovery option) and MemTest in Grub and that's it.  When building the GRUB menu to get to just having one kernel all the DKMS stuffage ran so I'm hoping I'm good.  If not I'll find out when a new kernel appears in the Update Manager.  If I get a failed boot after that I'll go straight to a command line install of the Ati driver.  Thank you for the tips, a little bit more for me ;)

---

### Post by TheWhiteDemon on 2010-01-30
> **markbuntu said:**
> Packaging scripts fo karmic are broken in this release but the installer works.

If you want to build packages for karmic you need to do it this way:
...


I'm confused as to the issue here. The 10.1 driver installed fine for me with Karmic 64 bit. What exactly in the scripts was broken for you?

---

### Post by markbuntu on 2010-01-30
> **TheWhiteDemon said:**
> I'm confused as to the issue here. The 10.1 driver installed fine for me with Karmic 64 bit. What exactly in the scripts was broken for you?

Did you build the packages manually or just run the installer?

---

### Post by TheWhiteDemon on 2010-01-30
> **markbuntu said:**
> Did you build the packages manually or just run the installer?

Ah, I guess I didn't read your whole post. I understand now.

---

### Post by cencorot_91 on 2010-01-31
can somebody tell me how to remove this driver?

---

### Post by Icarus315 on 2010-01-31
> **cencorot_91 said:**
> can somebody tell me how to remove this driver?

If you used the build option to install it (generate .deb packages, let synaptic - well dpkg - deal with them: which is what I always do) then you can just go into synaptic and search for "fglrx" and remove those packages.  I've never done it so you may want to wait for further advice.  The only "gotcha" I can for see is that perhaps on reboot your X Desktop Server might not give you a graphical desktop.  If you are worried about this, copy down or have access to the instructions to perform the driver install in the recovery console to reinstall the Ati driver from the command line once you are there.

If you installed via the ati-installer (not .deb packages) then you can check if there is a /usr/share/fglrx/ati-uninstall.sh (or something similar) and run it.  Reboot, as above X may be borked: reinstall driver.

The best option is to have access to another computer: you can attempt these things and then depending on the results have access to this board or another for where to go from there.

---

### Post by Icarus315 on 2010-01-31
Well, considering it is [stable]("http://freesoftnews.com/archives/19737") I went ahead and did a manual update to the 2.6.32.7 kernel today.  Nothing broke, Ati driver is fine.  You can always find the latest Ubuntu kernels [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), stay away unless you don't mind reinstalling your system like me.  So, I guess the lesson to learn from this is that if you use the build packages method of installing the Ati driver (which I always do) vs the "clobber over everything" normal install then the issue of kernel updates is mitigated?

---

### Post by Melcar on 2010-01-31
Nowadays, the fglrx module usually carries over when you change kernels (so no, how you install doesn't matter).  Doesn't always work of course, so it's still better to re-install the drivers if you change kernels.

---

### Post by Icarus315 on 2010-01-31
> **Melcar said:**
> Nowadays, the fglrx module usually carries over when you change kernels (so no, how you install doesn't matter).  Doesn't always work of course, so it's still better to re-install the drivers if you change kernels.

Right on, thank you for the extra information!

---

