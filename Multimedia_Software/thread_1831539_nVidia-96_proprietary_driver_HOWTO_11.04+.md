---
title: "nVidia-96 proprietary driver HOWTO 11.04+"
date: 2011-08-23
forum: Multimedia Software
---

### Post by indrora on 2011-08-23
Those of us who use the old nvidia-96 series drivers know that under 11.04 there's a new load of pain because of the X folks. Here's how to make life (a little) less painful than with Nouveau[1]

Here's what we're aiming for:
[IMG]http://i.imgur.com/4lGVA.png[/IMG]

First, we're going to have to get the nVidia driver From Their Website. 

The fastest is via FTP. The latest version (as of TODAY) is 96.43.20, and it lives at

[ftp://download.nvidia.com/XFree86/Linux-x86/96.43.20/](ftp://download.nvidia.com/XFree86/Linux-x86/96.43.20/)

We're going for the first file in there.

Second, we're going to have to disable any traces of Nouveau. The nVidia installer *will* do this for you if you haven't already, but its generally best to do it yourself (it saves a restart of the kernel)

add the following line to /etc/modprobe.d/blacklist.conf[2]
```
blacklist nouveau
```

Third, we're going to reboot. Once GDM/KDM comes up, press ctl-alt-F1 to get to a shell window. We're going to stop gdm/kdm/etc. Log in and run the following:
```
sudo stop gdm
```

Replace gdm with kdm if using kubuntu.

Fourth, we're going to run the nvidia installer. cd to the directory you've downloaded it (probably Downloads) and run the following:

```
chmod a+x NVIDIA-Linux-x86-96.43.20-pkg0.run
sudo ./NVIDIA-Linux-x86-96.43.20-pkg0.run
```

The installer will ask you to abide by the nVidia license (if you dont agree with using their license, well, you're not the target of this HOWTO are you?).

The installer will also say it was unable to run a distributor-specific script and ask if you want to continue. Saying no will push you back to a command line. Saying yes will install and configure the driver.

Give the installer approx. 5 minutes. Go get a drink and check your voicemail.:popcorn:

SIDENOTE: What's the installer doing? The installer here is actually compiling a version of the module that glues the proprietary driver (the Binary Blob that so many GNU folks are afraid of) with the kernel. It's also making sure there's nothing kicking around that it doesn't like.

The installer will be pretty much automated through the entire thing save for one more question: Should it run nvidia-xconfig? Tell it yes unless you're REALLY familiar with your X11 configuration. Otherwise, just say yes.

Once its done, you can either run "sudo start gdm/kdm" or just restart. Either way, X will be happy and come up.

Now, to fix your resolution. Chances are, the resolution nvidia-xconfig chose is REALLY conservative (in my case, 1080x1024 vs. 1920x1200) You will need to run the following from a terminal window:
```
sudo nvidia-settings
```

If this doesn't come up then you've done something wrong. Really wrong. If it complains it can't find a file like /home/jerkwad/.nvidia-settings-rc, ignore it.

The tab we're looking for is this:

[IMG]http://i.imgur.com/UpZbC.png[/IMG]

This is where you can configure magic like Xinerama (many-screens-one-desktop) or Multiple X Screens. We're concerned about resolution, not magic. Change the resolution to either 'auto' or what the native resolution of your display is.

You can test any of the resolutions your nVidia card says your screen supports by hitting "Apply". Once you're happy, continue on to the next step...

Press the button 'Save To X Configuration File' and let it save to /etc/X11/xorg.conf. Log out and log back in (or restart, if you really want) and enjoy.



TROUBLESHOOTING...

[SIZE="3"]I updated and did what I was told and now my graphics wont come up![/SIZE]

Unfortunately, there's a little problem with this path: Kernel updates throw away your install. To fix this, you have to actually /uninstall/ the nVidia driver and then /reinstall/. Its a pain, but until Cannonical starts updating their nVidia drivers, we're hoz0rd. 

[SIZE="3"]The installer crashed! My computer tells me about inodes going away! OH NOES![/SIZE]

I had this happen with the most recent kernel update. Its nothing *too* scary unless you are one of those people who unplug their computers instead of telling to to shutdown. Otherwise, reboot, tell it to fix things and just cross your fingers. If something REALLY bad happens, well... I dont know what to do. I haven't experienced it. 

[1] For me, Noveau is hideously slow, trashes my X root window and can't live without a composite manager like xcompmgr. i'm now happily 

[2] the nVidia installer will create this as a file, adding an option line to explicitly disable KMS. Without Noveau running however, KMS won't bother unless something ELSE wants to use it.


[SIZE="4"]There's no way you're running Natty! You've just gotten the GTK style and some other things to make it look right![/SIZE]

[[IMG]http://i.imgur.com/UVh6Ol.png[/IMG]](http://imgur.com/UVh6O)

---

