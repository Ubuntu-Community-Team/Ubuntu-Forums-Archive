---
title: "Mostly perfect 12.04 system running - should I upgrade to 14.04?"
date: 2014-07-25
forum: Mythbuntu
---

### Post by MrBackhand on 2014-07-25
Like the title says, for the last year and 1/2 or so I've had a great running, "wife approved", MythTV system as our main living room device.  We can record 4 hdtv shows at once, and watch a recording, without a problem.  I tried to update to the new HWE recently and received the error that I have broken packages, which other people have also reported, and is now listed as a bug.  I decided to wait on that to get fixed, did a recent update, now the sound in my Steam games quit working.  Should I bite the bullet and upgrade my Mythbuntu system to 14.04?  Specs are below.

AMD Phenom II X4 965 Processor @ 3.40 GHz
16 gigs ram
nVidia geForce GTX 660 Ti
2 Hauppuage 2250 PCI-E Capture cards
SIIG Vista MCE Remote
Bluetooth Keyboard and Mouse
ALSA is my sound, thinking of switching to Pulse.

Linux MythTV 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
MythTV Version : v0.27.3-109-g0dd5ab3
MythTV Branch : fixes/0.27
Network Protocol : 77
Library API : 0.27.20140718-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libfftw3 using_libxml2 using_lirc using_mheg using_opengl using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_sdl using_taglib using_v4l2 using_x11 using_xrandr using_xv using_profiletype using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_mheg using_libass using_libxml2

Connected via HDMI to a Yamaha 7.1 Surround receiver which outputs to a TV.

Thanks for the advice in advance!

---

### Post by Bucky Ball on 2014-07-25
If you have room on the drive install 14.04 LTS to another partition and tweak in the wee small hours until you it qualifies for the stamp of approval. 

12.04 LTS is meant for what you're doing: production machines, servers, and reliability. It is supported until 2017 so there is no rush. 14.04 will be more stable when there is, but it's pretty stable now. In light of the fact 12.04 is well supported and certainly current, the fact that things are starting to break might signal some other problem which would be present in 14.04 anyhow. It shouldn't be breaking.

Perhaps try:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

... and report any errors.

---

### Post by MrBackhand on 2014-07-25
Thank you for your reply.  

I ran the two commands above and my system is updated now, however, when I login I receive the message below.

Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.13.0-32-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Your current Hardware Enablement Stack (HWE) is going out of support
on 08/07/14.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available.

For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)

To upgrade to a supported (or longer supported) configuration:

* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade

OR

* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

and reboot your system.

If I try to install a newer HWE per the commands above I get the error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-generic-lts-trusty is already the newest version.
linux-image-generic-lts-trusty is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx-lts-trusty : Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but it is not going to be installed
                              Recommends: libgl1-mesa-dri-lts-trusty (>= 7.2) but it is not going to be installed
 xserver-xorg-lts-trusty : Recommends: libgl1-mesa-dri-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-input-all-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-video-all-lts-trusty but it is not going to be installed
                           Recommends: x11-xserver-utils-lts-trusty but it is not going to be installed
                           Conflicts: libglapi-mesa:i386 (>= 0~)
E: Unable to correct problems, you have held broken packages.

---

### Post by Bucky Ball on 2014-07-25
Very odd and something I know nothing about. Have you manually installed hardware stack or been tweaking in that direction? Is it just a regular 12.04 LTS Desktop install or have you tinkered bit/lot? 12.04, the release, is supported for another two and a half years yet, so unsure why you are being advised to upgrade to 14.04. Maybe a wiser head will throw up the reason. :-k

---

### Post by uteck on 2014-07-25
Have you checked out any of the fixes on this page for the HWE problem?
[http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support](http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support)

The first time I did a major update of my Myth backend I used Clonezilla to make a recovery image, which was very fortunate since something odd did happen and the file system got corrupted on the / partition after the upgrade.

---

### Post by MrBackhand on 2014-07-25
It is a Mythbuntu 12.04 DVD install from a while back with regular updates.  Yes, I have researched the error and found it as a confirmed bug @ [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264).  I have not tried the final "working" suggestion because I do not want to put it into a worst state for upgrades.  I think going with the devil I know is better than going with the one I don't, so I will stick with 12.04.  :)

---

### Post by mattlach on 2014-07-27
Since MythTV can be rather picky with compatibility and upgrades, what I always do is image my working install before instaling any update or upgrading.

That way, if it breaks, it is easy to go back to the "wife approved" working install :p

---

### Post by agamotto on 2014-08-01
I would have to vote against upgrading to 14.04.x currently.  I just spent four days trying to get 14.04.1 working on a system that I have been running 12.04 on for about three years now.  I couldn't pin down the exact causes, but 14.04 was very unstable for me.  It would lose my USB keyboard/mouse, or it would lose my wireless card, various other glitches.  The two times I booted and was able to set up the tuners, it worked great.  Then it would glitch and I simply got tired of it.  I put 12.04.4 back on it, and other than a glitch with video playback (stuttering) on some channels, it is back to normal.

---

