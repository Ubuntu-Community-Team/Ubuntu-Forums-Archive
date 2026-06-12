---
title: "Trying to compile the Vbox kernel modules...can't?"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jim March on 2010-09-03
I just upgraded from Lucid-32bit, had Virtual full-tilt edition off of their site loaded and running.  Post Maverick update, did:

---
jim@jim-lappy:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for jim: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
jim@jim-lappy:~$ 
---

According to that log, it can't find kernel sources so I loaded them in Synaptic - seemed to load there but I still get:

---
Error! Your kernel headers for kernel 2.6.35-19-generic cannot be found at
/lib/modules/2.6.35-19-generic/build or /lib/modules/2.6.35-19-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.35-19-generic package.
Failed to install using DKMS, attempting to install without
Makefile:159: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
---

Like help?

:(

Thanks...

---

### Post by jfernyhough on 2010-09-03
Do you have the kernel headers installed? Have you rebooted since upgrading?

Bear in mind the VirtualBox additions won't work properly yet anyway (not compatible with the latest Xorg).

---

### Post by Jim March on 2010-09-03
Yes, as I said, I installed package linux-headers-2.6.35-19-generic - and I've also tried rebooting.

And I know about the guest editions issue but I can live without that for now.

Does anybody know why it won't compile?

---

### Post by Jim March on 2010-09-04
Anybody know why this won't compile?  Getting desperate here, I need to do a demo in court on Sept. 10th.  I can live with 800x600 (no guest additions) but I have to compile the kernel module...

---

### Post by cariboo on 2010-09-04
Seeing as you did an upgrade, did you run:

```
sudo apt-get -f install
```

just to make sure there wasn't anything not installed?

You're a braver man than I, using a pre-release version for business and in public. :)

---

### Post by Jim March on 2010-09-04
Ah.  Good thought but no...no problem there.  Checked Synaptic again, the kernel module vbox is complaining about lacking is certainly there.

I'm stumped.

---

