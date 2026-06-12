---
title: "intel i830/i845/i855GM graphics"
date: 2010-12-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by davidmohammed on 2010-12-27
All,
  Does anyone know if support for the intel i830/i845/i855GM graphics in natty has been/or will be improved over the VESA support introduced in maverick?

... or are these laptops stuck with 9.10 / 10.04 + various workarounds?

---

### Post by davidmohammed on 2011-01-03
... (bump) anybody testing with these pre 2008 laptops?

---

### Post by bapoumba on 2011-01-03
Title changed as requested (it's a Staff only option). Cheers!

---

### Post by jerrylamos on 2011-01-03
> **davidmohammed said:**
> ... (bump) anybody testing with these pre 2008 laptops?

Yeah, I've got Natty on IBM Thinkpad R31 which is i830 and also IBM ThinkCentre A30 which is i845G.

Both are on "classic" mode.  Suits me, a lot more function with less keystrokes and less windows than "Unity".

The i845G requires activating the gnome-panel on every boot.  i830 boots "classic" O.K.

Unity will run on this ati radeon xpress 200 but I use classic instead.  I'll try Unity from time to time.

The real pain is IBM Thinkpad T40 with ati radeon mobility 7500.  It's a pain plus acrobatics to get a partially disfunctional "classic" running, absolutely forget about Unity at this stage of development.

Jerry

p.s. That's at kernel -11.  No clue for the next major update...

---

### Post by Starks on 2011-01-04
A couple of 3D solutions were discussed during the Maverick dev cycle, but all were shot down due to time constraints and the undue amount of effort they'd require to safely implement.

As someone who frequents the Ubuntu-X mailing list and IRC channel, I don't see the scenario changing for Natty.

---

### Post by JRV on 2011-01-04
Thanks for the info.  I have an old Dell laptop with an i845 I am trying to resurrect.  10.04 doesn't work, and I had been putting off investigating the problem.

---

### Post by jerrylamos on 2011-01-04
> **JRV said:**
> Thanks for the info.  I have an old Dell laptop with an i845 I am trying to resurrect.  10.04 doesn't work, and I had been putting off investigating the problem.

My i845G has run every Ubuntu since Dapper Drake, does run 10.04 Lucid, 10.10 Maverick, and with effort 11.04 Natty.  See the thread: No Gnome panel

Sometimes I have to put i915.modeset=0 in the linux boot line to kill kms depending on the kernel updates.  
Sometimes I have to:
sudo gedit /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
Save
Quit

Sometimes needed, sometimes not depending on the state of the kernel.

Oops, had to re-boot, Natty "classic" screen froze. (this is ati radeon xpress 200) nicely the post was still there.

Jerry

---

### Post by Catharsis on 2011-01-05
Upstream actually published a novel patch a couple days ago which is looking good in preliminary testing. I believe someone is working on packaging it in a PPA for testing in Ubuntu, so stay tuned for some calls-for-testing which will probably pop up on the ubuntu-x mailing list or on this forum sometime.

---

### Post by davidmohammed on 2011-01-05
> **Catharsis said:**
> Upstream actually published a novel patch a couple days ago which is looking good in preliminary testing. I believe someone is working on packaging it in a PPA for testing in Ubuntu, so stay tuned for some calls-for-testing which will probably pop up on the ubuntu-x mailing list or on this forum sometime.

Excellent news - look forward to testing this in natty.

---

### Post by Catharsis on 2011-01-07
Patched kernels are ready, courtesy of Brian Rogers. Source: Bug [lpbug]541511[/lpbug], comment 427.

[QUOTE=Brian Rogers]I've made a kernel with the latest fix available in this PPA:
[https://launchpad.net/~brian-rogers/+archive/graphics-fixes-testing](https://launchpad.net/~brian-rogers/+archive/graphics-fixes-testing)

If it gets good feedback, I'll copy it to my regular graphics-fixes PPA.

This kernel is based on Natty's 2.6.37 kernel, has the changes in drm-intel-next applied, and the patch at [https://bugs.freedesktop.org/show_bug.cgi?id=27187#c291](https://bugs.freedesktop.org/show_bug.cgi?id=27187#c291) is added. I've produced builds for Lucid, Maverick, and Natty. It has a cache coherency checker, so you'll see periodic messages in dmesg reporting on the number of flushes and whether any problems are detected.

From Daniel Vetter's patch description:
> Poke HIC bit + wbinv + cache coherency checker
>
> Chris Wilson's latest patch with my cache coherency checker added. Spills the
> number of chipset flushes regurlarly into the dmesg and bails loudly if one
> fails.
>
> Tested-by lines (like for the previous patch attempts by me) highly welcome.

Feedback about the patch can be sent directly to the upstream bug report at
[https://bugs.freedesktop.org/show_bug.cgi?id=27187](https://bugs.freedesktop.org/show_bug.cgi?id=27187)

If you have issues relating to installing/booting this kernel, report them here.[/QUOTE]

Installation instructions:
```
sudo add-apt-repository ppa:brian-rogers/graphics-fixes-testing
sudo apt-get update
sudo apt-get install linux-headers-2.6.37-graphics2+12 linux-headers-2.6.37-graphics2+12-generic linux-image-2.6.37-graphics2+12-generic
```
Maverick & Natty users should also make sure to enable the -intel driver instead of the default fbdev driver:
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

### Post by jerrylamos on 2011-01-08
Thanks for the ppa.  I did get this error message:

...............
Setting up linux-headers-2.6.37-graphics2+12 (2.6.37-graphics2+12.26) ...
Setting up linux-headers-2.6.37-graphics2+12-generic (2.6.37-graphics2+12.26) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.37-graphics2+12-generic /boot/vmlinuz-2.6.37-graphics2+12-generic
/etc/kernel/header_postinst.d/nvidia-common: line 8: [: too many arguments
jerry@linux:~$ 


Jerry

---

### Post by jerrylamos on 2011-01-08
After ppa install error reported in previous post booted in recovery mode and did fix broken packages.  Seemed to go O.K. then rebooted.

Natty with ppa on i845G would not boot with xorg.conf specifying intel.  Totally black screen.  Nothing does anything. Power off/on.

ppa did boot with no xorg.conf.

How do I tell if the ppa is doing what was intended?  It's running here, in classic mode.  

Jerry

---

### Post by Catharsis on 2011-01-08
> **jerrylamos said:**
> After ppa install error reported in previous post booted in recovery mode and did fix broken packages.  Seemed to go O.K. then rebooted.

Natty with ppa on i845G would not boot with xorg.conf specifying intel.  Totally black screen.  Nothing does anything. Power off/on.

ppa did boot with no xorg.conf.

How do I tell if the ppa is doing what was intended?  It's running here, in classic mode.  

Jerry

You could check the log files from the previous boot, i.e. kern.log and Xorg.0.log.old, after you reboot using the fbdev driver instead of -intel.

---

### Post by fonix232 on 2011-01-09
Any news about 855GM support?

---

### Post by jerrylamos on 2011-01-11
> **Catharsis said:**
> You could check the log files from the previous boot, i.e. kern.log and Xorg.0.log.old, after you reboot using the fbdev driver instead of -intel.
Booted a different partition and looked at the Natty logs.
kern.log and Xorg.0.log and Xorg.0.log.old do not show a problem.

.xession-errors however includes:

```
...(polkit-gnome-authentication-agent-1:1076): GLib-GObject-WARNING **: cannot regi
ster existing type `_PolkitError'
(polkit-gnome-authentication-agent-1:1076): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
...
```

I could boot with no xorg.conf and do an ubuntu-bug xorg, since ubuntu-bug requires a running X in order to report - and the problem is there isn't any running X at the point of failure.

Maybe I'll do that and attach the .xsession-errors.

Jerry

---

### Post by Catharsis on 2011-01-11
Jerry,

What does your xorg.conf look like?

You could also try ppa-purge'ing the kernel and reinstalling it.

I'd also give a yell to Brian Rogers in the comments section of Bug [lpbug]541511[/lpbug], since he said "If you have issues relating to installing/booting this kernel, report them here."

---

### Post by jerrylamos on 2011-01-12
> **Catharsis said:**
> Jerry,

What does your xorg.conf look like?

You could also try ppa-purge'ing the kernel and reinstalling it.

I'd also give a yell to Brian Rogers in the comments section of Bug [lpbug]541511[/lpbug], since he said "If you have issues relating to installing/booting this kernel, report them here."

Catharsis, the kernel runs fine with no xorg.conf.  With typical xorg.conf specifying "intel" and verifying that "intel" was selected in Xorg.0.log, a failure is reported in .xsession-errors.  No failures in kern.log or in Xorg.0.log or Xorg.0.log.old.

The kernel is still up, I can do Ctrl-Alt-F1 to do sudo session gdm stop and sudo session gdm start.  Seems to me the kernel is running.

Now with my two test pc's with integrated intel video graphics I've had all kinds of X failures over the years since Intrepid Alpha when major changes were made in Compiz which did code that wouldn't work on those drivers.  Intrepid got running by blacklisting Compiz from the intel video graphics pc's.  

Over the years the failures using intel video graphics get fixed then boom they go bad again when there's a change in Compiz or in whatever else code is driving the desktop.  Usually driver "vesa" will work, Natty default fbdevhw is being used and functions fine, Natty Alpha 1 doesn't try Unity with it likely developers considered too slow or won't do some "eye candy".

So I've got a launchpad bug entered against xorg.  Now maybe the kernel is asking the desktop manager to do something that doesn't work with the intel driver but does work with fbdevhw, so I could re-try the failure and post to Brian Rogers.

Jerry

---

### Post by James Keating on 2011-01-13
This kernel works the best for me so far. Thank you. The only glitch I observe on my machine is that upon resuming after suspending, the screen lighting is dimmed by one level. This is a very minor annoyance, easily fixed each time with the Fn-brighten key combination.

Most kernels choke when I try to run any kind of video or Gnome programs and their kin (Firefox, gjiten, Geeqie). Until now, I was relying on kernel 2.6.34-020634rc7, but that was iffy too. 

My computer is an NEC VersaPro VY15F laptop with  an Intel 82852/82855 graphics chip.

I have kept changes to two lines in xorg.conf, Section "Device":
Identifier "Configured Video Device"
Driver "intel"
Option "DRI" "off"
EndSection

I have also kept the modeset=1 parameter in /etc/defaults/grub: 
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"

In a decade of using Linux, this is the most serious problem I have ever encounted. Not only couldn't I boot after upgrading the last two times, but the solution was almost completely different the second time. This kernel works, and I hope the patch gets into Natty so I don't spend another day or two struggling with the next upgrade.

---

### Post by migrate from windows on 2011-01-21
I installed brian rogers as told still display is in stripes and scrambles ..am i missing anything ? Im a linux newbie :-(

---

### Post by Tommaso on 2011-01-21
> **migrate from windows said:**
> I installed brian rogers as told still display is in stripes and scrambles ..am i missing anything ? Im a linux newbie :-(

same here...kernel work ok on maverick...maybe there is a problem with the intel driver?

---

### Post by jerrylamos on 2011-01-21
> **Tommaso said:**
> same here...kernel work ok on maverick...maybe there is a problem with the intel driver?

I've got bugs out on "Compiz" which is certainly changed from maverick....Compiz is trying to do all sorts of shading and ovelays and 3D and whatever stunts they can think of which is breaking on a lot of different hardware.

Stay tuned....

Jerry

---

### Post by migrate from windows on 2011-01-22
> **James Keating said:**
> This kernel works the best for me so far. Thank you. The only glitch I observe on my machine is that upon resuming after suspending, the screen lighting is dimmed by one level. This is a very minor annoyance, easily fixed each time with the Fn-brighten key combination.

Most kernels choke when I try to run any kind of video or Gnome programs and their kin (Firefox, gjiten, Geeqie). Until now, I was relying on kernel 2.6.34-020634rc7, but that was iffy too. 

My computer is an NEC VersaPro VY15F laptop with  an Intel 82852/82855 graphics chip.

I have kept changes to two lines in xorg.conf, Section "Device":
Identifier "Configured Video Device"
Driver "intel"
Option "DRI" "off"
EndSection

I have also kept the modeset=1 parameter in /etc/defaults/grub: 
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"

In a decade of using Linux, this is the most serious problem I have ever encounted. Not only couldn't I boot after upgrading the last two times, but the solution was almost completely different the second time. This kernel works, and I hope the patch gets into Natty so I don't spend another day or two struggling with the next upgrade.

@Jameskeating can u pls post a copy of ypur xorg.conf and /etc/defaults/grub

---

### Post by James Keating on 2011-02-09
my /etc/X11/xorg.conf 
with one section modified:
Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"intel"
	Option 		"DRI" "off"
EndSection


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"intel"
	Option 		"DRI" "off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

--------------------------------------------------------------------

my /etc/default/grub
with one line modified:
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# before Lucid  GRUB_CMDLINE_LINUX_DEFAULT="nosplash i915.modeset=0 nomodeset"
GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=1"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by cooper_d on 2011-03-02
I have installed the patched kernel on Ubuntu 10.10 but am still getting issues with page flipping for my 855gm graphics card.

If I use a screensaver with rotating shapes, for example, they preview perfectly in the full screen view.  However, when the screensaver starts naturally after the preset time 'syslog' and 'kern.log' literally fill my disk up with the following errors:

Mar  2 09:28:48 dave-laptop kernel: [  268.018755] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018773] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018791] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018808] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018826] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018844] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018862] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018879] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018897] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018915] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018933] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018951] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018969] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.018986] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.019004] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.019022] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.019040] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.019058] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Mar  2 09:28:48 dave-laptop kernel: [  268.019075] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times

Does anyone know how to fix this? I have tried disabling graphic acceleration but then the screensavers are all jerky and presumably games won't run smoothly either but I certainly don't get the error messages.

---

### Post by jerrylamos on 2011-03-03
Just installed Natty 02 March Daily Build on i845 video graphics using whatever defaults the .iso had.  Running O.K. in classic mode no effects.

Jerry

---

### Post by useResa on 2011-03-04
> **jerrylamos said:**
> Just installed Natty 02 March Daily Build on i845 video graphics using whatever defaults the .iso had.  Running O.K. in classic mode no effects.I have the same experience ... no modification to the standard setting gives me a working desktop although not as fancy as it can be (from my understanding), see screenshot. This is an installation on a Dell Dimension 2400 with an 845 intel graphics card.
Kernel version: 2.6.38-5-generic
Intel driver version: 2:2.14.0-4ubuntu1
Graphics card: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

What I understand from the hardware lister is that in this mode the i915 driver is used (see also screenshot). If I try to use the intel driver by creating an xorg.conf as suggested in the wiki [here]("https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus"), I get all sorts of errors. If I try to report them I can't since my keyboard does not work and I can thus not sign in into launchpad.

Furthermore, for some reason, the maximum resolution I can get is 1024x768 while in 10.10 on this box I can use 1440x900. Any suggestions on how I can improve this? Tried using xorg.conf to fix this, but that did not work (so far)

UPDATE: Noticed the following error several times in "dmesg":
```
[ 1016.112878] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[ 1016.164259] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 65
```
The numbers in the brackets change every time btw.

---

### Post by XenoPhoenix on 2011-04-11
> **cooper_d said:**
> 
Mar  2 09:28:48 dave-laptop kernel: [  268.018755] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times

Does anyone know how to fix this? I have tried disabling graphic acceleration but then the screensavers are all jerky and presumably games won't run smoothly either but I certainly don't get the error messages.

I am experiencing exactly the same issue. Trying to run XBMC only on natty minimal install and acceleration is working though that error message is constantly written to the syslog every frame resulting in rsyslogd consumeing 30% of my CPU and having 12G of logs in about an hour!!

From a little bit of search this appears to be a kernel issue introduced between 2.6.35 and 2.6.36 though that is far from certain.

Hopefully if more people notice this it will be fixed!

---

### Post by heiko81 on 2011-04-13
So after having tried Ubuntu 11.04 on my laptop from its alpha 3, I have something useful to share...
this is my video card (as from lspci):

Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I installed Ubuntu 11.04 and there is no Unity because of the lack of 3D..but the Classic desktop starts with no problem at all and without doing anything (Xorg, ecc)..

the 3 biggest problems I found are:
- like I said previously, compiz doesn't work and so unity and every other program that requires 3D (like Docky);
- I didn't make it to play high quality movies in .avi with vlc, totem, mplayer;
- there are some pixels in the notification area and indicator panels that are showing something else, maybe the desktop backgrund (but the icons are visible and everything is usable, so this is not a big problem).

So I tried to solve these problem installing the Ubuntu Xorg edgers PPA...this solved the last 2 problems and I think that it is a positive thing and I feel to recommend it to everyone having the same problems...
also, if you need compositing, you could use xcompmgr to replace compiz, just add it to the start programs..it works flawlessly, obviously unity doesn't work..but AWN and Docky work without any problem..and then the first problem will be gone too, if you don't need Unity..I'd like it, but maybe we should wait a little more to try it..
there should be a chance to savour it installing the Unity 2d ppa..maybe I'll give it a try and I'll let you know..

hope this would be of some help..bye..

EDIT: I tried the unity 2d ppa and it is awesome and works perfectly, I haven't had any problem till now..I suggest it to everyone with the same video card..it is a different way to try unity..bye..

---

### Post by Anthony25 on 2011-04-14
Hello,
There is a new version of the Glasen' fix, the 2.15 but it doesn't solve the problem for me (if I force the hardware acceleration so I have some artifacts) ...

I hope there will be a news fix which will definitely solve the problem

---

