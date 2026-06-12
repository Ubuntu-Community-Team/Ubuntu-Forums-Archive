---
title: "Catalyst 13.4 and drivers install on 13.04 32bit, radeon 6600M,"
date: 2013-04-29
forum: Multimedia Software
---

### Post by dougleduck on 2013-04-29
I've attempted to install the Amd Catalyst 13.4 and the associated drivers, using instructions here [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/286775#286775]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/286775#286775").

Upon restart I'm unable to get to the login screen instead greeted by the all too familiar prompt asking me to either, -Run in low graphics mode, -Reconfigure Graphics etc which only ever dropped me to a terminal.

After some faff starting low graphics mode I managed to log in, only to find unity not to start or any windows decorations. I managed to remove the proprietary drivers and re-install the software centre drivers. 

13.04 runs but the open drivers have problem ([https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1173967?comments=all]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1173967?comments=all")), which eventually causes a shutdown from overheating. 

Note that even if this overheating issue was solved, the proprietary drivers are the only ones that offer graphics switching and any decent performance at the minute. 


lspci output below
```
$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6600M/6700M/7600M Series]

```

---

### Post by dougleduck on 2013-05-03
Mega Bump!

I attempted to replicate the problem and add some more info. I used a rather scattergun approach to grabbing log files attached from various points in the install.

If anyone finds some info stating it doesn't work with a rarings current kernel, etc, please share :). Apologies for the rather rough live-blogging style.

I start by ensuring my system was returned to its original state following purge instructions here
[INDENT][http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)[/INDENT]
and then restarting.

Installed updates, linux-image-3.8.0-19 and restarted.

Checked requirements listed here
[http://wiki.cchtml.com/index.php/Catalyst_13.4](http://wiki.cchtml.com/index.php/Catalyst_13.4)
[http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Before_you_start)

was missing XFree86-Mesa-libGL and freetype and not in software centre. 
 
I've attached Xorg.0.log.beforeDeb, on offchance its useful.

At this point, as I seen before, the core temperature was rising (>90C) quickly. Unsure, but either onboard or the AMD GPU running at full whack?

Created and installed .deb from the Catalyst 13.4 from the AMD site

```
sudo ./amd-catalyst-13.4-linux-x86.x86_64.run --buildpkg Ubuntu/raring
sudo dpkg -i fglrx*.deb

```
and restarted...

Logged in, No windows decorations. ctrl-alt-t brings up terminal so I can start firefox. I installed 
```
sudo apt-get install compizconfig-settings-manager
```
as per [http://askubuntu.com/questions/285779/after-upgrading-to-13-04-unity-interface-is-not-showing/285822#285822](http://askubuntu.com/questions/285779/after-upgrading-to-13-04-unity-interface-is-not-showing/285822#285822) to try to resolve.

Computer crashed,restarted with with alt-prnt-screen reisub.

Attaching Xorg.0.log, kern.log, dmesg.log and sys.log, in PostDebInstall.tar.gz

Trying
```
dconf reset -f /org/compiz/
```

for info did.
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6600M/6700M/7600M Series]
```

Tried to find fglrx, didn't exist. Trying installed .deb's indivdually.
```
$sudo dpkg -i fglrx_*.deb
[sudo] password for jody:
(Reading database ... 173766 files and directories currently installed.)
Preparing to replace fglrx 2:12.104-0ubuntu1 (using fglrx_12.104-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
rmdir: failed to remove ‘’: No such file or directory
Done.
Unpacking replacement fglrx ...
Setting up fglrx (2:12.104-0ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-initramfs: deferring update (trigger activated)
Loading new fglrx-12.104 DKMS files...
Building only for 3.8.0-19-generic
Building for architecture i686
Building initial module for 3.8.0-19-generic
Done.

fglrx:
Running module version sanity check.

Good news! Module version  for fglrx.ko
exactly matches what is already found in kernel 3.8.0-19-generic.
DKMS will not replace this module.
You may override by specifying --force.

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

Tried to start amdccle, got the following message
[INDENT]There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.

Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.[/INDENT]

Some commands from wiki above that I tried no immediate effect.
```
sudo amdconfig --tls=0
sudo amdconfig --acpi-services=off
```

I think the computer crashed, and when it rebooted I got a prompt about booting into basic graphics mode. I could only get a terminal, from here I replaced Xorg.conf with a backup and placed some log files on the desktop, attached in reinstallinggraphicsloh.zip.

I can now get back to a desktop without unity or windows decorations.

---

### Post by dougleduck on 2013-05-05
Bump.

Raring is so smooth, I'd love to actually run it.

---

### Post by Mark Phelps on 2013-05-06
You have AMD/Intel hybrid graphics -- for which there is no simple solution and drivers downloaded from AMD generally will not work.

You need to read through the linked thread to see if any of the solutions there work for you:

[http://ubuntuforums.org/showthread.php?t=1930450]("http://ubuntuforums.org/showthread.php?t=1930450")

---

### Post by dougleduck on 2013-05-06
OMG! So that forum yielded some surprising results.

So I tried two things, sudo apt-get install libgl1-mesa-glx --reinstall which I suspect did nothing really.

But also 
sudo amdconfig --px-igpu

which allowed me to start amdccle.

Trying to start unity I got errors about compiz and windows decorations so I then reset compiz again, as I'd also played with the settings before with :

dconf reset -f /org/compiz/


After logging out and back in, unity appears!

Temperature seem reasonable, fan working normally. Unity seems nippy.

Cheers. Yet to verify the drivers are doing anything yet (posting before I break something).

---

### Post by dougleduck on 2013-05-06
So turned the amd drivers on exclusively using the control centre, but back to low graphics mode.

Putting back onto intel GPU for a root around.

---

### Post by dougleduck on 2013-05-06
So if I try to start the discrete (AMD) GPU

sudo amdconfig --px-dgpu

it (unity/X?) dies and I get kicked into the 'start in low graphics mode' options. 

Putting integrated back on and resetting compiz gets me back to unity.

---

### Post by dougleduck on 2013-05-07
After following another link trail, it looks as if the latest amd drivers are not compatible with the intel drivers that come with raring, xserver-xorg-video-intel 2.2.21. The last known to work seem to be 2.20.9.

It seems changes in this driver means the amd gpu cant communicate with it properly?

You can download this in a deb from [http://packages.ubuntu.com/quantal/i386/xserver-xorg-video-intel/download](http://packages.ubuntu.com/quantal/i386/xserver-xorg-video-intel/download)

I tried this, as rarings not my production machine, but it failed because of a dependency lidudev0 was not installed (or perhaps the required version).

More experimenting later.

---

### Post by patslap on 2013-05-28
I too have a Lenovo E520 laptop with a similar AMD Radeon HD 6630m/Intel Sandybridge Core i5 hybrid graphics setup. 

I have tried getting the Radeon card to work for some time, too, but without success, even after following the guidance on [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) . Each time I revert back to the integrated onboard Intel graphics, which perform fine (runs Half Life 2 on steam at 50fps on medium to high settings). 

It would be useful to use the Radeon, so I'm still looking for a working solution.

---

