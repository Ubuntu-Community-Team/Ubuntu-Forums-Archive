---
title: "Nvidia Driver splts monitor into 4 screens (SOLVED)"
date: 2011-01-21
forum: Multimedia Software
---

### Post by evolving_monkey on 2011-01-21
Hello all,

I tried to install the nVidia driver in the repository and it caused my monitor to split into four screens. I searched in the forum and didn't find a workable solution. 

I finally found the solution at [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html) 

This method works flawlessly for me in both 32 bit and 64 bit environments and there is no need to reinstall the nVidia driver after a kernel upgrade. Since the driver is installed in through a repository that is taken care of. This is by far the easiest method I have found and actually solves a few dual monitor issues as well. You just need to copy and paste the given commands into a terminal window to rum them. Once the following steps are completed, you will be able to install the nVidia driver through System/Administration/Hardware Drivers like you would normally. Make sure to follow the directions for your particular release to avoid problems...so read carefully.

I have installed using this method on an MSI A5000 laptop. It has an nVidia GeForce 8200m G video card. I just put in a Seagate MomentusXT 500GB Solid State Hybrid Drive and decided to go with the 64 bit version. So far, it is running brilliantly and I can definitely see a performance boost. The nVida card is is working the best I've seen so far on this laptop with Ubuntu...very happy with this setup.

I am also copying the content in case the site is ever taken down. This way we can have it in our forum. I'm not the original author. I'm just hoping to save someone a few headaches. If this has already been posted, my apologies, but I didn't find it. 

Good luck...I hope this helps.

***_Please Note:_*** The nVidia driver version that is listed in the tutorial is no longer current. This is not a concern because the most current stable driver is what will be installed. At the time of this posting it is version 260.19

The following is from [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html):

Written by Andrew in graphics drivers, linux, nvidia, ubuntu
Thursday, June 24, 2010
24 Jun
2010

How To Install nVidia 256.35 Display Drivers In Ubuntu (From A PPA Repository)

		25	

nvidia 256.35 ubuntu

nVidia released the new 256.35 display drivers as stable, just 2 days after the release candidate.


nVidia 256.53 graphics drivers highlights:

    * Added unofficial GLX protocol support
    * Improved Thermal Settings reporting in nvidia-settings to accurately reflect hardware configurations with multiple thermal sensors.
    * Fixed an interaction problem between Compiz and 'screen-scraping' VNC servers like x11vnc and vino that caused the screen to stop updating.
    * Enhanced VDPAU to add basic support for Xinerama. VDPAU will now operate on a single physical X screen under Xinerama. See the README for more details.
    * Enhanced VDPAU's handling of corrupt clips of all formats on GPUs with VDPAU feature set C to be at least as good as on GPUs with VDPAU feature set B. This significantly improves various clips provided by nvnews.net user eamiller.
    * Fixed a bug in Xv attribute handling that caused hue, saturation,brightness, and contrast values to be misapplied when using an Xv overlay adaptor.
    * Implemented new APIs to allow sharing VDPAU surfaces with OpenGL andCUDA.
    * Removed precompiled kernel interfaces from the NVIDIA Linux-x86 .run file;


And many other improvements and bug fixes. The complete release notes can be found HERE.


Important note before trying to upgrade: these drivers will only work with GeForce 6 and above!

The easiest way to upgrade to the latest nVidia 256.35 display drivers in Ubuntu (Maverick, Lucid, Karmic, Jaunty, Intrepid or Hardy) is to use the following PPA (just copy/paste the commands in a terminal):


1. Add the PPA

***_-For Ubuntu Lucid and Maverick:_***

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates



_***-For Ubuntu Karmic, Jaunty, Intrepid and Hardy:***_

sudo sh -c "echo 'deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) UBUNTU_VERSION main' >> /etc/apt/sources.list"
sudo sh -c "echo 'deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) UBUNTU_VERSION main' >> /etc/apt/sources.list"



Replace the "UBUNTU_VERSION" in the commands above with your Ubuntu version (karmic, jaunty, intrepid or hardy).


2. Install the nVidia display drivers

***_-For Ubuntu Lucid and Maverick:_***

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings



Then go to System > Administration > Hardware Drivers and make sure "Nvidia current" is activated.

[B][I][U]
-For Ubuntu Karmic, Jaunty, Intrepid and Hardy:[/U][/I][/B]

sudo apt-get update && sudo apt-get install nvidia-glx-256 nvidia-256-modaliases nvidia-settings



Then go to System > Administration > Hardware Drivers and make sure Nvidia 256.35 graphics drivers are activated.


And finally, restart.


If for some reason the new drivers do not work properly, use PPA Purge to remove the PPA and revert all the changes.


To find our if your graphics card is supported, go HERE and click on the SUPPORTED PRODUCTS tab.

---

