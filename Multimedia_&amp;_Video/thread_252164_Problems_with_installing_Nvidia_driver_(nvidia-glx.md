---
title: "Problems with installing Nvidia driver (nvidia-glx)"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by Malta Soron on 2006-09-06
Hi there!

I've got some problems with installing the Nvidia driver. I want to do this:

```
sudo apt-get install nvidia-glx nvidia-settings nvidia-xconfig
sudo nvidia-glx-config enable
```

But apt can't find nvidia-xconfig and wen I enter the second line I receive this output:

```
jos@jos:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
```

I tried the suggested command, but it couldn't find 'tee /var/lib/xfree86/xorg.conf.md5sum'.

I tried using the nv and nvidia drivers by editing /etc/X11/xorg.conf, but then X crashes.

I also tried installing nvidia-glx-legacy, but that didn't work either.

Do you have an idea how I could get nvidia-glx working?

---

### Post by skymt on 2006-09-06
How does X crash? Does it give an error?

---

### Post by flipkick on 2006-11-05
Here's my souces.list:

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


## PLF
## Please report any bug on [https://launchpad.net/products/plf/+bugs](https://launchpad.net/products/plf/+bugs)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm



when I try to install the "nvidia-glx" package apt tells me this:
-------
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

The following packages have unmet dependencies.
  nvidia-glx: Depends: nvidia-kernel-1.0.9625
E: Broken packages
-------

Any hints ?

I "somehow" messed things up (again)...

---

### Post by MasterOfDisaster on 2006-11-05
In response to Malta Soron, what video card are you using?

Also, installing nvidia-settings and nvidia-xconfig require me to remove my nvidia-glx.  I'm not sure if this is just me, or if it might be screwing you up.nvidia-glx-config enable

If your card is listed as a card supported by nvidia-glx then:
Finally, the error message from nvidia-glx-configure means that you have to manually edit the etc/X11/xorg.conf file.  Find the Device section, and under that heading there should be a line that says 'Driver    "nv"'.  Replace that nv with nvidia, but only if you are sure the nvidia-glx is installed (or else X will not start).  Then restart the X server and you should be free sailing.

Anyways, have fun.

To flipkick, dependency errors are caused (usually) by conflicting repositories.  Try disabling all 3rd party repos, reloading/refreshing, and trying again.

---

### Post by flipkick on 2006-11-06
> **MasterOfDisaster said:**
> 
To flipkick, dependency errors are caused (usually) by conflicting repositories.  Try disabling all 3rd party repos, reloading/refreshing, and trying again.

Thanks Mr Sisaster.

I disabled all third party repositories and it succeeded

---

### Post by adam.skinner on 2006-11-06
The culprit here is Amaranth.  I was like "Oh yeah?  Remove nvidia-glx?  Sure thing, *I trust you*".

Stupid noob mistake number 25372.

Commenting out the Amaranth repository should fix the problem.  O ryou can just be patient and wait for them to fix it.  Or you could manually install your nvidia driver.  There are other repos out there too.

Personally, I don't need the latest driver because I couldn't get the Beryl working with the nVidia beta driver anyway (so I'm riding the Xgl pony into 3D wonderland).

---

### Post by MasterOfDisaster on 2006-11-08
Just realized that nvidia-settings is included in nvidia-glx... So it's not needed unless you use the nvidia-glx-legacy.

---

### Post by tseliot on 2006-11-08
> **adam.skinner said:**
> The culprit here is Amaranth.  I was like "Oh yeah?  Remove nvidia-glx?  Sure thing, *I trust you*".

Stupid noob mistake number 25372.

Commenting out the Amaranth repository should fix the problem.  O ryou can just be patient and wait for them to fix it.  Or you could manually install your nvidia driver.  There are other repos out there too.

Personally, I don't need the latest driver because I couldn't get the Beryl working with the nVidia beta driver anyway (so I'm riding the Xgl pony into 3D wonderland).

You can use my Stable repositories:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

