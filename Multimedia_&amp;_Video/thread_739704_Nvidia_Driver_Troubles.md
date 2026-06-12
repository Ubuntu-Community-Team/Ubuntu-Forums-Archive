---
title: "Nvidia Driver Troubles"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by hooflung64 on 2008-03-30
I just gave Vista Ultimate 64 the boot of my machine. Here are the specs:

Opteron 180 ( 2 x 2.4ghz )
eVGA mobo with Nforce 4 SLI chipset
eVGA 8800GS Superclocked
4g of OCZ DDR400
160g WD SATA II
Audigy 2 ZS
Ubuntu 7.1 x64

I installed the Nvidia driver just fine I suppose. When I restarted the gdm I got my fully accelerated compiz desktop and all was well with that. Then I moved on to install EVE-Online's Linux client and tried to rustle up the 32bit library dependancies since it wouldn't start on my x64 right off.

So I decide to reboot and when I come back into the OS the GDM wants me to run in safe mode like the driver isn't installed anymore. Can anyone help with this issue? Where should I go from here?

---

### Post by hooflung64 on 2008-03-30
Well I figured it out. I went ahead and did a fresh install again. Then I did these steps:

I removed anything Nvidia related already on the system through synaptic.

Then I went into a terminal  after exiting the window manager by CTRL+ALT+F2 and did:

```

sudo /etc/init.d/gdm stop

sudo apt-get install ia32-libs
sudo apt-get install build-essential
sudo apt-get install xserver-xorg-dev

sudo sh NVIDIA-Linux-x86_64-169-12-pkg1.run

sudo modprobe nvidia

sudo vim /etc/X11/xorg.conf

sudo /etc/init.d/gdm start

```

When the Nvidia Installer asked to make xorg.conf file I said no. I then manually replaced 'vesa' with 'nvidia' in the original.

I found if I didn't do the ia32-libs the OpenGL 32 compatibility sanity check would fail. I then went into the Nvidia X Server Settings page and exported the new xorg.conf file into my Documents as xorg.conf.new and coped the original to /etc/X11/xorg.conf.old and then copied my new one over as the main xorg.conf file.

Restarted and BAM. All is good after I rebooted. Hopefully some others might find this helpful. Basically what was happening is that there were conflicting files on the system AND the Nvidia Installer wasn't inserting the module into the kernel except for the current session.

---

