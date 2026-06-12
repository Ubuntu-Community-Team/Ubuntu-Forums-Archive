---
title: "Intel 845 / Nvidia / 10.04 installation nightmare"
date: 2010-08-14
forum: Multimedia Software
---

### Post by bluetomgold on 2010-08-14
I've been trying to install drivers for a PNY NVIDIA Geforce 6200 AGP card all day and am now pulling my hair out and in low graphics mode. The card worked out of the box, but video performance was poor - full screen Flash video playback, for example, was not going to happen. The machine is a P4 2.8gig with 2gb ram, higher spec than my laptop which plays streamed video at full screen perfectly.

Note that the machine also has an onboard intel 845 graphics chip which is disabled, but even so (I believe) causing issues with compiz. Possibly this is the root of my problems? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580768](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580768)

OK so tried so far:

The card did not show up in hardware drivers so:

```
sudo apt-get --purge remove xserver-xorg-video-nouveau 
sudo apt-get install nvidia-current
```Then found nvidia-current in hardware drivers, so activated and restarted.

Following reboot, in hardware drivers: "Activated but not currently in use"

Followed the instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

```
sudo update-alternatives --config gl_conf
```(selected option 2 nvidea current, manual)
```
sudo ldconfig
sudo nvidia-xconfig
```"WARNING: Unable to locate/open X configuration file.
New X configuration file written to '/etc/X11/xorg.conf'"
```
 sudo reboot
```checked again in hardware drivers: "Activated but not currently in use"

Having not got anywhere with the nvidia-current drivers I decided to attempt to install the latest "NVIDIA-Linux-x86-256.44.run" file from the nvidia homepage instead. Following instructions I basically removed the nvidia-current drivers from hardware drivers, downloaded the .run file and then...

```
sudo apt-get --purge remove nvidia-*
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-256.44.run
```When the software loads, it says "You appear to be running an x server..." and won't continue. I've also tried:

```
sudo service gdm stop
sudo gdm stop
```But I can't get any further.

I may well be barking up the wrong tree. Either way I'd really appreciate some help!

---

### Post by bluetomgold on 2010-08-14
I've just made some progress. Followed this information [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html) but using the -x86-256.44 driver and installed before booting gnome. 

This has worked in so far as I now have the proper resolution and I can (finally) turn on visual effects. The driver is not displayed in Hardware Drivers, though, and Flash performance is still rubbish.

Hmmm. Advice appreciated.

---

### Post by bluetomgold on 2010-08-14
Following a reboot, "Desktop effects could not be enabled".

Not so good.

---

