---
title: "nvidia PPA driver install and kernel questions"
date: 2010-08-01
forum: Multimedia Software
---

### Post by jsimerly on 2010-08-01
I have always used the Ubuntu repositories for Nvidia card drivers.  I'm running Lucid and just replaced a 9800 GT with a GTX 470.  It was a simple hardware swap and I stayed with the installed 195.36.15 driver, as the Nvidia website says that this legacy driver supports both 9800 GT and GTX 470.  While on the website, I read that the current 256-level drivers fix a host of issues on the newer cards.  However, that driver level is not available from the official Ubuntu repositories.

A quick Google search led me to this PPA, which I promptly placed in /etc/apt/sources.list.d:

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) lucid main

apt-get update and apt-get upgrade loaded the new nvidia packages and the latest 256-level drivers.  During installation, I noticed a message stating that the packages would be installed only on the running kernel (2.6.32-24).  This contrasts with nvidia package installation from the repositories, which uses DKMS to install the nvidia driver on all kernels.  I always try to keep at least N-1 (though it's usually N-2) kernels on my system in case there's ever a fatal flaw in the latest kernel version.

Needless to say, when I booted to the older kernel (2.6.32-23), I landed in Nvidia EE error land.  Running nvidia-xconfig did not fix it, so I rebooted to the latest kernel and all graphics functionality was restored.  From there, I turned off the PPA from Software Sources and used Synaptic to force version back to the nvidia packages from the official repositories.

I really want the functionality and tessalation capabilities of the newer drivers, so I am posting this to ask if a PPA can be configured to use DKMS so that future kernel upgrades will incorporate the drivers from that PPA.  I really don't want to re-install the nvidia packages every time I get a new kernel from the repositories.

---

### Post by NRDNick on 2010-10-29
Bump, I'd love to know if this is possible as well.

---

