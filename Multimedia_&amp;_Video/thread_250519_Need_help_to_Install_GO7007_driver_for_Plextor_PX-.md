---
title: "Need help to Install GO7007 driver for Plextor PX-TV402U"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by hollowGod on 2006-09-04
Hi!

Can someone please tell me how to do this?
I have searched the internet for a "How to" but with no luck.

What I have found out is that I am supposed to configure the kernel in some way.

Here is the link to the driver:
[http://oss.wischip.com/]("http://oss.wischip.com/")

From the README:
> A fully built kernel source tree must be available.  Typically this will be
linked from "/lib/modules/<KERNEL VERSION>/build" for convenience.  If this
link does not exist, an extra parameter will need to be passed to the
`make` command.

All vendor-built kernels should already be configured properly.  However,
for custom-built kernels, the following options need to be enabled in the
kernel as built-in or modules:

        CONFIG_HOTPLUG           - Support for hot-pluggable devices
        CONFIG_MODULES           - Enable loadable module support
        CONFIG_KMOD              - Automatic kernel module loading
        CONFIG_FW_LOADER         - Hotplug firmware loading support
        CONFIG_I2C               - I2C support
        CONFIG_VIDEO_DEV         - Video For Linux
        CONFIG_SOUND             - Sound card support
        CONFIG_SND               - Advanced Linux Sound Architecture
        CONFIG_USB               - Support for Host-side USB
        CONFIG_USB_DEVICEFS      - USB device filesystem
        CONFIG_USB_EHCI_HCD      - EHCI HCD (USB 2.0) support

Additionally, to use the example application, the following options need to
be enabled in the ALSA section:

        CONFIG_SND_MIXER_OSS     - OSS Mixer API
        CONFIG_SND_PCM_OSS       - OSS PCM (digital audio) API

The hotplug scripts, along with the fxload utility, must also be installed.
These scripts can be obtained from <http://linux-hotplug.sourceforge.net/>.
Hotplugging is used for loading firmware into the Cypruss EZ-USB chip using
fxload and for loading firmware into the driver using the firmware agent.

How do I config the Kernel source/headers?
How do I compile and install source/headers?

I know that in DAPPER I must use "sudo make install USE_DEV=y"
to build the driver since hotplug is replaced by udev in Dapper.

hollowGod

---

### Post by kogos on 2008-03-01
so, noone answered???

I know this is a considerably old post, but i found it while googling... 

I have Gutsy on and unfortunately i can't make Plextor pvr to work... and now even [http://oss.wischip.com/](http://oss.wischip.com/) isn't working (no page found). I even tried to search for GO7007 driver from another site, but still no luck...

Anyway, i'll find the driver somewhere, but what i really need is some giude on how to install the driver...

P.S.: i've been using ubuntu for 6 months now, so i am not an expert or anything... be "gentle" please...

---

### Post by kogos on 2008-03-05
... after 6 months of trying to install the go7007 drivers and MythTV on Ubuntu Gutsy, i now know there is NO way i will ever do this... I wonder why this is SOOOO hard to do... Driver is compiled fine, MythTV installs fine, and then the Plextor PVR is just not recognized... Why this had to be so difficult... I got so ungry about this that i formatted my hard disk and installed a fresh copy of Ubuntu gutsy, since i've done so many tests that messed up my system :(

Is this so difficult with other USB PVR devices? or is it only the plextor one?

P.S.: i am reading all around that the Plextor pvr is an excellent choise for linux users... I say it's the worst. I don't wanna have excellent video compression quality if i can't even use it :(

---

### Post by Evo Pete MTL on 2008-03-12
I have exactly the same problem the page for the drivers does not exist. I will try contacting Plextor to get some info.

---

### Post by Evo Pete MTL on 2008-03-12
I found them and made things work! Check out this link:

[http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_usbfs_fix](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_usbfs_fix)

Enjoy!

---

