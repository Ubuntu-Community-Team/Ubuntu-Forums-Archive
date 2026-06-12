---
title: "VirtualBox OSE vboxdrv Not Found"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aaaantoine on 2011-04-26
Just upgraded to Natty yesterday (yes, I bit the bullet ahead of time like a fool -- I really wanted to try out Unity).

I'll start the train of thought from the moment I discovered a problem.

I tried to run my Windows XP guest in VirtualBox.  I got this error:

> 
Failed to open a session for the virtual machine Windows.

The virtual machine 'Windows' has terminated unexpectedly during startup with exit code 1.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {662c175e-a69d-40b8-a77a-1d719d0ab062}


In the same instance, I got another pop-up saying...

> 
Kernel driver not installed ( rc=-1908 )

Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root.


So I checked it out.  virtualbox-ose-dkms is already installed.  So I opened up a terminal and tried what it said...

```
$ sudo modprobe vboxdrv
FATAL: Module vboxdrv not found.
$
```

Okay, the module is missing.  So I looked up how to rebuild the module in Ubuntu, and figured out it's a lot like how it's done in Arch.

```
$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
$ 
```

...Huh.  Really?

```
$ ls /etc/init.d
. . .
fancontrol              rc                          urandom
firestarter             rc.local                    virtualbox-ose
gdm                     rcS                         winbind
. . .

```

Well there's that, at least.  Let's see what I can do with it.

```

$ sudo /etc/init.d/virtualbox-ose setup
Usage: /etc/init.d/virtualbox-ose {start|stop|stop_vms|restart|force-reload|status}
$ sudo /etc/init.d/virtualbox-ose start
 * Starting VirtualBox kernel modules                                            
 * No suitable module for running kernel found
                                                                         [fail]
$ sudo /etc/init.d/virtualbox-ose status
VirtualBox kernel module is not loaded.
$ 

```

I tried removing and reinstalling both virtualbox-ose and virtualbox-ose-dkms, but neither the vboxdrv module nor the script for generating the vboxdrv module showed up.

...And now, I'm stuck.

I would like to avoid having to download the package from Oracle, and in the meanwhile I'll just use my laptop's Windows VM to do what I need to do.

But, help would be very much appreciated. :)

---

### Post by dino99 on 2011-04-26
i'm using virtualbox from Oracle (not from synaptic) and it works smootly. note: always remove/purge the previous install  ( not upgrading)

---

### Post by aaaantoine on 2011-04-26
Something I noticed when using apt-get to install virtualbox-ose-dkms...

```
Setting up virtualbox-ose-dkms (4.0.4-dfsg-1ubuntu4) ...
Loading new virtualbox-ose-4.0.4 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-8-generic-pae
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

```

Now why the heck wasn't linux-source installed?  Shouldn't linux-source (and similar packages) provide a dependency for virtualbox-ose-dkms?

Edit: Okay, it's throwing that error even after linux-source is installed.

---

### Post by aaaantoine on 2011-04-27
I guess nobody else is having this problem with virtualbox-ose?  Or maybe I'm the only one trying to get virtualbox-ose to work...

---

### Post by tekstr1der on 2011-04-27
Up until the 4.0.6 release recently (and .deb installer), I'd been using virtualbox-ose from the repos without issue. Simply installing the package pulled in the dkms package which built the kernel module without any further user interaction.

I dual boot with arch linux and share virtual machines between the two OS's. There's no reason to use the arch installation method under ubuntu due to dkms. Did you purge all configuration files when you reinstalled?

---

### Post by dino99 on 2011-04-27
so have you linux-source-2.6.3x installed ?

---

### Post by aaaantoine on 2011-04-27
So uh... What's the difference between "linux", "linux-generic", and "linux-generic-pae"?  It seems out of the three I have linux-generic-pae installed.

I had installed the source for the standard linux kernel, but not generic-pae.

Rather than change my kernel and risk screwing something up, I looked at the available packages relating to linux-generic-pae and found the relevant linux-headers package was not installed.  Installing this -- then reinstalling virtualbox-ose-dkms -- fixed the issue.

Thank you for your assistance.

---

### Post by tekstr1der on 2011-04-27
> **dino99 said:**
> so have you linux-source-2.6.3x installed ?

Not sure who this is directed toward, but no, I don't. Either way, the kernel source is not needed by the OP for the installation of virtualbox-ose.

---

### Post by aaaantoine on 2011-04-27
Indeed. Just the right headers are needed, it turns out.

---

### Post by tekstr1der on 2011-04-27
> **aaaantoine said:**
> Indeed. Just the right headers are needed, it turns out.

Correct. I should have initially asked if the headers were installed. Glad you got it sorted.

---

