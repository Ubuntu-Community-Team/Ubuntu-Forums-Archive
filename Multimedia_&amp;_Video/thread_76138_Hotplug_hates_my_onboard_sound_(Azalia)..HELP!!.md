---
title: "Hotplug hates my onboard sound (Azalia)..HELP!!"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by HeXeD on 2005-10-14
Please hang in there..I'm not the best when it comes to linux.  Not a ABSOLUTE newbie, but not a regular user of linux.  Trying to be though..

Information about computer:
I have 5.10 installed on my laptop.  It has a Intel NQ82915PM chipset with a Realtek ALC880 Audio / WOW ASP.  this is the Azalia driver people have been getting to work with the snd-hda-intel module.  Here is where it gets crappy...

Problem:
When I first installed ubuntu, and it ejected the disk for further installation, durring reboot, computer would get to the part "Starting hotplug subsystem" and freeze.  The keyboard is responding, and it displays my type, however it is not accepting anything, just moves down every line when I press enter.  Then I decided to ctrl+c on that part just to get ubuntu installed.  That worked correctly, however I had a bunch of other problems. 

I messed around with my bios setting (stupid pheonix bios with all of maybe 4 different options) and disabled the option for "Azalia" in the bios which actually represents  itself as "Azalia - Device 27, Function 0".  When I disable this in the bios, it no longer freezes waiting for hotplug to initialize.  It actually works great, with the exception that I am now at the point where I want to install sound and alsa has no way to locate my sound card because it is disabled in the bios.  This gets to my question..

Please correct me if I am wrong in any of my "assumptions."  If it is freezing on starting hotplug..and only when I have my Azalia enabled, would it be correct to assume that the sound initialization is what is hanging it up?  Is there a config which shows what hotplug would be starting up in order for me to find out what I need to put into the blacklist?  Or is there some log file that has all the information?  

I tried to boot into recovery mode, and it freezes there as well.  It shows me everything loading, and gets to the following and then freezes:

<3>hw_random: RNG not detected
      hw_random: can't be loaded
missing kernel or user mode driver hw_random

I am almost certain the RNG is not the issue (seeing that the random number generator should have nothing to do with my sound...but once again, then steps in my newbness and I start assuming things..  even when I disable my Azalia from the bios, and boot into recovery mode, I get "Initializing random number generator.... [ok].  What is going on here?

Can anyone help me try to troubleshoot exactly what hotplug is trying to load..and rid of it?  Is this possible?  Can I have something not load up with hotplug but still work?

Signed,

Confused

---

### Post by shenki on 2005-10-14
you are not alone. I've been struggling (unsucessfully) to get my intel HD audio sound working for the month or so that I've had this laptop. 

Here are some bugs relating to your issue:

[15465](http://bugzilla.ubuntu.com/show_bug.cgi?id=15465) Hotplug hangs on boot trying to load snd-hda-intel
[15031](http://bugzilla.ubuntu.com/show_bug.cgi?id=15031) ALC880 + Intel 915GM - ICH6 results in Kernel panic

The second bug has some promising links to patches for the kernel, and also a kernel .deb that has the patch itegrated. Didn't work for me, but give it a go.

---

### Post by Ryujin on 2005-10-14
I had a lot of trouble on my old laptop with the same thing on many distros, including Ubuntu, I fixed it by switching to oss instead of alsa, but I have never done it with Ubuntu, I have always done it by compiling my own kernel, but that dosen't do much good for your situation, unless one time it lets you boot (mine did sometimes)

---

### Post by shenki on 2005-10-15
oh, i can boot up fine - removed the offending modules so i can use the computer. I doubt that the intel card has oss support, or does it?

thanks for the suggestion

---

### Post by HeXeD on 2005-10-18
ok, here is what I have done to "somewhat" solve my problem.  Well, at least this time my computer boots with my sound enabled in bios, and it now shows up on lspci.

What I did was go into the blacklist in hotplug (/etc/hotplug/blacklist) and added the snd_hda_intel module to the blacklist to keep hotplug from attempting to load it.  The only problem now is no matter what I do, gnome does not think I have anything installed.  ALSA found my card with no problems.  

Now when I try to run modprobe snd_hda_intel, it tells me the following error which has been very hard to research in Google.

hexed@ubuntu-mobile:~$ sudo modprobe snd_hda_intel
Password:

sh: line 1:  8320 Segmentation fault      modprobe --ignore-install snd-hda-intel
FATAL: Error running install command for snd_hda_intel


I am wondering if it is doing this because of my blacklisting of the snd_hda_intel module.  This wouldn't make much sense because I assume the module is not available for the hotplug system, but does the sound drivers really need to run with hotplug if the device is not a "hotpluggable" device?  I guess my main problem besides by ineptitude in linux is my misunderstanding of the hotplug system.

Driving me nuts...Thanks for the help so far.

---

### Post by jeremytaylor on 2005-10-19
You can fix this by following the wiki instructions at 
[https://wiki.ubuntu.com/HdaIntelSoundHowto?highlight=%28hda%29%7C%28intel%29]("https://wiki.ubuntu.com/HdaIntelSoundHowto?highlight=%28hda%29%7C%28intel%29")
I followed the second set of instructions which make use of the repos. Once you've worked through that just remove the modules from the black list and all should work fine.
Jeremy

---

### Post by HeXeD on 2005-10-19
Thanks for the link!  however everything was going ok until I gotto one part:

When entering in:

root@ubuntu-mobile:/usr/src/linux-headers-2.6.12-9-686# make-kpkg --rootcmd=fakeroot --append-to-version=2.6.12-9-686 modules-image

I get the following error:

We do not seem to be in a top level linux kernel source directory
tree. However, there are kernel headers that may be suitable to build
external kernel modules. Since you do not have non-module targets, let
us continue.
Warning: The file include/linux/version.h exists
The contained UTS_VERSION string:
                        "2.6.12-9-686"
does not match expectations:
                        "..2.6.12-9-686"
I'll try and recover
touch: cannot touch `Makefile': No such file or directory
touch Makefile failed:256 at /usr/bin/make-kpkg line 974, <VERSION> line 3.
root@ubuntu-mobile:/usr/src/linux-headers-2.6.12-9-686#


Any ideas here?  I have tried 2.6.12-9-686 and -9-686 as well after the --append-to-version.  I just can't seem to get it to work and I have looked all over so far..

---

### Post by jeremytaylor on 2005-10-19
oh dear. sorry i've no idea. It worked for me and I just assumed it might help you too. Have you got other linux headers installed? Are you sure that is the kernel you are using?
jeremy

---

### Post by HeXeD on 2005-10-19
BTW..

I am jacking around with recompiling my kernel.  Since I have never worked with compiling my kernel for sound problems..I'm a bit confused.  Should I keep OSS AND ALSA in the kernel?  Should I disable it all?  I would assume if I disabled it all I wouldn't ever get it working..but would it be in my best interest to do that?

---

### Post by HeXeD on 2005-10-19
This is what I have:

root@ubuntu-mobile:/usr/src/linux# uname -a
Linux ubuntu-mobile 2.6.12-9-686 #1 Tue Oct 4 18:57:15 BST 2005 i686 GNU/Linux

I got the linux headers from apt-get.  My usr/src looks like this:

root@ubuntu-mobile:/usr/src# ls
alsa-driver.tar.bz2                               linux-patches
ATI                                               linux-source-2.6.12
kernel-image-2.6.12-custom_10.00.Custom_i386.deb  linux-source-2.6.12.tar.bz2
linux                                             modules
linux-headers-2.6.12-9-686

Any ideas?

---

