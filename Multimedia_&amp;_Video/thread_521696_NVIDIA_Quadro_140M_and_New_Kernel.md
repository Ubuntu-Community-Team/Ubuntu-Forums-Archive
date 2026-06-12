---
title: "NVIDIA Quadro 140M and New Kernel"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by jb1789 on 2007-08-09
Hello, everyone.

In order to make my wireless card (Intel 4965) work on my Dell Latitude D830, I upgraded to the newest Gutsy kernel and used the Intel Linux Wireless Drivers.  After upgrading the kernel, I removed the new repositories since some of the new Gutsy packages are unstable.  Now, when I try to install the newest nvidia drivers to replace of the generic vesa driver and the nonfunctional nv driver, the installation always fails because I do not have the libc development packages.  When I run  sudo apt-get install build-essential, the output is

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

I am assuming that this problem is due to having the latest kernel, because when I upgraded, the sound also stopped functioning.  Does anyone know how to correct any of these problems?

Thanks in advance,
JB

---

### Post by tseliot on 2007-08-10
You shouldn't install kernels from unstable distributions.

You can [compile your own kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel") and build the kernel modules with module assistant.

OR you can use this guide **at your risk**:
[http://ubuntuforums.org/showthread.php?t=511974&highlight=master+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=master+kernel)

---

### Post by jb1789 on 2007-08-10
Thanks for the reply.

When I upgraded the kernel, I followed [http://ubuntuforums.org/showthread.php?t=493095&highlight=4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=4965), which seems similar to your second link.  This update was necessary to get the wireless card functioning properly because the Gutsy packages have most of the necessary modules.  Now, I cannot install the latest nvidia drivers, manually or using envy.  The errors which kill the installation all have to do with not having the latest libc-dev packages.  Since the kernel that I use and need is 2.6.22-9, I do not think that I can use the instructions in your first link.  Is there any way that I could install the driver in this kernel, or is it impossible?

Thanks again,

JB

---

### Post by tseliot on 2007-08-10
> **jb1789 said:**
> Is there any way that I could install the driver in this kernel, or is it impossible?
sorry but I don't think you can compile the Nvidia kernel module without the compilers.

---

### Post by jb1789 on 2007-08-10
I just tried the sudo apt-get install build-essential command in an older kernel (2.6.20-15) and I received the same error as above with regards to libc.  Do you know why I cannot install this package in any kernel?

---

### Post by tseliot on 2007-08-10
> **jb1789 said:**
> I just tried the sudo apt-get install build-essential command in an older kernel (2.6.20-15) and I received the same error as above with regards to libc.  Do you know why I cannot install this package in any kernel?

That's because you upgraded some other packages (some dependencies) when you installed the new kernel.

In other words, unless you know what packages you have to downgrade, you have a half broken system. But of course a full upgrade to Gutsy would solve this problem of yours.

---

### Post by jb1789 on 2007-08-10
Thank you for all of your help.  I guess I'll just wait for Gutsy to get my NVidia graphics card working because the vesa driver is usable, and in my opinion, having is working wireless card is more important than using the nvidia driver.

---

