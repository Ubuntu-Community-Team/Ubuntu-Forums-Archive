---
title: "PLEASE READ: Turbulence ahead: New X stack coming to natty"
date: 2011-01-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-01-25
I got this email this afternoon:

> ********************************************************************
tl;dr:  X is getting a major update this week for natty.  Be careful
when upgrading the next few days.
********************************************************************


Thanks everyone who tested xorg-edgers.  Feedback has been positive and
everything looks good to go.

We are currently uploading the dependencies for this new X stack into
Natty, as you may have noticed.  Our goal is to get it all in by
Friday for the Alpha-2 release coming next week.

We have already uploaded various prerequisites and dependencies.  This
includes major updates for libdrm and mesa, which are worth special
mention.  This includes improved OpenGL functionality, Sandy Bridge
support, and a variety of bug fixes.  For full details see
[http://mesa3d.org/relnotes-7.10.html]("http://mesa3d.org/relnotes-7.10.html").  It also includes some changes to
ABI packaging which may affect other packages dependent on libdrm driver
packages.  Please keep an eye out for regressions in 3D functionality or
packaging issues associated with libdrm or mesa.

A variety of driver updates is also planned for the coming week,
including -intel, -ati, -nouveau, -synaptics, etc.  We're going to try
to get these updates in prior to the xserver update where possible.

xserver 1.10 will be updated probably Wednesday or Thursday.  This
server has a new server and video ABI, which means existing driver
packages will break.

The server needs to be uploaded first so the new drivers build against
the correct ABI, which means that there will be a period where safe
upgrades will have held-back packages.  The dependencies should ensure
that you won't accidentally get a non-working combination of Xserver and
drivers, but be careful if an upgrade wants to remove X packages.

We are also going to be demoting several of the really obscure/ancient X
drivers (apm, ark, chips, glide, i740, tseng, and voodoo; perhaps more)
that no one seems to use.  These will still be in the archive (for now)
but will live only in universe and require manual installation by anyone
that happens to need them.  If you particularly care about any of these
drivers, just let us know.


---

### Post by VMC on 2011-01-25
Since I rarely update Natty, but instead use zsync to install new ISO almost every day or when there's is a new ISO, this will be interesting to see how my nvidia works with this new xorg.

Maybe natty changes will list the new files when they become available.

Thanks for the info.

---

### Post by Quackers on 2011-01-26
Thanks cariboo907, I'll clean my glasses :wink:

---

### Post by Harry33 on 2011-01-26
> **VMC said:**
> Since I rarely update Natty, but instead use zsync to install new ISO almost every day or when there's is a new ISO, this will be interesting to see how my nvidia works with this new xorg.

Maybe natty changes will list the new files when they become available.

Thanks for the info.

NVidia cards with the binary driver (nvidia-current) will not work with the latest xserver 1.10 (rc 2 series).
The git snapshot version in xorg-edgers is already unsupported by nvidia-current (because of the new ABI).
So, not even the latest nvidia-current_270.18 will work, even if you add these lines in xorg conf:
```

Section "ServerFlags"
    Option "IgnoreABI" "True"
EndSection

```

---

### Post by kansasnoob on 2011-01-26
Thanks for posting this. I was thinking about trying a new daily but now I think I'll wait for the official iso-testing release.

---

### Post by VMC on 2011-01-26
> **Harry33 said:**
> NVidia cards with the binary driver (nvidia-current) will not work with the latest xserver 1.10 (rc 2 series).
The git snapshot version in xorg-edgers is already unsupported by nvidia-current (because of the new ABI).
So, not even the latest nvidia-current_270.18 will work, even if you add these lines in xorg conf:
```

Section "ServerFlags"
    Option "IgnoreABI" "True"
EndSection

```

I use nvidia driver from their web page and it has worked flawlessly since using natty.

---

### Post by mexlinux on 2011-01-26
OK, I already screwd my natty instalation by making a dist-upgrade.... 
any idea on how do I resolve it?

---

### Post by Roger E Critchlow Jr on 2011-01-26
Mine has been a total botch all along.  No menus work on the desktop, it never writes a usable grub.cfg, and today it just black screens on boot.

Boot the natty "recovery" image from the grub menu, drop into a root shell, do: 

    apt-get update && apt-get dist-upgrade && reboot

until it gets better.  I promise, it will get better, but I can't promise when it will get better.

If you've lost the grub entry for an alternate system on your disk because update-grub reported the partition as unwritable (why is update-grub trying to mount with write permission?) as it did for /dev/sda5 on my machine, then

  mount /dev/sda5 /mnt && umount /dev/sda5 && update-grub

may succeed in recovering the missing boot entries.  It's easier than rewriting grub.cfg by hand.

Personally, I think I'll just check back for updates sometime next week,

-- rec --

---

### Post by kyleabaker on 2011-01-26
My nvidia computer stops during boot after updates, so I'm assuming its due to the video updates. I'm not using any restricted drivers so I'm hoping that updating in tty1 with eventually fix it. I don't see any direct errors.

EDIT:
Although, "libdrm-nouveau1a" is being kept back atm and I'm pretty sure thats whats causing the current problem. :/

---

### Post by cariboo on 2011-01-26
I personally use:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

and will continue doing so until the drivers have caught up withe the new X stack.

---

### Post by kyleabaker on 2011-01-26
> **cariboo907 said:**
> I personally use:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

and will continue doing so until the drivers have caught up withe the new X stack.

An update for xserver-xorg-video-nouveau just came through and fixed my video issue. :guitar:

Also, I'll probably use safe-upgrade from now on. :D

---

### Post by MacUntu on 2011-01-27
Boot-to-black with i915 and KMS enabled. :-(

That is, until you update xserver-xorg-video-intel. :D

---

### Post by Harry33 on 2011-01-27
Please note that new video and input drivers are just now being upgraded into Natty's official repo.
ATM there are new video drivers:
 - intel (2:2.14.0-1ubuntu2),
 - nouveau (1:0.0.16+git20110107+b795ca6e-0ubuntu)
and new input driver
 - synaptic (1.3.99+git20110116.0e27ce3a-0ubuntu1)

These new drivers are built to support both xserver 1.9 series and xserver 1.10 (rc1) series.

This means people using Natty can upgrade these as soon as possible.


Note also that after upgrading the new plymouth (0.8.2-2ubuntu13), libdrm packages must be upgraded.
Package libdrm-nouveau1 can be removed, the new one is libdrm-nouveau1a.

---

### Post by go7Ul1ai on 2011-01-27
So is it safe for me to update my system now or shall I carry on waiting??

Edit: nevermind, risked it and my machine still works

---

### Post by Harry33 on 2011-01-27
> **lee.jarratt said:**
> So is it safe for me to update my system now or shall I carry on waiting??

Edit: nevermind, risked it and my machine still works

Like you did and said, drivers should be updated.

---

### Post by terry_gardener on 2011-01-27
is it safe to upgrade if you are using the nvidia-current drivers from repo (not ppa) 
thanks

---

### Post by Harry33 on 2011-01-27
> **terry_gardener said:**
> is it safe to upgrade if you are using the nvidia-current drivers from repo (not ppa) 
thanks

Well if you are using binary drivers of Nvidia, you do not need to upgrade anything yet.
There are intel and nouveau video drivers available.
If you have a laptop, then you should upgrade the synaptic input driver.

But about the coming upgrades, do not upgrade xserver 1.10 series (1.9.99.901).
Nvidia-current_260 does not support it, and it is possible that 270 version do not either.

---

### Post by tghe-retford on 2011-01-27
> **terry_gardener said:**
> is it safe to upgrade if you are using the nvidia-current drivers from repo (not ppa)
Yes, for now.

The only Xorg upgrades I have seen so far relate to Nouveau and Synaptics as explained above, no show-stopping Xorg updates on my desktop so far.

I'm just waiting for the time when I might have to start holding back updates of packages.

---

### Post by terry_gardener on 2011-01-27
thank you harry and retford 

i have updated and no problems.

---

### Post by jerrylamos on 2011-01-28
> **Harry33 said:**
> Please note that new video and input drivers are just now being upgraded into Natty's official repo.
ATM there are new video drivers:
 - intel (2:2.14.0-1ubuntu2),
 - nouveau (1:0.0.16+git20110107+b795ca6e-0ubuntu)
and new input driver
 - synaptic (1.3.99+git20110116.0e27ce3a-0ubuntu1)

These new drivers are built to support both xserver 1.9 series and xserver 1.10 (rc1) series.

This means people using Natty can upgrade these as soon as possible.


Note also that after upgrading the new plymouth (0.8.2-2ubuntu13), libdrm packages must be upgraded.
Package libdrm-nouveau1 can be removed, the new one is libdrm-nouveau1a.

Oops.  Acer Aspire one D255E netbook intel N10 video graphics was running Unity 3D fine earlier today.  

Then the "dread update" struck.  Boots to black screen no matter what I try.

I can get as far as recovery mode fix broken packages so I'll try that tomorrow...

Jerry

---

### Post by Harry33 on 2011-01-29
> **jerrylamos said:**
> Oops.  Acer Aspire one D255E netbook intel N10 video graphics was running Unity 3D fine earlier today.  

Then the "dread update" struck.  Boots to black screen no matter what I try.

I can get as far as recovery mode fix broken packages so I'll try that tomorrow...

Jerry

Jerry,
check if have you upgraded xserver-xorg-input-evdev (1:2.6.0-1ubuntu1) before the breakage.
For me (with nvidia-current and xserver 1.92) it does not boot.
I had to downgrade evdev package.

I have to check this more indepth, because I am not using Natty official xserver 1.9.0.

---

### Post by ratcheer on 2011-01-29
Is there a version of the nVidia proprietary driver that works with the new X, yet?

Tim

---

### Post by sgage on 2011-01-29
> **Harry33 said:**
> But about the coming upgrades, do not upgrade xserver 1.10 series (1.9.99.901).
Nvidia-current_260 does not support it, and it is possible that 270 version do not either.

Any idea when xserver 1.10 (1.9.99.901) will be on the repo's? I've already backed off from nvidia-current to nouveau in preparation, but if it's going to be a few more days I'll put nvidia-current back on...

---

### Post by Harry33 on 2011-01-29
> **ratcheer said:**
> Is there a version of the nVidia proprietary driver that works with the new X, yet?
Tim

NVidia_270.18 has a preliminary support for xserver 1.10 rc1.
Nvidia-current can be downloaded from xorg-edgers PPA,
but xserver 1.10rc1 is not there any more.
There is this later git version (20110124), which is not supported yet.

Then again, there is no xserver 1.10 version in Natty repos yet.
We ought to wait a bit more, perhaps a week or so.

---

### Post by Harry33 on 2011-01-29
> **sgage said:**
> Any idea when xserver 1.10 (1.9.99.901) will be on the repo's? I've already backed off from nvidia-current to nouveau in preparation, but if it's going to be a few more days I'll put nvidia-current back on...

Perhaps next week.

---

### Post by tghe-retford on 2011-01-29
The xserver-xorg-input-evdev 1:2.6.0-1ubuntu1 upgrade did nasty things to my computer today.

[FONT="Courier New"]sudo aptitude hold xserver-xorg-input-evdev[/FONT] ensures it won't happen again until Xorg and its packages have stablised, then [FONT="Courier New"]sudo aptitude unhold xserver-xorg-input-evdev[/FONT] should allow it to upgrade again. Just have to remember what I held (/var/log/aptitude tells me what is held), and it's worth nothing I do almost everything with Aptitude.

Whilst I can stand and accept things breaking during testing, Xorg ain't one of them!

---

### Post by inportb on 2011-01-29
lol, I forgot to RTFP and had to reinstall twice, on Friday and just now. I have learned my lesson, and I now have a *buntu 10.10 recovery partition :P

---

### Post by Harry33 on 2011-01-30
Regarding xserver-xorg-input-evdev_2.6.0 there is a bug report with a lot of duplicates:
# bug709977
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/709977](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/709977)

---

### Post by zika on 2011-01-30
It is not global: After I've made everything ready for rescue, if a bug strikes, it (all) went OK...
AMD_64, ATI...

---

### Post by miegiel on 2011-01-30
> **tghe-retford said:**
> The xserver-xorg-input-evdev 1:2.6.0-1ubuntu1 upgrade did nasty things to my computer today.

[FONT="Courier New"]sudo aptitude hold xserver-xorg-input-evdev[/FONT] ensures it won't happen again until Xorg and its packages have stablised, then [FONT="Courier New"]sudo aptitude unhold xserver-xorg-input-evdev[/FONT] should allow it to upgrade again. Just have to remember what I held (/var/log/aptitude tells me what is held), and it's worth nothing I do almost everything with Aptitude.

Whilst I can stand and accept things breaking during testing, Xorg ain't one of them!

Thanks, ```
sudo aptitude hold xserver-xorg-input-evdev
``` was exactly what I needed. As long as I don't use the graphical updater or *apt-get* and use ```
sudo aptitude upgrade
``` instead, the *xserver-xorg-input-evdev* package will be held back.

Now I need to figure out how to know when it's safe to install the *xserver-xorg-input-evdev* package. And how to revert the installation of the package on my other (main) xubuntu installation (I installed xubuntu twice in a dualboot).

---

### Post by Harry33 on 2011-01-30
There is a new xserver-xorg-input-evdev (2.6.0-1ubuntu2) in Launchpad now in order to fix this issue (bug # 709977).

Go ahead and test it.
Here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2)

---

### Post by Harry33 on 2011-01-30
Right I have tested now the new version of
xserver-xorg-input-evdev (2.6.0-1ubuntu2)
and I can confirm it fixes the segfaulting issue.

This was the fix:
```
Disable patch 101-gestures.patch - Fix SIGSEGV in xserver.

```
The update is already in Natty repos (main server).
Others may download it form here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2)

---

### Post by miegiel on 2011-01-30
> **Harry33 said:**
> There is a new xserver-xorg-input-evdev (2.6.0-1ubuntu2) in Launchpad now in order to fix this issue (bug # 709977).

Go ahead and test it.
Here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2)

Thanks, I just grabbed [xserver-xorg-input-evdev_2.6.0-1ubuntu2_i386.deb]("https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2/+buildjob/2232978/+files/xserver-xorg-input-evdev_2.6.0-1ubuntu2_i386.deb") (actually I grabbed all 3 but I only needed to install this package), booted to rescue mode, installed it and rebooted.

It's up and running again, everything looks good from here (do I need to report that somewhere?).

---

### Post by Harry33 on 2011-01-30
> **miegiel said:**
> Thanks, I just grabbed [xserver-xorg-input-evdev_2.6.0-1ubuntu2_i386.deb]("https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2/+buildjob/2232978/+files/xserver-xorg-input-evdev_2.6.0-1ubuntu2_i386.deb") (actually I grabbed all 3 but I only needed to install this package), booted to rescue mode, installed it and rebooted.

It's up and running again, everything looks good from here (do I need to report that somewhere?).

Actually the fix has been confirmed in Launchpad many times already, so no need to report it.;)

---

### Post by maheshasolkar on 2011-01-30
> **Harry33 said:**
> There is a new xserver-xorg-input-evdev (2.6.0-1ubuntu2) in Launchpad now in order to fix this issue (bug # 709977).

Go ahead and test it.
Here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2)

That got machine up and running again! (Nvidia 8400GS/64-bit - with nvidia-current from the repository).

Thanks Devs!

---

### Post by ratcheer on 2011-01-31
Is this the one?

Changes:
 xorg-server (2:1.9.99.901+git20110131.be3be758-0ubuntu1) natty; urgency=low
 .
   * Merge from (unreleased) debian-experimental.  Remaining Ubuntu changes

Tim

---

### Post by Quackers on 2011-02-01
I ran all updates except xserver.xorg ones and rebooted. I got all the keyboard lights flashing and no display. I presume this is some sort of kernel panic but without the display? Anyway, on reboot all was fine, so I don't know what caused that.
As I am running the nvidia-current driver I have not run any of the xserver.xorg updates, as one of those wants to remove nvidia-current.
Is it safe to run all of the updates that don't want to remove nvidia-current? I presume so. I ask because there are about 25 updates to hold, if that's not the case :-)
Thanks

---

### Post by Harry33 on 2011-02-01
New xserver 1.10 rc1 (2:1.9.99.901+git20110131.be3be758-0ubuntu1) will break your system as it is now.
Also package xserver-xorg depends on this new xserver 1.10 rc1.
Do not upgrade these now.

First of all, because of incorrect dependencies and related demands, it will remove or break your xserver-xorg-input-evdev driver (that means no kb and no mouse)!

The incorrect dependencies are explained here.
First I must explain that these xserver and driver packages are marked (with virtual packages) to relate to the correct ABI. That means a correct xserver needs a correct driver.
It works like this:
xserver (xserver-xorg-core) produces virtual packages xorg-video-abi-* and xorg-input-abi-*,
then,
input driver (xserver-xorg-input-*) depends on xorg-input-abi-*
and
video driver (xserver-xorg-video-*) depends on xserver-video-abi-*.

Right now these do not match and hence the system tries to remove necessary packages causing a breakage.

---

### Post by Quackers on 2011-02-01
Ok, thanks Harry33, I'll hold them then :-)

---

### Post by zika on 2011-02-01
What about *aptitude safe-upgrade*```
Resolving dependencies...                
The following packages will be upgraded:
  bluez bluez-alsa bluez-cups bluez-gstreamer chromium-browser 
  chromium-browser-inspector chromium-codecs-ffmpeg empathy empathy-common 
  gcalctool gir1.2-atk-1.0 gnome-orca google-chrome-unstable libatk1.0-0 
  libatk1.0-data libbluetooth3 libdb4.8 libdbusmenu-glib3 libdbusmenu-gtk3 
  libgexiv2-0 libgmime-2.4-2 libgmime2.4-cil libssl-dev libssl0.9.8 
  mousetweaks nautilus-sendto-empathy openssl update-manager 
  update-manager-core x11-common xorg xserver-common xserver-xorg-input-all 
  xserver-xorg-video-all 
```...?
Is this safe?

---

### Post by dino99 on 2011-02-01
> **zika said:**
> What about *gaptitude safe-upgrade*[code]Resolving dependencies...

Is this safe?

seems to be

---

### Post by zika on 2011-02-01
> **dino99 said:**
> seems to be\\:D/ We're alive! Thank You... :)

---

### Post by Harry33 on 2011-02-01
Here is an update to what I wrote earlier.

Xserver 1.10 rc1 (2:1.9.99.901+git20110131) provides virtual packages
xorg-input-abi-12.1 and xorg-video-abi-9.

Now the newest input drivers, like
```
xserver-xorg-input-evdev 2.6.0-1ubuntu6
xserver-xorg-input-synaptics 1.3.99+git20110116.0e27ce3a-0ubuntu3

```all depend on the same virtual package
xorg-input-abi-12.1.

And the newest video drivers, like
```
xserver-xorg-video-intel 2:2.14.0-1ubuntu4
xserver-xorg-video-ati 1:6.13.2+git20110124.fadee040-0ubuntu4
xserver-xorg-video-nouveau 1:0.0.16+git20110107+b795ca6e-0ubuntu4
xserver-xorg-video-vesa 2.3.0-4ubuntu1

```all depend on the same virtual package
xorg-video-abi-9.

So, this means they are compatible. All of them are already in Natty repos.
You may now try upgrading those. But only if you use open source ati/radeon or nouveau or intel drivers.
Remember at the same time to upgrade also these three
xorg packages:
```
x11-common 7.6~3ubuntu1
xorg 7.6~3ubuntu1
xserver-xorg 7.6~3ubuntu1

```
Because not all input drivers have been upgraded in Natty repos, the above mentioned upgrading will remove the old drivers (old ABI).
See what drivers are shown to be removed, if you need one or more of them,
do not upgrade yet.

People using nvidia-current (like me), do not upgrade. May end up black screen and reversing demands skills to use terminal (recovery mode).

---

### Post by cecilpierce on 2011-02-01
Gee ! I wish I read this a few minutes ago, trashed two installs, got two more to mess with ):P

---

### Post by tghe-retford on 2011-02-01
As I am using nvidia-current, I have done the following:

```
sudo aptitude hold ~nxserver x11-common
```

to hold back all packages with xserver in their name and x11-common. Now when I do a safe-upgrade, there is now no Xorg packages waiting to be upgraded. Just to make sure, will this keep things at bay until nvidia-current is upgraded and I can then unhold the above packages?

---

### Post by Harry33 on 2011-02-01
> **tghe-retford said:**
> As I am using nvidia-current, I have done the following:

```
sudo aptitude hold ~nxserver x11-common
```

to hold back all packages with xserver in their name and x11-common. Now when I do a safe-upgrade, there is now no Xorg packages waiting to be upgraded. Just to make sure, will this keep things at bay until nvidia-current is upgraded and I can then unhold the above packages?

For those, who use Synaptic the same goes like this:
In Synaptic click once the package (or holding shift pressed as many packages as you like) you want to lock from updates.
Then choose from the menu - Package
and set option "Lock Version" on.

---

### Post by mc4man on 2011-02-01
The x11-common is safe to upgrade though doesn't particularly matter one way or the other. (probably needed for apport, though apport is liable to produce numerous 'false' reports anyway

---

### Post by plun on 2011-02-01
Maybe time for the official message about this:

[https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html](https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html)

#-o

---

### Post by tjeremiah on 2011-02-01
> **plun said:**
> Maybe time for the official message about this:

[https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html](https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html)

#-o
I dont know if this was the cause of my problem but I updated about 20 minutes ago and Unity fails to load. So now im using the classic Desktop or w/e its called. I safe upgraded too.

---

### Post by BegbieThesec on 2011-02-01
So, I also updated some hour ago, Unity won't start, but I can't choose classic gnome because I had automatic login on. Any ideas how to work this around?

---

### Post by coffeecat on 2011-02-01
> **tjeremiah said:**
> I dont know if this was the cause of my problem but I updated about 20 minutes ago and Unity fails to load. So now im using the classic Desktop or w/e its called. I safe upgraded too.

What graphics and what driver? This might help:

[http://ubuntuforums.org/showthread.php?t=1679795](http://ubuntuforums.org/showthread.php?t=1679795)

It worked for me.

> **BegbieThesec said:**
> So, I also updated some hour ago, Unity won't start, but I can't choose classic gnome because I had automatic login on. Any ideas how to work this around?

When my Unity broke, I simply got the classic desktop when I tried to log into Unity. Do you get no GUI at all?

---

### Post by BegbieThesec on 2011-02-01
Yeah, no GUI at all, purple screen with "ubuntu" as always, some stripes appears on that and freezes. It's my fault, I did some weird partial upgrades.

Maybe some fixes in updates will fix this for me, is there a way to update my Natty from live cd of Ubu? 

But I guess I will make fresh install of Alpha 2. If it will be released soon. Is date of 2011/02/03 unchanged?

---

### Post by tjeremiah on 2011-02-01
> **coffeecat said:**
> What graphics and what driver? This might help:

[http://ubuntuforums.org/showthread.php?t=1679795](http://ubuntuforums.org/showthread.php?t=1679795)

It worked for me.

Thanks. That fixed my problem ;)

---

### Post by coffeecat on 2011-02-01
> **BegbieThesec said:**
> Yeah, no GUI at all, purple screen with "ubuntu" as always, some stripes appears on that and freezes. It's my fault, I did some weird partial upgrades.

Maybe some fixes in updates will fix this for me, is there a way to update my Natty from live cd of Ubu? 

But I guess I will make fresh install of Alpha 2. If it will be released soon. Is date of 2011/02/03 unchanged?

I'd be wary of Alpha2. Or at least keep an eye on the bug report linked from the thread I linked. This bug report:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/711401](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/711401)

They'll have to be quick to get bugfixed libglew and libglewmx out in time for Alpha2, so there's a danger that Alpha2 will come out with the bad libglew and libglewmx and you'll still have a broken Unity. But at least you'll have a bootable system, albeit into the classic desktop.

Or you could wait until the bug report tells you that replacement libglew* packages have hit the repos and then boot in recovery mode to a root console with networking where you will be able to update the system, and hopefully fix whatever the partial upgrade broke.

---

### Post by kyleabaker on 2011-02-01
> **BegbieThesec said:**
> Yeah, no GUI at all, purple screen with "ubuntu" as always, some stripes appears on that and freezes. It's my fault, I did some weird partial upgrades.

Maybe some fixes in updates will fix this for me, is there a way to update my Natty from live cd of Ubu? 

But I guess I will make fresh install of Alpha 2. If it will be released soon. Is date of 2011/02/03 unchanged?

It's still slated for that date:
[https://wiki.ubuntu.com/NattyReleaseSchedule](https://wiki.ubuntu.com/NattyReleaseSchedule)

I don't think they would release Alpha 2 with this current Unity crash. I'm planning to continue updates with my broken gui or in recovery mode until the problem solves itself, and that should be by Thursday (I'm only assuming).

---

### Post by cariboo on 2011-02-01
Even though there is a soft feature freeze on for alpha 2, bug fixes will still make it in  before release.

---

### Post by webme on 2011-02-01
> **BegbieThesec said:**
> Yeah, no GUI at all, purple screen 

Maybe some fixes in updates will fix this for me, is there a way to update my Natty from live cd of Ubu? 


On Grub, choose "2.6.38 recovery mode" and then select dpkg broken packages.(Do this from your current installation, no need for a live cd).

---

### Post by mc4man on 2011-02-01
> Or you could wait until the bug report tells you 
For the moment the glew packages will be reverted back to previous.

Myself though don't see a 3d option for nvidia cards that will work with the new X, at least as the packages stand now.

---

### Post by BegbieThesec on 2011-02-02
Thx webme, I did that, few packages were updated and now I'm able to launch (classic gnome) from "safe graphic mode", still no luck when booting it normal way.

Anyway, my nvidia drivers were uninstalled yesterday during some weird update as I said before... Is it just me or it suppose to happen? When I try to install them through "extra drivers" in administration in menu (as I always did), it seems to remove a lot of xorg related packages, so when I reboot, even safe mode won't load up, saying something about missing x etc.

Hm... In "Extra drivers" I can choose some "Experimental 3D support for NVIDIA cards" I did not try that one... And interesting - with those at least "safe graphic mode" is on, but no 3d support etc, so it's kind of phantom drivers. ;)

Ok, "... which means existing driver packages will break", I guess first post in this topic means that I shouldn't be surprised and wait for updates. Thanks for a tip about recovery mode, useful for the future.

---

### Post by Harry33 on 2011-02-02
> **BegbieThesec said:**
> Thx webme, I did that, few packages were updated and now I'm able to launch (classic gnome) from "safe graphic mode", still no luck when booting it normal way.

Anyway, my nvidia drivers were uninstalled yesterday during some weird update as I said before... Is it just me or it suppose to happen? When I try to install them through "extra drivers" in administration in menu (as I always did), it seems to remove a lot of xorg related packages, so when I reboot, even safe mode won't load up, saying something about missing x etc.

Hm... In "Extra drivers" I can choose some "Experimental 3D support for NVIDIA cards" I did not try that one... And interesting - with those at least "safe graphic mode" is on, but no 3d support etc, so it's kind of phantom drivers. ;)

Ok, "... which means existing driver packages will break", I guess first post in this topic means that I shouldn't be surprised and wait for updates. Thanks for a tip about recovery mode, useful for the future.

You cannot install new xserver 1.10 rc1 if you have the stable nvidia-current (Nvidia proprietary drivers) package installed. Nvidia-current_260.19.29 (and earlier versions) provides a virtual package
xorg-video-abi-8.
Now, the new xserver 1.10 rc1 breaks that abi-8.

That is what happened. With new xserver you can only use nouveau (or nv) driver for Nvidia graphic cards.

Out of curiosity, you can also get the new Nvidia beta driver (270.18 ) from xorg-edgers PPA,
it will install even with xserver 1.10, but it will not support it => black screen after plymouth, no gdm.

---

### Post by BegbieThesec on 2011-02-02
That solves the puzzle! Thanks Harry.

Still no luck in booting into gdm, only "safe graphic mode", but at least something gave my Natty back! Kind of. Waiting for juicy updates and fixes.

---

### Post by zika on 2011-02-02
Was all this with NV users preventable by using &#8222;aptitude safe-upgrade&#8220;...?
It seems to me that only those that used UM or Synaptic got bitten...
As ATI user I can, just, ask...
It seems to me that transistion was handled just right. Good job dev's... I waited long enough to have all dependencies fulfilled and...
We learned a lot from previous testing periods... (LL,MM)
[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by sgage on 2011-02-02
Synaptic tells you exactly what it's going to do. When you mark an upgrade, and it tells you it's going to remove half of Ubuntu, it's up to you to think "hmmm... maybe I ought to wait on this one".

---

### Post by zika on 2011-02-02
> **sgage said:**
> Synaptic tells you exactly what it's going to do. When you mark an upgrade, and it tells you it's going to remove half of Ubuntu, it's up to you to think "hmmm... maybe I ought to wait on this one".Exactly...
I think that so does UM...
I propose and advocate &#8222;aptitude safe-upgrade&#8220; because it takes that decision of Yours out of the loop... :)

What I was, really, asking was: If partial upgrade was not chosen, would NV users have been bitten...?

---

### Post by Harry33 on 2011-02-02
> **zika said:**
> Exactly...
I think that so does UM...
I propose and advocate „aptitude safe-upgrade“ because it takes that decision of Yours out of the loop... :)

What I was, really, asking was: If partial upgrade was not chosen, would NV users have been bitten...?

Yes.

With nvidia-current 260.19.29 (in Natty repos) it would have been uninstalled because of unmet dependencies.

With nvidia-current 270.18 (from xorgedgers PPA) no package would have been uninstalled. This is because 270.18 does not provide virtual package xorg-video-abi-8 nor any other viurtual package and thus there would have not been unmet dependencies.

Anyway the result would have been black screen (segfault) before gdm.

---

### Post by zika on 2011-02-02
> **Harry33 said:**
> Yes.

With nvidia-current 260.19.29 (in Natty repos) it would have been **uninstalled** because of unmet dependencies.

Anyway the result would have been black screen (segfault) before gdm.
With safe-upgrade?

---

### Post by Harry33 on 2011-02-02
> **BegbieThesec said:**
> That solves the puzzle! Thanks Harry.

Still no luck in booting into gdm, only "safe graphic mode", but at least something gave my Natty back! Kind of. Waiting for juicy updates and fixes.

So you have the xserver 1.10 rc1 now installed (packages xserver-common and xserver-xorg-core)?
And you have also the latest packages x11-common, xorg, xserver-xorg, xserver-xorg-input-evdev and xserver-xorg-video-vesa installed?

Did you remove nvidia-current completely (purged it)?
What video driver do you use now (nouveau)?
If it is nouveau please empty the file /etc/X11/xorg.conf.
And also check that nouveau is not blacklisted = remove the file (if it exists) /etc/modprobe.d/nvidia-graphics-drivers.conf

---

### Post by Harry33 on 2011-02-02
> **zika said:**
> With safe-upgrade?

Not so sure about the functionality of "safe-upgrade" in a situation where there are no unmet dependencies.
I myself use only Synaptic to really be sure what is happening and why.

---

### Post by BegbieThesec on 2011-02-02
Yes, I do have those packages. I use nouveau driver because others don't like packages you've mentioned (they want to remove them).

nvidia-current was removed during those evil partial upgrades (I know, I was stupid to do them), I did not remove them "manually".

I cleaned /etc/X11/xorg.conf as you wrote. 

"/etc/modprobe.d/nvidia-graphics-drivers.conf" does not exist.

And what's interesting, after that - Natty launched in "normal" way! Well... Unity won't work, but classic gnome runs fine, with all effects! So your tips was very useful, thanks.

---

### Post by zika on 2011-02-02
> **Harry33 said:**
> Not so sure about the functionality of "safe-upgrade" in a situation where there are no unmet dependencies.
I myself use only Synaptic to really be sure what is happening and why.My point exactly...
You are able to interpret what is happening and why...
Big difference.
On our local Ubuntu-forum, we have NV users that succumbed to the itch to do partial upgrade, and got into similar trouble You're helping BT with...
I remember that I was not able (enough), not so long ago, to interpret what is happening and why (if I could, now... I do hope I can, but...)...
That is why I do advocate use of safe-upgrade for those who are not sure they could interpret what is happening and why...
Again, because I do not use NV, I wonder if this transition was so clean for NV as it was for ATI (even though I'm using only open-source driver, all the time)... If there were dependencies set right, which I think was the case, as far as I could interpret files, no problem would emerge for NV users if no partial upgrade was performed...
Nevertheless, we are going ahead...

---

### Post by mc4man on 2011-02-02
> I wonder if this transition was so clean for NV as it was for ATI 
Only if a nv user was using nouveau (no 3d) before the upgrade

(If you have nouveau w/ no 3d then you'll always login to gnome-panel even if Ubuntu Desktop is selected at the login screen

If nvidia-current was removed as part of the upgrade then the current xorg.conf is not moved or removed and the reboot will fail

(if one was to use jockey-gtk to first return to nouveau (remoce nvidia-current), that also would be done improperly and a reboot would fail

---

### Post by sgage on 2011-02-02
> **mc4man said:**
> (if one was to use jockey-gtk to first return to nouveau (remoce nvidia-current), that also would be done improperly and a reboot would fail

Actually, I used jocky to return to nouveau from nvidia-current, and it was done properly (xorg.conf removed and all, reboot worked fine).

---

### Post by mc4man on 2011-02-02
> Actually, I used jocky to return to nouveau from nvidia-current, and it was done properly (xorg.conf removed and all, reboot worked fine).
Not working here w/ the latest jockey, plus the jockey screen is way oversized.
Am going to re-install to 1/27 to see if unity and nouveau 3d worked then, will also try that switch again

As far as current state of nouveau 3d and unity this bug is also what I get
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588)

---

### Post by Harry33 on 2011-02-02
> **zika said:**
> My point exactly...
You are able to interpret what is happening and why...
Big difference.
...


Zika, my text was not meant to upset you in any way.
What I wanted to say is this.
Using terminal commands like "sudo apt-get update & upgrade" (the worst possible one)
and even "sudo aptitude safe-upgrade"
one will see only a part of the information one can get from using Synaptic.
In particular, when packages are upgraded one by one, also checking dependencies, dependants and possible provided packages.
I do believe that with Synaptic any user will learn faster about the composition and dynamics of the whole Ubuntu system, and will less likely end up reinstalling from CD.

---

### Post by zika on 2011-02-02
> **Harry33 said:**
> Zika, my text was not meant to upset you in any way.
What I wanted to say is this.
Using terminal commands like "sudo apt-get update & upgrade" (the worst possible one)
and even "sudo aptitude safe-upgrade"
one will see only a part of the information one can get from using Synaptic.
In particular, when packages are upgraded one by one, also checking dependencies, dependants and possible provided packages.
I do believe that with Synaptic any user will learn faster about the composition and dynamics of the whole Ubuntu system, and will less likely end up reinstalling from CD.
Oh, but You did not upset me, in any way, really. It must be that I did not convey my thoughts in my writing, precise and right...
We do have different opinion on what tool to use, but that is natural. I think that diversity is the good thing...
I'm sorry if I led You to believe that I'm upset in any way...
I feel (partly because I see how it affects me. Finally I've learned how to restrain myself...) that Synaptic (by offering partial upgrades) is provoking more partial upgrades than the method I advocate... Just that...
But, of course, that is just my opinion.
I was, mainly, exploring what is the situation with NV because we get questions on our local UF (about NN) and I do not have NV to play with...
Cheers!

---

### Post by thhart on 2011-02-03
> **mc4man said:**
> Not working here w/ the latest jockey, plus the jockey screen is way oversized.
Am going to re-install to 1/27 to see if unity and nouveau 3d worked then, will also try that switch again

As far as current state of nouveau 3d and unity this bug is also what I get
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588)

Can you let me know how to get back to 1/27? Is there a repository  with older version kept? Can I backjump to a date with the package tools?

BTW, even the nouvea driver has some problems at least with me:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/711434](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/711434)

Thanks
Thomas

---

### Post by BegbieThesec on 2011-02-03
Hm... Some updated were here, but still - when I want to install nvidia-current, it wants to remove a lot of xorg packages. I can have only nouveau driver, but with that, Unity won't load up, must use classic gnome.

I wonder will it be fixed (able to install nvidia-current) or should I reinstall my Natty when Alpha2 will be released (I guess it's the same as just updating, but who knows)?

---

### Post by oasick on 2011-02-03
> **BegbieThesec said:**
> Hm... Some updated were here, but still - when I want to install nvidia-current, it wants to remove a lot of xorg packages. I can have only nouveau driver, but with that, Unity won't load up, must use classic gnome.

I wonder will it be fixed (able to install nvidia-current) or should I reinstall my Natty when Alpha2 will be released (I guess it's the same as just updating, but who knows)?

Install libgl1-dri-experimental package to have 3D acceleration with nouveau driver. Unity can load up with this ;)

---

### Post by BegbieThesec on 2011-02-03
> **oasick said:**
> Install libgl1-dri-experimental package to have 3D acceleration with nouveau driver. Unity can load up with this ;)

I do have that package and in classic gnome I have 3d support, all effects etc, that's why it surprise me. When I choose Unity in gdm all I got is desktop with icons on it, no unity, no compiz.

---

### Post by mc4man on 2011-02-03
> **BegbieThesec said:**
> I do have that package and in classic gnome I have 3d support, all effects etc, that's why it surprise me. When I choose Unity in gdm all I got is desktop with icons on it, no unity, no compiz.
ck. the LP link I gave at bottom of post 73

---

### Post by Yougo on 2011-02-03
it's a bit of a crude solution, but i placed launchers on the desktop that run root terminal, "metacity --replace", "compiz --replace" and "unity", so i have at least some means of getting window borders, and in some cases ALT+F2 support.

the experimental 3d driver works :), but not very stable. it feels like the mouse goes to sleep. i have to nudge it first, and then it responds
also, while i did get my 3d unity running, compiz tends to crash. running "unity" gets it going again...

it doesn't like gnome-shell/mutter very much though. it only draws icons and menus, no windows...

---

### Post by Harry33 on 2011-02-03
> **BegbieThesec said:**
> Hm... Some updated were here, but still - when I want to install nvidia-current, it wants to remove a lot of xorg packages. I can have only nouveau driver, but with that, Unity won't load up, must use classic gnome.

I wonder will it be fixed (able to install nvidia-current) or should I reinstall my Natty when Alpha2 will be released (I guess it's the same as just updating, but who knows)?

Well as I said berofe (in my post no 60).
The reason is this:
nvidia-current_260.19.29 (which is latest one in Natty repos) provides a virtual package xserver-xorg-video-8.
Well, then, you have installed latest xserver 1.10 rc1 in Natty repos.
And the package xserver-xorg-core breaks the very same xserver-xorg-video-8.

So, by trying to install nvidia-current_260.19.29 you create an impossible situation and the xserver 1.10 is going to be uninstalled with all dependencies, to prevent broken packages.

Will this be fixed then?
Yes it will, but Canonical cannot do that.
This is because nvidia proprietary driver is not free source code.
Only Nvidia Co. can do that.
And I think new driver will be released when xserver 1.10 rc2 is released (we have rc1 now).

---

### Post by BegbieThesec on 2011-02-03
"nvidia proprietary driver is not free source code"

I think because of that I'm more than comfortable with nouveau driver... Just wondering if Unity will play nicely with them, or I will "have to" install nvidia-current. But I know - we will see.

It sucks that we must count only on nvidia guys on that, but that's how it is, and that's all. I wonder why nouveau drivers aren't on the "first" place, default etc, I didn't see them in earlier releases of Ubu... Well, but this is offtopic.

Again, Harry, thanks for reply.

---

### Post by Yougo on 2011-02-04
as nouveau is 2d, it will not run Unity, however *additional drivers* should also offer an experimental 3d driver. it's a bit shaky for me (but what can i say, it's trying to hold on in an alpha...) but it seems a good alternative for nvidia for now

on my 10.10 machine, i am running nvidia though. when i installed that, there really was nothing else, and i don't feel like breaking my work machine trying to switch...

i'll see how the 3d driver holds up, and what features it gives me on gaming, multiple screens/expanded desktop, switching modes on the fly (granted, that last one isnt so great on nvidia either...)

plugging in an external screen or beamer is still awkward compared to how the other OS just does that right, but that's a different story.

---

### Post by Quackers on 2011-02-04
The experimental 3D driver doesn't run unity for me :-(  It also seems to crash compiz too.

---

### Post by zika on 2011-02-04
Try unity-2d?
Disclaimer: I do not like it so I do not use it...

---

### Post by Quackers on 2011-02-04
> **zika said:**
> Try unity-2d?
Disclaimer: I do not like it so I do not use it...

I could do that, but I'll wait a while :-) 
I'm back using alpha1 install now :-(

---

### Post by MacUntu on 2011-02-04
Is there an ETA on working VBox acceleration? :(

---

### Post by brianafischer on 2011-02-04
For those who run nVidia cards, it seems there is a recent binary update that is compatible with the new X stack:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

I haven't had a chance to run these drivers yet, but they will install...

---

### Post by terry_gardener on 2011-02-04
> **brianafischer said:**
> For those who run nVidia cards, it seems there is a recent binary update that is compatible with the new X stack:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

I haven't had a chance to run these drivers yet, but they will install...

i have not tried those drivers but i dont think that there will work as 270.18 doesn't have 1.10 rc1 support.

this has already been mentioned on the forums (post #60 from harry)

---

### Post by Harry33 on 2011-02-04
> **terry_gardener said:**
> i have not tried those drivers but i dont think that there will work as 270.18 doesn't have 1.10 rc1 support.
this has already been mentioned on the forums (post #60 from harry)

Yes this is true.
We must wait until Nvidia Corporation releases binary drivers for xserver 1.10 rc2.
It is "estimated" to happen within a couple of weeks.

The nvidia-current_270.18 driver does have a preliminary (limited) support for xserver 1.10 rc1.
However, the xserver 1.10 series in Natty repos is not actually rc1.
It is rc1 + git 20110131. There is an ABI bumb between those two xserver versions.
So, once again nvidia 270.18 does not support Natty's xserver 1.10.

---

### Post by ratcheer on 2011-02-04
> **Harry33 said:**
> Yes this is true.
We must wait until Nvidia Corporation releases binary drivers for xserver 1.10 rc2.
It is "estimated" to happen within a couple of weeks.



I have basically gone out of the Natty business until the driver becomes available.

Tim

---

### Post by brianafischer on 2011-02-04
> **Harry33 said:**
> Yes this is true.
We must wait until Nvidia Corporation releases binary drivers for xserver 1.10 rc2.
It is "estimated" to happen within a couple of weeks.

The nvidia-current_270.18 driver does have a preliminary (limited) support for xserver 1.10 rc1.
However, the xserver 1.10 series in Natty repos is not actually rc1.
It is rc1 + git 20110131. There is an ABI bumb between those two xserver versions.
So, once again nvidia 270.18 does not support Natty's xserver 1.10.
Thanks for the clarification!

---

### Post by sgage on 2011-02-04
> **ratcheer said:**
> I have basically gone out of the Natty business until the driver becomes available.

Tim

Ditto.

---

### Post by jimmyave on 2011-02-04
Hey! Well that's why my X doesn't work anymore...

How can I get it fixed until a new NVIDIA driver is released?

Cheers!

---

### Post by brianafischer on 2011-02-04
> **jimmyave said:**
> Hey! Well that's why my X doesn't work anymore...

How can I get it fixed until a new NVIDIA driver is released?

Cheers!
I just ran the following from the kernel netroot recovery with a hardwired ethernet connection.

This is from memory, so please add to this if necessary.

```
sudo apt-get remove nvidia-common nvidia-settings
sudo apt-get install ubuntu-desktop
```

---

### Post by sirjasonr on 2011-02-05
> **jimmyave said:**
> Hey! Well that's why my X doesn't work anymore...

How can I get it fixed until a new NVIDIA driver is released?

Cheers!

I've just started using the nouveau drivers temporarily until things settle down. I removed all nvidia packages and proprietary drivers, moved my nvidia xorg.conf to a temporary location (so that there is no file named xorg.conf in /etc/X11/) prompting the default display config to kick in. Then, I changed all the desired settings (such as a dual-monitor configuration as is my case) using System -> Preferences -> Monitors in the Ubuntu Classic Desktop (no effects).

Once the turbulence subsides, I'll put all the packages back and move my old xorg.conf back as well. Things are working reasonably well considering the circumstances. My graphics card has a DVI and VGA output (which is how I'm running my dual monitor set up), and the VGA screen flickers a little bit. But all-in-all I'm not complaining.

---

### Post by jimmyave on 2011-02-05
Okey, thanks for the answers!

Still doesn't work doh... I guess I have to downgrade my xserver. Google it is!

---

### Post by rv65 on 2011-02-09
I have Natty with Nvidia 270.18 and would like to downgrade my Xorg server? I would appreciate if somebody posts the amd64 files as thats what my desktop runs.

---

### Post by Harry33 on 2011-02-09
> **rv65 said:**
> I have Natty with Nvidia 270.18 and would like to downgrade my Xorg server? I would appreciate if somebody posts the amd64 files as thats what my desktop runs.

So you want to downgrade xserver 1.10 rc1 to xserver 1.9.0?

You need to downgrade 2 xserver packages:
 - xserver-xorg (to version 7.5+6ubuntu8 )
 - xserver-xorg-core (to version 1.9.0-0ubuntu7)

Then you need to downgrade **all** input and video drivers you have installed.
For example evdev (for mouse and kb) and vesa (for failsafe X).
 - xserver-xorg-input-evdev (to version 2.6.0-1ubuntu4)
 - xserver-xorg-video-vesa (to version 2.3.0-4)

Note, that these you do **not** have to downgrade: x11-common, xorg, xserver-common.

---

### Post by lucazade on 2011-02-09
> **Harry33 said:**
> So you want to downgrade xserver 1.10 rc1 to xserver 1.9.0?

You need to downgrade 2 xserver packages:
 - xserver-xorg (to version 7.5+6ubuntu8 )
 - xserver-xorg-core (to version 1.9.0-0ubuntu7)

Then you need to downgrade **all** input and video drivers you have installed.
For example evdev (for mouse and kb) and vesa (for failsafe X).
 - xserver-xorg-input-evdev (to version 2.6.0-1ubuntu4)
 - xserver-xorg-video-vesa (to version 2.3.0-4)

Note, that these you do **not** have to downgrade: x11-common, xorg, xserver-common.

```

#!/bin/bash
sudo apt-get purge xserver-xorg-video-nouveau xserver-xorg-video-intel xserver-xorg-video-all xserver-xorg-input-all

mkdir xorg19
cd xorg19

wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_i386.deb
#wget -c http://ppa.launchpad.net/xorg-edgers/wayland/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.12.0-1ubuntu6~bryce2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.3.2-6ubuntu3.1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.5+6ubuntu3_i386.deb
#wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.5+6ubuntu3_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.5.0-2build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.2.2-2ubuntu5_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.6.9-2build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xf86-input-wacom/xserver-xorg-input-wacom_0.10.8-0ubuntu1_i386.deb
#wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.5+6ubuntu3_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-apm/xserver-xorg-video-apm_1.2.3-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ark/xserver-xorg-video-ark_0.7.2-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.13.1-1ubuntu5_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-chips/xserver-xorg-video-chips_1.2.3-1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-cirrus/xserver-xorg-video-cirrus_1.3.2-2ubuntu3_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-fbdev/xserver-xorg-video-fbdev_0.4.2-2ubuntu2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.11.9-5_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i128/xserver-xorg-video-i128_1.3.3-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i740/xserver-xorg-video-i740_1.3.2-2build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.8.2-3build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mga/xserver-xorg-video-mga_1.4.11.dfsg-4build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-neomagic/xserver-xorg-video-neomagic_1.2.4-3build2_i386.deb
#wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_0.0.16+git20100805+b96170a-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nv/xserver-xorg-video-nv_2.1.17-3ubuntu3_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.904+svn842-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-r128/xserver-xorg-video-r128_6.8.1-3build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.13.1-1ubuntu5_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-rendition/xserver-xorg-video-rendition_4.2.4-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.3-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3virge/xserver-xorg-video-s3virge_1.10.4-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-savage/xserver-xorg-video-savage_2.3.1-2ubuntu2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-siliconmotion/xserver-xorg-video-siliconmotion_1.7.4-0ubuntu2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.3-1build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sisusb/xserver-xorg-video-sisusb_0.9.4-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.4.3-2build2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.3.4-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tseng/xserver-xorg-video-tseng_1.2.4-0ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.3.0-3build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vmware/xserver-xorg-video-vmware_11.0.1-2build1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.2.4-0ubuntu1_i386.deb

sudo dpkg -i *.deb

```

---

### Post by Harry33 on 2011-02-09
> **lucazade said:**
> ```

#!/bin/bash
sudo apt-get purge xserver-xorg-video-nouveau xserver-xorg-video-intel xserver-xorg-video-all xserver-xorg-input-all

mkdir xorg19
cd xorg19

wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_i386.deb
...
...
sudo dpkg -i *.deb

```

He wanted AMD64 architecture packages.

---

### Post by lucazade on 2011-02-09
> **Harry33 said:**
> He wanted AMD64 architecture packages.

ops.. mea culpa
search and replace "i386" with "amd64"

this was a script i've used for my binary blobs!

---

### Post by brianafischer on 2011-02-09
Thanks for the script.  My nvidia driver is now working well.  Any advice on how to block the xserver updates until a compatible nvidia drivers is working?

I currently use
> sudo aptitude update && sudo aptitude safe-upgrade

but this still prompts to update xserver.

---

### Post by lucazade on 2011-02-09
> **brianafischer said:**
> Thanks for the script.  My nvidia driver is now working well.  Any advice on how to block the xserver updates until a compatible nvidia drivers is working?

I currently use


but this still prompts to update xserver.

open synaptic and lock all the packages by hand :)

something like:
echo 'xserver-xorg-core...' | sudo dpkg --set-selections
should help doing this from terminal.. but haven't tested

---

### Post by praveenthivari on 2011-02-09
How to downgrade packages from tty1 because the defalt nouveau drivers dont seem to like my graphic card and create destorted desktop. I cant do anything from tht desktop.:mad:

---

### Post by Harry33 on 2011-02-09
> **praveenthivari said:**
> How to downgrade packages from tty1 because the defalt nouveau drivers dont seem to like my graphic card and create destorted desktop. I cant do anything from tht desktop.:mad:

You only have to download all necessary packages into any partition that is mounted on boot.
Then boot into recovery mode (press and hold down "shift" before grub loads).
Wait till you see screen asking what to do, select "Drop to shell with net".
Then go to the directory where the downloaded files are.
Then do this (all files at the same time, otherwise packages will break):
```
dpkg -i package1.deb package2deb ...
```
Then:
```
reboot
```

---

### Post by praveenthivari on 2011-02-09
Thanks.Will try tht now.

---

### Post by brianafischer on 2011-02-09
The following modified shell script from lucazade works great.  I have updated it for a 64-bit system and added a hold to the xorg packages so they do not appear in apt updates.

> #!/bin/bash
sudo apt-get purge xserver-xorg-video-nouveau xserver-xorg-video-intel xserver-xorg-video-all xserver-xorg-input-all

mkdir xorg19
cd xorg19

wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_amd64.deb)
#wget -c [http://ppa.launchpad.net/xorg-edgers/wayland/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.12.0-1ubuntu6~bryce2_amd64.deb](http://ppa.launchpad.net/xorg-edgers/wayland/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.12.0-1ubuntu6~bryce2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.3.2-6ubuntu3.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.3.2-6ubuntu3.1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.5+6ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.5+6ubuntu3_amd64.deb)
#wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.5+6ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.5+6ubuntu3_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.5.0-2build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.5.0-2build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.2.2-2ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.2.2-2ubuntu5_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.6.9-2build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.6.9-2build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xf86-input-wacom/xserver-xorg-input-wacom_0.10.8-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xf86-input-wacom/xserver-xorg-input-wacom_0.10.8-0ubuntu1_amd64.deb)
#wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.5+6ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.5+6ubuntu3_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-apm/xserver-xorg-video-apm_1.2.3-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-apm/xserver-xorg-video-apm_1.2.3-0ubuntu1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ark/xserver-xorg-video-ark_0.7.2-2build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ark/xserver-xorg-video-ark_0.7.2-2build2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.13.1-1ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.13.1-1ubuntu5_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-chips/xserver-xorg-video-chips_1.2.3-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-chips/xserver-xorg-video-chips_1.2.3-1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-cirrus/xserver-xorg-video-cirrus_1.3.2-2ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-cirrus/xserver-xorg-video-cirrus_1.3.2-2ubuntu3_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-fbdev/xserver-xorg-video-fbdev_0.4.2-2ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-fbdev/xserver-xorg-video-fbdev_0.4.2-2ubuntu2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.11.9-5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.11.9-5_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i128/xserver-xorg-video-i128_1.3.3-2build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i128/xserver-xorg-video-i128_1.3.3-2build2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i740/xserver-xorg-video-i740_1.3.2-2build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i740/xserver-xorg-video-i740_1.3.2-2build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.8.2-3build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.8.2-3build2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mga/xserver-xorg-video-mga_1.4.11.dfsg-4build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mga/xserver-xorg-video-mga_1.4.11.dfsg-4build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-neomagic/xserver-xorg-video-neomagic_1.2.4-3build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-neomagic/xserver-xorg-video-neomagic_1.2.4-3build2_amd64.deb)
#wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_0.0.16+git20100805+b96170a-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_0.0.16+git20100805+b96170a-0ubuntu1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nv/xserver-xorg-video-nv_2.1.17-3ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nv/xserver-xorg-video-nv_2.1.17-3ubuntu3_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.904+svn842-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.904+svn842-0ubuntu1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-r128/xserver-xorg-video-r128_6.8.1-3build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-r128/xserver-xorg-video-r128_6.8.1-3build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.13.1-1ubuntu5_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.13.1-1ubuntu5_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-rendition/xserver-xorg-video-rendition_4.2.4-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-rendition/xserver-xorg-video-rendition_4.2.4-0ubuntu1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.3-2build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.3-2build2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3virge/xserver-xorg-video-s3virge_1.10.4-2build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3virge/xserver-xorg-video-s3virge_1.10.4-2build2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-savage/xserver-xorg-video-savage_2.3.1-2ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-savage/xserver-xorg-video-savage_2.3.1-2ubuntu2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-siliconmotion/xserver-xorg-video-siliconmotion_1.7.4-0ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-siliconmotion/xserver-xorg-video-siliconmotion_1.7.4-0ubuntu2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.3-1build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.3-1build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sisusb/xserver-xorg-video-sisusb_0.9.4-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sisusb/xserver-xorg-video-sisusb_0.9.4-0ubuntu1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.4.3-2build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.4.3-2build2_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.3.4-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.3.4-0ubuntu1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tseng/xserver-xorg-video-tseng_1.2.4-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tseng/xserver-xorg-video-tseng_1.2.4-0ubuntu1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.3.0-3build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.3.0-3build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vmware/xserver-xorg-video-vmware_11.0.1-2build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vmware/xserver-xorg-video-vmware_11.0.1-2build1_amd64.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.2.4-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.2.4-0ubuntu1_amd64.deb)

sudo dpkg -i *.deb

echo xserver-common hold | dpkg --set-selections
echo xserver-xorg-core hold | dpkg --set-selections
#echo xserver-xorg-video-intel hold | dpkg --set-selections
echo xserver-xorg-input-evdev hold | dpkg --set-selections
echo xserver-xorg hold | dpkg --set-selections
#echo xserver-xorg-input-all hold | dpkg --set-selections
echo xserver-xorg-input-mouse hold | dpkg --set-selections
echo xserver-xorg-input-synaptics hold | dpkg --set-selections
echo xserver-xorg-input-vmmouse hold | dpkg --set-selections
echo xserver-xorg-input-wacom hold | dpkg --set-selections
#echo xserver-xorg-video-all hold | dpkg --set-selections
echo xserver-xorg-video-apm hold | dpkg --set-selections
echo xserver-xorg-video-ark hold | dpkg --set-selections
echo xserver-xorg-video-ati hold | dpkg --set-selections
echo xserver-xorg-video-chips hold | dpkg --set-selections
echo xserver-xorg-video-cirrus hold | dpkg --set-selections
echo xserver-xorg-video-fbdev hold | dpkg --set-selections
echo xserver-xorg-video-geode hold | dpkg --set-selections
echo xserver-xorg-video-i128 hold | dpkg --set-selections
echo xserver-xorg-video-i740 hold | dpkg --set-selections
echo xserver-xorg-video-mach64 hold | dpkg --set-selections
echo xserver-xorg-video-mga hold | dpkg --set-selections
echo xserver-xorg-video-neomagic hold | dpkg --set-selections
#echo xserver-xorg-video-nouveau hold | dpkg --set-selections
echo xserver-xorg-video-nv hold | dpkg --set-selections
echo xserver-xorg-video-openchrome hold | dpkg --set-selections
echo xserver-xorg-video-r128 hold | dpkg --set-selections
echo xserver-xorg-video-radeon hold | dpkg --set-selections
echo xserver-xorg-video-rendition hold | dpkg --set-selections
echo xserver-xorg-video-s3 hold | dpkg --set-selections
echo xserver-xorg-video-s3virge hold | dpkg --set-selections
echo xserver-xorg-video-savage hold | dpkg --set-selections
echo xserver-xorg-video-siliconmotion hold | dpkg --set-selections
echo xserver-xorg-video-sis hold | dpkg --set-selections
echo xserver-xorg-video-sisusb hold | dpkg --set-selections
echo xserver-xorg-video-tdfx hold | dpkg --set-selections
echo xserver-xorg-video-trident hold | dpkg --set-selections
echo xserver-xorg-video-tseng hold | dpkg --set-selections
echo xserver-xorg-video-vesa hold | dpkg --set-selections
echo xserver-xorg-video-vmware hold | dpkg --set-selections
echo xserver-xorg-video-voodoo hold | dpkg --set-selections

---

### Post by BegbieThesec on 2011-02-10
Weird.. I've downgraded those packages, installed nvidia-current, but all I can get is classic desktop without effects.. So it's like I don't have drivers installed, but I do.. stupid Nvidia.

Edit: had to run nvidia-xconfig. I Have Unity back. :)

---

### Post by David Tomic on 2011-02-10
> **brianafischer said:**
> The following modified shell script from lucazade works great.  I have updated it for a 64-bit system and added a hold to the xorg packages so they do not appear in apt updates.

You need to post it using CODE tags, rather than QUOTE.  Otherwise your links get truncated and it doesn't work.

---

### Post by durand on 2011-02-11
> **David Tomic said:**
> You need to post it using CODE tags, rather than QUOTE.  Otherwise your links get truncated and it doesn't work.

```

#!/bin/bash
sudo apt-get purge xserver-xorg-video-nouveau xserver-xorg-video-intel xserver-xorg-video-all xserver-xorg-input-all

mkdir xorg19
cd xorg19

wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.9.0-0ubuntu7.3_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.9.0-0ubuntu7.3_amd64.deb
#wget -c http://ppa.launchpad.net/xorg-edgers/wayland/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.12.0-1ubuntu6~bryce2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.3.2-6ubuntu3.1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.5+6ubuntu3_amd64.deb
#wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.5+6ubuntu3_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse/xserver-xorg-input-mouse_1.5.0-2build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.2.2-2ubuntu5_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.6.9-2build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xf86-input-wacom/xserver-xorg-input-wacom_0.10.8-0ubuntu1_amd64.deb
#wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.5+6ubuntu3_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-apm/xserver-xorg-video-apm_1.2.3-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ark/xserver-xorg-video-ark_0.7.2-2build2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.13.1-1ubuntu5_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-chips/xserver-xorg-video-chips_1.2.3-1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-cirrus/xserver-xorg-video-cirrus_1.3.2-2ubuntu3_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-fbdev/xserver-xorg-video-fbdev_0.4.2-2ubuntu2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-geode/xserver-xorg-video-geode_2.11.9-5_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i128/xserver-xorg-video-i128_1.3.3-2build2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-i740/xserver-xorg-video-i740_1.3.2-2build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mach64/xserver-xorg-video-mach64_6.8.2-3build2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mga/xserver-xorg-video-mga_1.4.11.dfsg-4build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-neomagic/xserver-xorg-video-neomagic_1.2.4-3build2_amd64.deb
#wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nouveau/xserver-xorg-video-nouveau_0.0.16+git20100805+b96170a-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nv/xserver-xorg-video-nv_2.1.17-3ubuntu3_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome/xserver-xorg-video-openchrome_0.2.904+svn842-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-r128/xserver-xorg-video-r128_6.8.1-3build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-radeon_6.13.1-1ubuntu5_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-rendition/xserver-xorg-video-rendition_4.2.4-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.3-2build2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-s3virge/xserver-xorg-video-s3virge_1.10.4-2build2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-savage/xserver-xorg-video-savage_2.3.1-2ubuntu2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-siliconmotion/xserver-xorg-video-siliconmotion_1.7.4-0ubuntu2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sis/xserver-xorg-video-sis_0.10.3-1build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sisusb/xserver-xorg-video-sisusb_0.9.4-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tdfx/xserver-xorg-video-tdfx_1.4.3-2build2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-trident/xserver-xorg-video-trident_1.3.4-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tseng/xserver-xorg-video-tseng_1.2.4-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.3.0-3build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vmware/xserver-xorg-video-vmware_11.0.1-2build1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-voodoo/xserver-xorg-video-voodoo_1.2.4-0ubuntu1_amd64.deb

sudo dpkg -i *.deb

echo xserver-common hold | dpkg --set-selections
echo xserver-xorg-core hold | dpkg --set-selections
#echo xserver-xorg-video-intel hold | dpkg --set-selections
echo xserver-xorg-input-evdev hold | dpkg --set-selections
echo xserver-xorg hold | dpkg --set-selections
#echo xserver-xorg-input-all hold | dpkg --set-selections
echo xserver-xorg-input-mouse hold | dpkg --set-selections
echo xserver-xorg-input-synaptics hold | dpkg --set-selections
echo xserver-xorg-input-vmmouse hold | dpkg --set-selections
echo xserver-xorg-input-wacom hold | dpkg --set-selections
#echo xserver-xorg-video-all hold | dpkg --set-selections
echo xserver-xorg-video-apm hold | dpkg --set-selections
echo xserver-xorg-video-ark hold | dpkg --set-selections
echo xserver-xorg-video-ati hold | dpkg --set-selections
echo xserver-xorg-video-chips hold | dpkg --set-selections
echo xserver-xorg-video-cirrus hold | dpkg --set-selections
echo xserver-xorg-video-fbdev hold | dpkg --set-selections
echo xserver-xorg-video-geode hold | dpkg --set-selections
echo xserver-xorg-video-i128 hold | dpkg --set-selections
echo xserver-xorg-video-i740 hold | dpkg --set-selections
echo xserver-xorg-video-mach64 hold | dpkg --set-selections
echo xserver-xorg-video-mga hold | dpkg --set-selections
echo xserver-xorg-video-neomagic hold | dpkg --set-selections
#echo xserver-xorg-video-nouveau hold | dpkg --set-selections
echo xserver-xorg-video-nv hold | dpkg --set-selections
echo xserver-xorg-video-openchrome hold | dpkg --set-selections
echo xserver-xorg-video-r128 hold | dpkg --set-selections
echo xserver-xorg-video-radeon hold | dpkg --set-selections
echo xserver-xorg-video-rendition hold | dpkg --set-selections
echo xserver-xorg-video-s3 hold | dpkg --set-selections
echo xserver-xorg-video-s3virge hold | dpkg --set-selections
echo xserver-xorg-video-savage hold | dpkg --set-selections
echo xserver-xorg-video-siliconmotion hold | dpkg --set-selections
echo xserver-xorg-video-sis hold | dpkg --set-selections
echo xserver-xorg-video-sisusb hold | dpkg --set-selections
echo xserver-xorg-video-tdfx hold | dpkg --set-selections
echo xserver-xorg-video-trident hold | dpkg --set-selections
echo xserver-xorg-video-tseng hold | dpkg --set-selections
echo xserver-xorg-video-vesa hold | dpkg --set-selections
echo xserver-xorg-video-vmware hold | dpkg --set-selections
echo xserver-xorg-video-voodoo hold | dpkg --set-selections

```

I also had to run ```

sudo nvidia-xconfig
sudo cp /etc/X11/XF86Config /etc/X11/xorg.conf

```

Not sure why nvidia thought I was using XF86 rather than Xorg.

---

### Post by zika on 2011-02-11
> **David Tomic said:**
> You need to post it using CODE tags, rather than QUOTE.  Otherwise your links get truncated and it doesn't work.With &#8222;quote&#8220; there is possibility to DL directly from the frame... All URL's were OK... There is no perfect solution... Just hover on each of them (watching status line) and You'll see why I do prefer &#8222;quote&#8220;...

---

### Post by David Tomic on 2011-02-11
> **zika said:**
> With „quote“ there is possibility to DL directly from the frame... All URL's were OK... 

Sure ... but there's 50+ links there [probably, I didn't actually bother to count them].

Why would anyone bother having to process every single one of them manually, when they could just copy/paste the whole lot in one go from a code box?

Anyway ... I got excited because I saw a whole bunch of Xorg packages in this mornings updates, and I thought this might have [finally] been resolved.  Alas, still not quite there yet by the looks of things ...

---

### Post by Harry33 on 2011-02-12
> **David Tomic said:**
> Sure ... but there's 50+ links there [probably, I didn't actually bother to count them].

Why would anyone bother having to process every single one of them manually, when they could just copy/paste the whole lot in one go from a code box?

Anyway ... I got excited because I saw a whole bunch of Xorg packages in this mornings updates, and I thought this might have [finally] been resolved.  Alas, still not quite there yet by the looks of things ...

Why would any expert bother to install all those video drivers.
With Nvidia you do not need any one of them, only proprietary nvidia-current,
with ATI all you need is ati and radeon,
with intel, most need only intel driver.
If one needs failsafe X, then also vesa is needed.

---

### Post by frafu on 2011-02-12
Thanks for the script for downgrading X to 1.9.     :-)

---

### Post by abeowitz on 2011-02-13
Thanks for the script, successfully downgraded Xorg and got nvidia-current working.

HOWEVER, my gnome theme is messed up. - UBUNTU CLASSIC DESKTOP - I've got desktop click sounds when I've disabled sound, and the gtk buttons and panel don't take on new themes.

I suspect a desktop related package was removed.  But /var/log/apt doesn't seem to hint at what it may have been...

Any ideas?

Edit:  Metacity will take on the new theme, but gtk/gnome widgets/buttons won't. 

Upon login the themes seemed to try to setup, but quickly switched back to default/ugly gtk button theme.

Sounds play on check boxes, dialog windows, etc.  Even though I've sound disabled in the config.

Edit 2:  Unity/netbook desktop seems OK, themes hold OK.  I like classic desktop better.  :/

Edit 3:  [http://ubuntuforums.org/showthread.php?t=1669783&highlight=themes+broken](http://ubuntuforums.org/showthread.php?t=1669783&highlight=themes+broken)  did not help.  :(

---

### Post by Harry33 on 2011-02-13
> **abeowitz said:**
> Thanks for the script, successfully downgraded Xorg and got nvidia-current working.

HOWEVER, my gnome theme is messed up. - UBUNTU CLASSIC DESKTOP - I've got desktop click sounds when I've disabled sound, and the gtk buttons and panel don't take on new themes.

I suspect a desktop related package was removed.  But /var/log/apt doesn't seem to hint at what it may have been...

Any ideas?

Edit:  Metacity will take on the new theme, but gtk/gnome widgets/buttons won't. 

Upon login the themes seemed to try to setup, but quickly switched back to default/ugly gtk button theme.

Sounds play on check boxes, dialog windows, etc.  Even though I've sound disabled in the config.

Edit 2:  Unity/netbook desktop seems OK, themes hold OK.  I like classic desktop better.  :/

Edit 3:  [http://ubuntuforums.org/showthread.php?t=1669783&highlight=themes+broken](http://ubuntuforums.org/showthread.php?t=1669783&highlight=themes+broken)  did not help.  :(

Se if this is your problems:
[http://ubuntuforums.org/showthread.php?t=1675969](http://ubuntuforums.org/showthread.php?t=1675969)

First, go check your ".xsession-errors" file in your home folder.
If you find the same error message,
go edit your "/etc/xdg/autostart/gnome-settings-daemon" file.

There is a bug report about this:
Bug #649809

---

### Post by abeowitz on 2011-02-13
Thanks Harry,

Didn't apply to my Natty setup.  BUT it did fix my Maverick install.. :)



> **Harry33 said:**
> Se if this is your problems:
[http://ubuntuforums.org/showthread.php?t=1675969](http://ubuntuforums.org/showthread.php?t=1675969)

First, go check your ".xsession-errors" file in your home folder.
If you find the same error message,
go edit your "/etc/xdg/autostart/gnome-settings-daemon" file.

There is a bug report about this:
Bug #649809

---

### Post by farooq23 on 2011-02-14
Any Idea when will nvidia release xserver 1.10 compatible drivers ??

---

### Post by portis on 2011-02-14
It depends on when the ABI of xserver 1.10 is stablized.

> **farooq23 said:**
> Any Idea when will nvidia release xserver 1.10 compatible drivers ??

---

### Post by MacUntu on 2011-02-14
Which is planned for Xserver 1.10 RC2, AFAIK. Not yet released, so probably a solution to this mess is still a few weeks away.

Seriously, now is a good time to try Nouveau (and its still experimental 3D acceleration support)! ;)

---

### Post by VMC on 2011-02-14
> **MacUntu said:**
> Which is planned for Xserver 1.10 RC2, AFAIK. Not yet released, so probably a solution to this mess is still a few weeks away.

Seriously, now is a good time to try Nouveau (and its still experimental 3D acceleration support)! ;)

I would use Nouveau, but since I do a fresh install almost daily using the latest daily-live, I have to download Nouveau each time and 40+ megs takes some time using my connection.

With nvidia proprietary, I have it always at hand. No need to always download the same file.

I tried to copy from apps the Nouveau, but could never install. I know about Apttocd, but thats a bit awkward.

---

### Post by mc4man on 2011-02-14
> I would use Nouveau..
Atm am using nouveau  on 2 diff. machines - 1 with the 3d drivers and unity, the other just nouveau and gnome-panel.
While it works ok in both cases it's not without some issues, to some extent probably hardware dependent and display type.

On both machines the 3d drivers are a clear improvement but do increase the heat levels a bit, on my desktop that doesn't matter, on a laptop it is a concern so removed them.

Also, at least here, nouveau does have video tearing beyond any seen with nvidia, the 3d drivers tend increase it, though in terms of actual video playback the player used is also a factor.

Depending on ones use and hardware nouveau or nouveau 3d could be fine or be totally unacceptable, personally don't see nouveau as ever being able to keep up with nvidia unless nvidia decided to provide some 'assistance'

---

### Post by MacUntu on 2011-02-14
> **VMC said:**
> I would use Nouveau, but since I do a fresh install almost daily using the latest daily-live, I have to download Nouveau each time and 40+ megs takes some time using my connection.

:?:

Nouveau is the standard driver when you do a fresh install. No need to download anything (besides libgl1-mesa-dri-experimental for 3D acceleration - and that's 917 kB).

---

### Post by gnomeuser on 2011-02-14
Nouveau's experimental 3d support no longer runs unity for me.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/718991](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/718991)

Aside that the transition has been smooth, being unsupported that is understandably acceptable, never the less it sucks for me since that means no unity.

I'd known about this from the xorg-edgers ppa for a while but forgot to file it.

---

### Post by mc4man on 2011-02-14
> Nouveau's experimental 3d support no longer runs unity for me.
There is something in progress there
[https://bugs.launchpad.net/nouveau/+bug/710588](https://bugs.launchpad.net/nouveau/+bug/710588)

(todays 64 bit iso was a complete disaster w/ nouveau (2d or 3d
basically booted to a desktop w/ nothing available but a terminal (Classic
Removing the bailer plugin allowed a restart to gnome-panel, but used the old style 'fallback' icons, both for login and on the desktop

---

### Post by gnomeuser on 2011-02-14
> **mc4man said:**
> There is something in progress there
[https://bugs.launchpad.net/nouveau/+bug/710588](https://bugs.launchpad.net/nouveau/+bug/710588)

(todays 64 bit iso was a complete disaster w/ nouveau (2d or 3d
basically booted to a desktop w/ nothing available but a terminal (Classic
Removing the bailer plugin allowed a restart to gnome-panel, but used the old style 'fallback' icons, both for login and on the desktop

Thank you, that sounds very likely, marked as duplicate.

---

### Post by ratcheer on 2011-02-14
> **MacUntu said:**
> Which is planned for Xserver 1.10 RC2, AFAIK. Not yet released, so probably a solution to this mess is still a few weeks away.


No news is bad news.

Tim

---

### Post by farooq23 on 2011-02-15
> **gnomeuser said:**
> Nouveau's experimental 3d support no longer runs unity for me.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/718991](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/718991)

Aside that the transition has been smooth, being unsupported that is understandably acceptable, never the less it sucks for me since that means no unity.

I'd known about this from the xorg-edgers ppa for a while but forgot to file it.

Same here, 3d nouveau drivers no longer runs unity for me too. I am using Geforce 210 graphics card. Any solution to this issue ?

Regards,
farooq23

---

### Post by mc4man on 2011-02-15
> **gnomeuser said:**
> Thank you, that sounds very likely, marked as duplicate.

have tried a commit to mesa and at least on a 8600m - pci-e, nouveau 3d is working again in the  unity login. I'd expect an updated package in near future baring any difficulties (is working fine here atm

---

### Post by cariboo on 2011-02-15
I just installed nouveau firmware, which solved my video corruption problems. According to the blurb in synaptic, it won't be needed for much longer, but for now it solved my minimal video corruption problems.

---

### Post by david stevenson on 2011-02-17
Well I tried 
sudo apt-get install libgl1-mesa-dri-experimental
unity --replace &
AND IT WORKS
well I am running unity 3D on an GeForce Go 7600 and X.Org X Server 1.9.99.901 (1.10.0 RC 1) now time to play a bit....

---

### Post by VMC on 2011-02-17
> **cariboo907 said:**
> I just installed nouveau firmware, which solved my video corruption problems. According to the blurb in synaptic, it won't be needed for much longer, but for now it solved my minimal video corruption problems.

I'm in Lucid right now, but is this the guy:

$ apt-cache showpkg nouveau-firmware
Package: nouveau-firmware
Versions: 
20091212-0ubuntu1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-amd64_Packages
                  MD5: 0422b15056d913dbcb543511da67cbae


Reverse Depends: 
Dependencies: 
20091212-0ubuntu1 - 
Provides: 
20091212-0ubuntu1 - 
Reverse Provides: 

Then I guess its just ***apt-get install nouveau-firmware***

I'm a bit perplexed how or why this doesn't get installed with jockey?!

---

### Post by cariboo on 2011-02-17
The blurb in synaptic said nouveau-firmware won't be needed for much longer, but I thought it wouldn't hurt to try it. Installing it did solve my initial video corruption problem when Unity first starts up. My background looked like it was tiled.

---

### Post by Harry33 on 2011-02-18
> **cariboo907 said:**
> The blurb in synaptic said nouveau-firmware won't be needed for much longer, but I thought it wouldn't hurt to try it. Installing it did solve my initial video corruption problem when Unity first starts up. My background looked like it was tiled.

Launchpad say this too:

```
Although the nouveau drivers are now able to generate this firmware for
 nv40 generation cards this package still contains the nvidia context programs
 for debugging purposes.
```

Here:
[https://launchpad.net/ubuntu/natty/amd64/nouveau-firmware/20091212-0ubuntu1](https://launchpad.net/ubuntu/natty/amd64/nouveau-firmware/20091212-0ubuntu1)

---

### Post by VinDSL on 2011-02-18
Kinda late to the party...

The first 11.04 builds wouldn't fit on a (normal) CD, and I figured that was a bad omen.

I installed Natty last night (from a Live CD) and played around for a few hours.  Then I crashed it before going to bed.  

I *guess* the 100+ updates did the deed. And, I didn't even get a kiss! :)

I did a fresh install, this afternoon, using the experimental nVidia drivers.

Here's the result...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-unity-desktop-18-feb-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-unity-desktop-18-feb-2011.png")[/INDENT]


Now that I've got a good start, which xorg files (specifically) should I pin?

The recommendations I've found are all over the place, and I'm NOT doing another update until I've got things locked down.

Thanks!

---

### Post by miegiel on 2011-02-18
> **VinDSL said:**
> Kinda late to the party...

The first 11.04 builds wouldn't fit on a (normal) CD, and I figured that was a bad omen.

I installed Natty last night (from a Live CD) and played around for a few hours.  Then I crashed it before going to bed.  

I *guess* the 100+ updates did the deed. And, I didn't even get a kiss! :)

I did a fresh install, this afternoon, using the experimental nVidia drivers.

Here's the result...


...


Now that I've got a good start, which xorg files (specifically) should I pin?

The recommendations I've found are all over the place, and I'm NOT doing another update until I've got things locked down.

Thanks!

Meh ... I should have gone off topic in [the (new) conky thread]("http://ubuntuforums.org/showthread.php?t=1681304") and warn you about natty and nvidia. ](*,)

---

### Post by cecilpierce on 2011-02-18
VinDSL

What is the info panel on the right called ? I would like to try it out, thanks. :confused:

---

### Post by cariboo on 2011-02-18
> **cecilpierce said:**
> VinDSL

What is the info panel on the right called ? I would like to try it out, thanks. :confused:

It's called conky, miegiel has a link in his post to the temporary conky thread, and there is a huge thread in the Cafe:


[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

Note: we've put off opening the Cafe for a week, as Canonical is buying us another database server as the old one failed at load balancing.

---

### Post by VinDSL on 2011-02-18
> **miegiel said:**
> Meh ... I should have gone off topic in [the (new) conky thread]("http://ubuntuforums.org/showthread.php?t=1681304") and warn you about natty and nvidia. ](*,)
Heh!  Thanks, miegiel!

I've been splitting my HDD into two equal pieces lately -- with an Ubu dev release on one half, and the latest stable release on the other, sooo no warning necessary!  ;)

A priori knowledge told me the update(s) would leave me stalled at Plymouth, and it did.

I want to proceed with the update(s), but I don't want to install Conky / conkyForecast over n' over again. :)

Should I simply pin everything that has anything to do with xorg?

I recall someone 'saying' (a few posts back) that locking everything-x was overkill.

My system rig is in the sig below (32-bit)...

---

### Post by miegiel on 2011-02-18
> **VinDSL said:**
> Heh!  Thanks, miegiel!

I've been splitting my HDD into two equal pieces lately -- with an Ubu dev release on one half, and the latest stable release on the other, sooo no warning necessary!  ;)

A priori knowledge told me the update(s) would leave me stalled at Plymouth, and it did.

I want to proceed with the update(s), but I don't want to install Conky / conkyForecast over n' over again. :)

Should I simply pin everything that has anything to do with xorg?

I recall someone 'saying' (a few posts back) that locking everything-x was overkill.

My system rig is in the sig below (32-bit)...

I think bocking all X related updates is overkill too. I don't have nvidia (intel here). I had a problem with evdev, but that's [fixed]("http://ubuntuforums.org/showthread.php?p=10412233#post10412233") now. From what I understood, with nvidia, you just need to avoid the propriety drivers and just use the open source (experimental 3D) ones.

---

### Post by Quackers on 2011-02-19
I am holding all xserver/xorg upgrades on one install (nvidia) for the moment. It may be overkill, but at least I don't have to pick up the pieces again :wink:
My other install is on the 3D experimental drivers, and is fully updated.

---

### Post by VinDSL on 2011-02-19
> **miegiel said:**
> From what I understood, with nvidia, you just need to avoid the propriety drivers and just use the open source (experimental 3D) ones.
> **Quackers said:**
> I am holding all xserver/xorg upgrades on one install (nvidia) for the moment. It may be overkill, but at least I don't have to pick up the pieces again :wink:

My other install is on the 3D experimental drivers, and is fully updated.
Interesting!  Thanks for the quick replies!

I was using nVidia 'current' drivers, last night, when the curtain came down.

Now, I'm using the 'experimental 3D' drivers, and they're working okay.  I get some screen flashing, from time-to-time, but it's livable.  

I *think* it's Compiz that's fragging the display.  Compiz crashes every couple of hours, but successfully reloads when I click the button in the dialog box.  ;)

I was looking at the 100+ updates that are being held back.

Besides the xserver/xorg updates, there are several GTK+ and Mesa updates.

Are the GTK+ and Mesa updates kosher?!?!?

If so, I think I'll play it safe, pin the xserver/xorg updates (for now) and update everything else.

---

### Post by Quackers on 2011-02-19
In my install which uses the experimental 3D drivers I have no updates pending, or held back. They all went fine. In my install which uses nvidia-current I have held all xorg/xserver updates until the problems are resolved.

---

### Post by mc4man on 2011-02-19
> If so, I think I'll play it safe, pin the xserver/xorg updates (for now) and update everything else.
It's probably best atm w/ nvidia and the nouveau 3d drivers to update all. should be fairly stable.
(the desktop I'm on now is fairly similar to your sig'ed hardware, an old gamimg p4, things are running quite well atm.

Currently w/ a 24" lcd using autohide, panel opacity at 0.0000, hide animation of fade only (launcher 'lock' is far upper corner w/ the mouse cursor

---

### Post by cecilpierce on 2011-02-19
[QUOTE=cariboo907;10472293]It's called conky, miegiel has a link in his post to the temporary conky thread, and there is a huge thread in the Cafe:


Thanks a lot cariboo907 :)

---

### Post by VinDSL on 2011-02-19
> **Quackers said:**
> In my install which uses the experimental 3D drivers I have no updates pending, or held back. They all went fine.

> **mc4man said:**
> It's probably best atm w/ nvidia and the nouveau 3d drivers to update all. should be fairly stable.
Sounds good!

OK, I'll backup my scripts to the 10.10 partition, and do a full update.

I spent 15 minutes, today, reinstalling Natty and 15 hours tweaking Conky...  LoL!  :D

Thanks again!

---

### Post by VinDSL on 2011-02-19
> **cecilpierce said:**
> VinDSL

What is the info panel on the right called ? I would like to try it out, thanks. :confused:Oops!  Missed your post, the first time around, cecilpierce.

As Jim said, it's:

[LIST]
[*]conky-all 1.8.0
[*]conkyForecast 2.16
[*]a lua background shading script
[*]and a lua LED bargraph script
[/LIST]

Beware, Conky (et al.) is very addictive!

It's not unusual for Conkystadors to wake up, in the middle of the night, and tweak their code, because they thought of some regex in their sleep.  LoL!

BTW, I'll be publishing it in a couple of days, here in the Ubu Forums.

I'm still playing around with the Banshee section...

---

### Post by lucazade on 2011-02-19
> **mc4man said:**
> It's probably best atm w/ nvidia and the nouveau 3d drivers to update all. should be fairly stable.
(the desktop I'm on now is fairly similar to your sig'ed hardware, an old gamimg p4, things are running quite well atm.

Currently w/ a 24" lcd using autohide, panel opacity at 0.0000, hide animation of fade only (launcher 'lock' is far upper corner w/ the mouse cursor

Unfortunately here it (still) hangs with Unity or compiz and nouveau 3D support enabled,
in classic session there are no problems or freeze.
My card is a 250gts pci-e.

---

### Post by VinDSL on 2011-02-19
Thought I'd pop back in, for a second...

I did a full update, and everything went fine!

Onward and upward...  ;)

---

### Post by mc4man on 2011-02-19
> **lucazade said:**
> Unfortunately here it (still) hangs with Unity or compiz and nouveau 3D support enabled,
in classic session there are no problems or freeze.
My card is a 250gts pci-e.
The recent update to the nouveau 3d drivers was in response to this error, whether it encompassed any others don't know
[https://bugs.launchpad.net/nouveau/+bug/710588](https://bugs.launchpad.net/nouveau/+bug/710588)
In this case unity/compiz would fail on login, not really a matter of starting then hanging, crashing.

Myself will switch back to nvidia the second it's available, can't see how nouveau will ever be as good 

Have found it's possible to create situations where compiz will crash with the nouveau 3d though in general use it's ok. In those cases usually see stuff like this in .xsession-errors or xsession-errors.old

> gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
ect.ect.

---

### Post by Harry33 on 2011-02-20
If you want to keep going with NVidia proprietary drivers,
either nvidia-current_260.19.29-0ubuntu1 (from Natty repos)
or nvidia-current_270.18-0ubuntu1 (from X Updates),
read this.

Nvidia-current needs (at the moment) xserver 1.9 series, it does not work with xserver 1.10 series.
Presuming you have now xserver 1.9 installed and a working system with nvidia-current, what are the x packages you should **not** upgrade?

These are **critical** (do not upgrade), so pin them:
 - xserver-xorg (1.7.5*)
 - xserver-xorg-core (1.9.0*)
 - xserver-xorg-video-vesa
 - xserver-xorg-input-*    the most important is -evdev and also synaptic (only in laptops)

These you do not need at all (meaning with nvidia-current):
 - xserver-xorg-input-all (meta package)
 - xserver-xorg-video-all (meta package)
 - xserver-xorg-video-* drivers (others than xserver-xorg-video-vesa, which is needed to start failsafe X).

These you can very well upgrade:
 - x11-common (1.7.6*)
 - xorg (1.7.6*)
 - xserver-common (1.9.99.*)
 - all other libx and x packages not mentioned here, they are not part of xserver.
 
However, if you already have a fully upgraded/updated Natty-alfa2, you already have xserver 1.10 series installed. Nvidia-current does not work in this environment, though it is possible to install it and break your system unbootable.
So in this case, nvidia-current will work only, after you have downgraded packages
- xserver-xorg (to 1.7.5*)
- xserver-xorg-core (to 1.9.0*)
- xserver-xorg-input-* (all of them)
- xserver-xorg-video-* (all of them)
Just remember that xserver packages and xserver-xorg driver packages work together, so they need to be downgraded at the same time.

---

### Post by doctordruidphd on 2011-02-20
Evidently aptosid has a patched nvidia driver for the new xorg files. Did the upgade yesterday, installed the nvidia-glx driver from the frickleplatz repository, and it works fine.  Tried installing nvidia-current on a fully upgraded kubuntu system today, and it although it loaded, it does not work, and a message in Xorg.0.log states that it might not. Switched back to nouveau, but no games or other effects.

So a patch is possible, question is, when or if. Aptosid's install procedure is different from k/ubuntu's, and I suspect would break other things if it were tried. But I may wind up trying it anyway, if no patch is forthcoming.

---

### Post by Harry33 on 2011-02-20
> **doctordruidphd said:**
> Evidently aptosid has a patched nvidia driver for the new xorg files. Did the upgade yesterday, installed the nvidia-glx driver from the frickleplatz repository, and it works fine.  Tried installing nvidia-current on a fully upgraded kubuntu system today, and it although it loaded, it does not work, and a message in Xorg.0.log states that it might not. Switched back to nouveau, but no games or other effects.

So a patch is possible, question is, when or if. Aptosid's install procedure is different from k/ubuntu's, and I suspect would break other things if it were tried. But I may wind up trying it anyway, if no patch is forthcoming.

I do not believe you can "patch" the closed source code.
Yes it is easy to install the package, but it won't work.
You see you need to update the source to support new ABI.
Only NVidia Corp. can do it.
Anyway, xserver 1.9 works very well and I gladly use nvidia-current with that.
Xserver 1.10 is just rc2 now and it isn't so mindblowing compared to xserver 1.9.
I will gladly wait until NVidia Corp. releases new superior drivers for X 1.10.

---

### Post by cariboo on 2011-02-20
+1, I'm happily using the Xorg 1.9 and the nvidia-current driver. I can wait until the new nvidia driver is available.

---

### Post by mick8985 on 2011-02-20
Can someone the commands to go back to an xserver configuration where nvidia-current can be used please?

---

### Post by cariboo on 2011-02-20
Check posts [101]("http://ubuntuforums.org/showpost.php?p=10442535&postcount=101") and [102]("http://ubuntuforums.org/showpost.php?p=10442692&postcount=102").

---

### Post by doctordruidphd on 2011-02-20
My mistake on aptosid--
There is a mixture of 1.9 and 1.10 packages, but the core of it is still 1.9. The break and fix were for some other problem.

I am currently running one natty system on 1.9 with nvidia-current, and a hold put on xserver-xorg-video-nv to prevent the xorg updates installing. So I guess we wait, though NVIDIA recently released a new beta driver, which does not work with xorg 1.10.

---

### Post by isaacahloe on 2011-02-20
man this is all a bit of a boner crusher for testers. I hope nvidia and nouveau teams work fast.

---

### Post by Harry33 on 2011-02-21
> **doctordruidphd said:**
> 
...
I am currently running one natty system on 1.9 with nvidia-current, and a hold put on xserver-xorg-video-nv to prevent the xorg updates installing. So I guess we wait, though NVIDIA recently released a new beta driver, which does not work with xorg 1.10.

You should lock (pin) these packages:
- xserver-xorg (1.7.5*)
- xserver-xorg-core (1.9.0*)
- xserver-xorg-video-vesa
- xserver-xorg-input-* the most important is -evdev and also synaptic (only in laptops)

Using nvidia-current, you do not need xserver-xorg-video-nv at all.

---

### Post by VinDSL on 2011-02-21
> **mc4man said:**
> Myself will switch back to nvidia the second it's available, can't see how nouveau will ever be as good.[...]
Agreed!

For those that haven't gone through this yet... the Experimental 3D Nouveau drivers will get you to Unity, but...

I sorely miss the nVidia Control Panel!

For example, the nVidia Panel allows you to adjust "Luminance Levels" (e.g. display brightness) which makes a h-u-g-e difference on my flat panel Dell display.

The alternative is to fiddle with the manual settings in my Dell display, which is like riding a rocket sled to hell!  I wouldn't touch the buttons on my monitor, if you beat me with a rubber hose, and stuck a gun in my mouth! :D

Also, there is no way to pin the resolution with the experimental drivers (AFAIK), so if you happen to use a KVM switch, Nouveau 3D will read the KVM buffer, and boot you into 640 X 480 resolution X 256 colors, if you haven't switched to your Natty machine at GRUB.

Anyway, I'll live with it for now.  I've got other irons in the fire, like implementing Conky / conkyForecast / Lua into Natty, blah, blah, blah.

Personally, I find (the switch to) Banshee more irritating than the obligatory nVidia video driver problems that seem to crop up with every new dev release.  I'm used to that, by now.  Banshee is a different matter...

> **Harry33 said:**
> If you want to keep going with NVidia proprietary drivers,[...]
Thanks, Harry33!

I wish your most excellent mash-up had been available 3 days ago, but I've made my bed, and I will sleep in it, unless I have to reinstall Natty again.  

Then, I'll take your route!  ;)

---

### Post by lucazade on 2011-02-21
> **VinDSL said:**
> Agreed!

For those that haven't gone through this yet... the Experimental 3D Nouveau drivers will get you to Unity, but...

I sorely miss the nVidia Control Panel!

For example, the nVidia Panel allows you to adjust "Luminance Levels" (e.g. display brightness) which makes a h-u-g-e difference on my flat panel Dell display.

Also, there is no way to pin the resolution with the experimental drivers (AFAIK), so if you happen to use a KTM switch, Nouveau 3D will read the KTM buffer, and boot you into 640 X 480 resolution X 256 colors, if you haven't switched to your Natty machine at GRUB.

Anyway, I'll live with it for now.  I've got other irons in the fire, like implementing Conky / conkyForecast / Lua into Natty, blah, blah, blah.

Personally, I find (the switch to) Banshee more irritating than the obligatory nVidia video driver problems that seem to crop up with every new dev release.  I'm used to it, by now.


Thanks, Harry33!

I wish your most excellent mash-up had been available 3 days ago, but I've made my bed, and I will sleep in it, unless I have to reinstall Natty again.  

Then, I'll take your route!  ;)

KTM switch?
Do you mean KMS?

---

### Post by VinDSL on 2011-02-21
> **lucazade said:**
> KTM switch?
Do you mean KMS?
Yes, thank you!  I haven't slept in (like) 28 hours...

I meant [KVM switch]("http://en.wikipedia.org/wiki/KVM_switch").  ;)

I'll fix that now.

---

### Post by mick8985 on 2011-02-21
Ok I did the instructions at post 101, worked great, I needed to use nvidia-xconfig.
Only issue is now for some reason all the videos are in negative :/ any ideas what's up with that.

---

### Post by Yes_It's_Me on 2011-02-22
> **isaacahloe said:**
> boner crusher

...

I'm happily on 1.9 with nvidia-current. Even 2D neauvou is buggy for me on my 570GTX which appears to be dying.

---

### Post by sgage on 2011-02-22
> **Yes_It's_Me said:**
> ...

I'm happily on 1.9 with nvidia-current.

I am, too. I find that using nouveau/experimental 3D my GPU runs a good 10 degrees C hotter than with the nvidia drivers. I have a fanless 8500GT card, so I sure don't need any unnecessary heat.

BTW, the card has been working great for a couple of years now. Very reliable, and silent.

---

### Post by zika on 2011-02-22
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu natty (development branch)
Release:    11.04
Codename:    natty


:~$ cat /etc/X11/xorg.conf
Section "Device"
Identifier "Default screen"
Option "ForceGallium" "True"
EndSection

:~$ glxinfo|grep render
direct rendering: Yes
**OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL DRI2**

:~$ cat /etc/apt/sources.list.d/xorg-edgers-ppa-natty.list
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main
#deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) natty main

?

---

### Post by isaacahloe on 2011-02-22
> **Yes_It's_Me said:**
> ...

I'm happily on 1.9 with nvidia-current. Even 2D neauvou is buggy for me on my 570GTX which appears to be dying.

oh yeah i just mean for testing the totally current natty with the new x-stack and everything. not bad mouthing anyone it's just overall unfortunate and like i said i hope that the nvidia and nouveau folks can get the drivers updated soon so that people can test the stuff daily via upgrading, but more specifically daily installing, without having to do extra downgrading and stuff.

i appreciate all the hard work from natty, xorg, nouoveau, nvidia. it will just be nice when everything is on the same page more or less.

---

### Post by Harry33 on 2011-02-22
> **isaacahloe said:**
> 
...
i appreciate all the hard work from natty, xorg, nouoveau, nvidia. it will just be nice when everything is on the same page more or less.

Yes it would, but it really is an impossible wish.
The development and testing of one project is one thing.
As soon as a project version is released, only then it is possible to begin the harmonizing development on another project.

After all, this is exactly the way it is done, through testing.
And we (the users of the dev versions) are testing right now.
This cannot be under development and ready to be released at the same time.

If you need more or less fully working version, stick with released distro version only. And let our dev versions show bugs, to be solved.

---

### Post by cariboo on 2011-02-22
I'm only seeing a 5° C difference on my 9400GT between nvidia-current and  nouveau, I do get corruption on right-click context menus though.

---

### Post by MacUntu on 2011-02-23
RC2 will soon land in Natty, which means we are not far away from getting a new Nvidia driver to finally fix this mess! \o/

---

### Post by Harry33 on 2011-02-23
> **MacUntu said:**
> RC2 will soon land in Natty, which means we are not far away from getting a new Nvidia driver to finally fix this mess! \o/

This is xserver 1.10 rc2 here:
[https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.9.99.902-2ubuntu1](https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.9.99.902-2ubuntu1)

---

### Post by VinDSL on 2011-02-24
> **Harry33 said:**
> This is xserver 1.10 rc2 here:
[https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.9.99.902-2ubuntu1](https://launchpad.net/ubuntu/natty/+source/xorg-server/2:1.9.99.902-2ubuntu1)
Interesting!

I just looked, and I'm already running &#8220;xorg-server&#8221; 2:1.9.99.902-2ubuntu1.

Soooo, does this mean I can ditch the experimental drivers and safely install nVidia et al.?

---

### Post by Harry33 on 2011-02-24
> **VinDSL said:**
> Interesting!

I just looked, and I'm already running “xorg-server” 2:1.9.99.902-2ubuntu1.

Soooo, does this mean I can ditch the experimental drivers and safely install nVidia et al.?

No no, don't do that.
You have now xserver 1.10 rc2 installed, but drivers that support it, is another thing.
There is no proprietary drivers available supporting it.
The latest beta release nvidia-current_270.26 works well only with xserver 1.9 or older.
So we must wait for Nvidia-Corp to upgrade the drivers next.

---

### Post by VinDSL on 2011-02-24
> **Harry33 said:**
> No no, don't do that.[...]

So we must wait for Nvidia-Corp to upgrade the drivers next.
Ok, thanks, Harry33!

I don't need any more adventures for a while.

Last night, the updates trashed my grub, and it took hours to get it back in order.  LoL!  :)

---

### Post by brianafischer on 2011-02-24
Is there an RSS feed or a resource that provides nvidia driver updates for Linux?

I couldn't find anything on [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

It would be nice to be "notified" when this driver is available.

---

### Post by portis on 2011-02-24
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)
It's not a RSS so have to check it manually or use SiteDelta for example.

> **brianafischer said:**
> Is there an RSS feed or a resource that provides nvidia driver updates for Linux?

I couldn't find anything on [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

It would be nice to be "notified" when this driver is available.

---

### Post by Harry33 on 2011-02-24
> **brianafischer said:**
> Is there an RSS feed or a resource that provides nvidia driver updates for Linux?

I couldn't find anything on [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

It would be nice to be "notified" when this driver is available.

Usually the first people to know are the ones who belong to the testing group.
I prefer to install the deb file from PPA.
You will see an announcement in this forum when it is available.

---

### Post by portis on 2011-02-24
[http://www.nvnews.net/vbulletin/showthread.php?p=2396539](http://www.nvnews.net/vbulletin/showthread.php?p=2396539)

270.29 (beta) for Linux x86/x86_64 released

    Added official support for xserver 1.10. The -ignoreABI option is no longer required with this version of the server.


The 270.29 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 270.29 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86_64 is available for download via FTP.

Please see the README (x86 / x86_64) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 270.29 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log.gz file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).

---

### Post by sgage on 2011-02-24
How long before it percolates to the natty repos? I'll be happy to un-pin my xserver stuff and move on...

---

### Post by webme on 2011-02-24
> **portis said:**
> [http://www.nvnews.net/vbulletin/showthread.php?p=2396539](http://www.nvnews.net/vbulletin/showthread.php?p=2396539)

270.29 (beta) for Linux x86/x86_64 released

    Added official support for xserver 1.10. The -ignoreABI option is no longer required with this version of the server.


The 270.29 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via FTP.
The 270.29 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86_64 is available for download via FTP.

Please see the README (x86 / x86_64) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 270.29 NVIDIA Linux graphics driver release, please start a new thread and include a detailed description of the problem, reproduction steps and generate/attach an nvidia-bug-report.log.gz file (please see [http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).

Great news!

---

### Post by cariboo on 2011-02-24
The 270.29 drivers are now available in the [X-updates ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"). This is so fresh, I haven't had the time to update myself yet. :)

**Update:** The drivers are still waiting to be built, so give it several of hours before trying to install them.

---

### Post by Harry33 on 2011-02-25
> **cariboo907 said:**
> The 270.29 drivers are now available in the [X-updates ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"). This is so fresh, I haven't had the time to update myself yet. :)

**Update:** The drivers are still waiting to be built, so give it several of hours before trying to install them.

Cariboo, these work well with the latest xserver 1.10 rc 2.
So you can now fully upgrade Natty.

---

### Post by VinDSL on 2011-02-25
> **cariboo907 said:**
> The 270.29 drivers are now available in the [X-updates ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"). This is so fresh, I haven't had the time to update myself yet. :)

**Update:** The drivers are still waiting to be built, so give it several of hours before trying to install them.

Whew!  That's good to know!

I just downloaded the nVidia run file (from the link above).

I shelled out, killed GDM, logged to root, and started the run file -- only to be greeted with "Nouveau is running and needs to be disabled".

I've never run into this problem before, while installing factory drivers, since I've never run Nouveau.  LoL!

Anyway, the PPA sounds like a better idea...

Thanks!  ;)

---

### Post by farooq23 on 2011-02-25
Finally !! The thing I have been waiting for, so eargly...

---

### Post by David Tomic on 2011-02-25
All good here .... *finally* back to my triple screen goodness! ;)

---

### Post by vikktor91 on 2011-02-25
Hmm i've some problems with the new X.I cant upgrade to it.When i try to upgrade xserver-xorg it says:
>  Depends: xserver-xorg-input-evdev but it is not going to be installed
and xserver-xorg-input-evdev says:
>  Depends: xorg-input-abi-12.1
The new nvidia drivers works, but with the older xorg(1.90)Anybody know what to do?

---

### Post by VinDSL on 2011-02-25
Oh, my!  It actually works!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-25-feb-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-feb-2011.png")[/INDENT]

---

### Post by Harry33 on 2011-02-25
> **vikktor91 said:**
> Hmm i've some problems with the new X.I cant upgrade to it.When i try to upgrade xserver-xorg it says:

and xserver-xorg-input-evdev says:

The new nvidia drivers works, but with the older xorg(1.90)Anybody know what to do?

What is the new nvidia driver you are talking about? Version number?
You see v. 270.29 (from X Updates PPA) depends on xserver 1.9.99.902-2ubuntu1 (this is 1.10 rc2) or newer.
You cannot even install it with xserver 1.9.
Note that there is no new nvidia driver in Natty repos, that one is old.

---

### Post by dino99 on 2011-02-25
i dont use input-all nor video-all, so i've only nvidia installed, that work fine of course but xorg.log complaint about missing: nouveau, nv (so oldish), vesa, fbdev fallback drivers :(

dont understand such default config ( its nice to have a fallback config, but 5 drivers is way to much )

---

### Post by Harry33 on 2011-02-25
> **dino99 said:**
> i dont use input-all nor video-all, so i've only nvidia installed, that work fine of course but xorg.log complaint about missing: nouveau, nv (so oldish), vesa, fbdev fallback drivers :(

dont understand such default config ( its nice to have a fallback config, but 5 drivers is way to much )

Yes those xserver-xorg-input-all and xserver-xorg-video-all are only meta packages.
They do nothing else than pull in a number of drivers, most of which users cannot even use.
But, you need at least one input-driver to be able input commands with keyboard and mouse.
The xserver-xorg-input-evdev does all that.
Then, in case you need to use failsafe graphics, you also need one video driver: xserver-xorg-video-vesa. That one is able to start X no matter what graphics card you have. for this purpose you also have the file xorg.conf.failsafe in your /etc/X11/ folder.
That is all you need if you have NVidia (or ATI) proprietary drivers installed.

---

### Post by portis on 2011-02-25
[http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA](http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA)

Only a few days have passed since the release of X.Org Server 1.10 RC2, but another release candidate has now arrived. Given the short turnaround time since the previous release candidate and now being days away from the final release, it's a mundane release candidate, right? Actually, no. RandR 1.4 was just pulled in its entirety from xorg-server 1.10, which also caused the server's video ABI to now be bumped again.

---

### Post by sgage on 2011-02-25
> **portis said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA](http://www.phoronix.com/scan.php?page=news_item&px=OTEzMA)

Only a few days have passed since the release of X.Org Server 1.10 RC2, but another release candidate has now arrived. Given the short turnaround time since the previous release candidate and now being days away from the final release, it's a mundane release candidate, right? Actually, no. RandR 1.4 was just pulled in its entirety from xorg-server 1.10, which also caused the server's video ABI to now be bumped again.

What does that mean, re: nvidia drivers?

---

### Post by vikktor91 on 2011-02-25
> **Harry33 said:**
> What is the new nvidia driver you are talking about? Version number?
You see v. 270.29 (from X Updates PPA) depends on xserver 1.9.99.902-2ubuntu1 (this is 1.10 rc2) or newer.
You cannot even install it with xserver 1.9.
Note that there is no new nvidia driver in Natty repos, that one is old.

I have nvidia v270.29(from x updates ppa) and downgraded X(v1.90).When i try to upgrade X it gives me the errors from the previous post.

---

### Post by portis on 2011-02-25
It means another ABI breakage will come...

> **sgage said:**
> What does that mean, re: nvidia drivers?

---

### Post by sgage on 2011-02-25
> **portis said:**
> It means another ABI breakage will come...

That's what I thought it meant :(

---

### Post by Harry33 on 2011-02-25
> **portis said:**
> It means another ABI breakage will come...

Yes this is xserver 1.10 rc3 you are talking about.
That one is not yet in Natty repos, so it does not harm us now, yet.

The xserver 1.10 rc2 we have now in Natty is marked (ABI) with xserver-video-abi-9.
However, the xserver 1.10 rc3 is market (ABI) with xserver-video-abi-10.

Trying to install that, would remove all xserver-input and xserver-video drivers + nvidia-cunrrent_270.29. So no deal with that one.
But it really is too early to worry about it.

---

### Post by Harry33 on 2011-02-25
> **vikktor91 said:**
> I have nvidia v270.29(from x updates ppa) and downgraded X(v1.90).When i try to upgrade X it gives me the errors from the previous post.

OK Vikktor91, no I think I know what is the matter.
Your system will not let new nvidia-current_270.29 install, because you have pinned (locked) the xserver1.9 series server and drivers.
Please unpin (unlock the old version) them first, and the installation will go fine.

---

### Post by mick8985 on 2011-02-25
Is it safe to upgrade without the X Updates ppa, or is it necessary?

---

### Post by webme on 2011-02-25
NVIDIA 270.29 official  is out (No  X-SWATT-PPA required), install it via update-manager.
The devs are fast!!!

---

### Post by Harry33 on 2011-02-25
> **mick8985 said:**
> Is it safe to upgrade without the X Updates ppa, or is it necessary?

Yes now it works.
Alberto Milone has uploaded the new nvidia drivers (270.29) into official repos.

---

### Post by prettl on 2011-02-25
Hy everyone,

Unfortunately it doesn't work properly for me. I have a laptop with Nvidia geforce 6200 vga and 1.5Gb memory. If the used memory amount is above approx. 65% of the whole memory I get white maximized windows if a composite manager is working.
Does anyone else have this issue or I'm alone with this?

Hear is a screenshot:[ATTACH]184467[/ATTACH]

---

### Post by webme on 2011-02-25
Works great with a 8400 GS !

---

### Post by BegbieThesec on 2011-02-25
Ok, I am too stupid, please help. 

When I try to upgrade (in Synaptic) nvidia-current I get a message that it requires "xorg-video-abi-9" and " xserver-xorg-core (>=2:1.9.99.902-2ubuntu1~)". So I try to upgrade xserver-xorg-core, but that wants to remove a lot of my xorg packages. 

I had xorg packages blocked, as most of nvidia users, then I unblocked them. I see that some folks aren't having any problems, so I was surprised (or as I said, I'm too noobish).

---

### Post by VinDSL on 2011-02-25
> **portis said:**
> It means another ABI breakage will come...

> **Harry33 said:**
> Yes this is xserver 1.10 rc3 you are talking about.
That one is not yet in Natty repos, so it does not harm us now, yet.

> **Harry33 said:**
> Please unpin (unlock the old version) them first, and the installation will go fine.
Which begs the question...

Whereas xserver 1.10 rc2 & nVidia 270.29 are working...

Is it time to pin them, in advance of xserver 1.10 rc3, and in expectation of breakage?

---

### Post by sgage on 2011-02-25
> **VinDSL said:**
> Which begs the question...

Whereas xserver 1.10 rc2 & nVidia 270.29 are working...

Is it time to pin them, in advance of xserver 1.10 rc3, and in expectation of breakage?

I already pinned mine, so I don't accidentally update myself into problems. I use Synaptic, and always check what's going on, but sometimes you get fooled. I will simply follow the news here and un-pin when the time comes.

---

### Post by Harry33 on 2011-02-25
> **VinDSL said:**
> Which begs the question...

Whereas xserver 1.10 rc2 & nVidia 270.29 are working...

Is it time to pin them, in advance of xserver 1.10 rc3, and in expectation of breakage?

You may very well do that, in order to be absolutely sure accidents do not happen.
Of course it is also possible that one or more of xserver packages gets updated within this rc2 context. But then you can always ask here on the forum, is it safe to update.

---

### Post by sgage on 2011-02-25
> **Harry33 said:**
> You may very well do that, in order to be absolutely sure accidents do not happen.
Of course it is also possible that one or more of xserver packages gets updated within this rc2 context. But then you can always ask here on the forum, is it safe to update.

You are correct, and I'd thought of that. Perhaps I ought to have a little more faith in my ability to tell what's going on :KS

---

### Post by isaacahloe on 2011-02-25
rejoice! i'm going have fun screwing around in natty after i get off work

---

### Post by sparker256 on 2011-02-25
> **BegbieThesec said:**
> Ok, I am too stupid, please help. 

When I try to upgrade (in Synaptic) nvidia-current I get a message that it requires "xorg-video-abi-9" and " xserver-xorg-core (>=2:1.9.99.902-2ubuntu1~)". So I try to upgrade xserver-xorg-core, but that wants to remove a lot of my xorg packages. 

I had xorg packages blocked, as most of nvidia users, then I unblocked them. I see that some folks aren't having any problems, so I was surprised (or as I said, I'm too noobish).

I am in the same situation and looking for a solution that does not include a reinstall.

Bill

---

### Post by Harry33 on 2011-02-25
> **BegbieThesec said:**
> Ok, I am too stupid, please help. 

When I try to upgrade (in Synaptic) nvidia-current I get a message that it requires "xorg-video-abi-9" and " xserver-xorg-core (>=2:1.9.99.902-2ubuntu1~)". So I try to upgrade xserver-xorg-core, but that wants to remove a lot of my xorg packages. 

I had xorg packages blocked, as most of nvidia users, then I unblocked them. I see that some folks aren't having any problems, so I was surprised (or as I said, I'm too noobish).

OK, let's have a look into that one.
Do you have packages from the xorg-edgers PPA installed?
Please list the xserver-xorg packages to be removed (exact name).

---

### Post by BegbieThesec on 2011-02-25
I was gonna to add xorg-edgers PPA, but then I saw new nvidia stuff is in official repos, so I didn't.

When trying to update xserver-xorg-core, it wants to remove xorg, xserver-xorg, 5 xserver-xorg-input-something packages and a lot of xserver-xorg-video-something. It also wants to install xserver-xorg-video-intel and xserver-xorg-video-nouveau. Basically same as in the past few days if I remember.

Exact names:
xorg
xserver-xorg
xserver-xorg-input-evdev
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse
xserver-xorg-input-wacom
xserver-xorg-video-apm/ark/ati/chips/cirrus/fbdev/i128/i740/mach64/mga/neomagic/nv/openchrome/r128/radeon/rendition/s3/s3virge/savage/siliconmotion/sis/sisusb/tdfx/trident/tseng/vesa/vmware/voodoo

---

### Post by Harry33 on 2011-02-25
> **BegbieThesec said:**
> I was gonna to add xorg-edgers PPA, but then I saw new nvidia stuff is in official repos, so I didn't.

When trying to update xserver-xorg-core, it wants to remove xorg, xserver-xorg, 5 xserver-xorg-input-something packages and a lot of xserver-xorg-video-something. It also wants to install xserver-xorg-video-intel and xserver-xorg-video-nouveau. Basically same as in the past few days if I remember.

Exact names:
xorg
xserver-xorg
xserver-xorg-input-evdev
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse
xserver-xorg-input-wacom
xserver-xorg-video-apm/ark/ati/chips/cirrus/fbdev/i128/i740/mach64/mga/neomagic/nv/openchrome/r128/radeon/rendition/s3/s3virge/savage/siliconmotion/sis/sisusb/tdfx/trident/tseng/vesa/vmware/voodoo

To make things easier now.
You do have nvidia-current (old one) installed.
Remove the following packages only (do not upgrade anything yet):
- xserver-xorg-input-all
- xserver-xorg-video-all
Then remove all other xserver-xorg-video-* packages,
but not xserver-xorg-video-vesa.

This removes all video drivers you cannot even use.
And it removes nouveau-driver, but you have nvidia-current there.

After that try to upgrade:
- x11-common (to version 7.6~3ubuntu8 )
- xorg (to version 7.6~3ubuntu8 )
- xserver-common (to version 1.9.99.902-2ubuntu1)

Now after that, what happens if you try to upgrade nvidia-current?
Do not upgrade, just print here what would happen.
Print here the exact version of the possible files to be removed.

---

### Post by BegbieThesec on 2011-02-25
I can remove xserver-xorg-video-packages, but when I want to remove xserver-xorg-input-evdev (all other -input aren't causing any trouble), Synaptic wants to remove also xorg, xserver-xorg and xserver-xorg-core.

And I have those updated, at least no updates available 
- x11-common (to version 7.6~3ubuntu8 )
- xorg (to version 7.6~3ubuntu8 )
- xserver-common (to version 1.9.99.902-2ubuntu1)

When I try to update nvidia-current:
nvidia-current:
 Requires: xorg-video-abi-9
  Requires: xserver-xorg-core (>=2:1.9.99.902-2ubuntu1~). but there must be installed 2:1.9.0-0ubuntu7.3 (I translated to english, but guess it's ok)

Do I have to maybe downgrade xserver-xorg-core package?

---

### Post by eco2geek on 2011-02-25
I can confirm that nvidia-current now works when installed from the regular Ubuntu repos (at least on x64 hardware). I'm running Ubuntu from a daily-build live CD dated 2/23/11. When I installed nvidia-current, it automatically upgraded all or most all of the xorg packages. (Packages: nvidia-current v270.29; xserver-xorg-core v1.9.99.902 aka X.Org X Server 1.10.0 rc 2)

Oh, and look! Unity!

(Installing and running nvidia-current from a live CD is tedious but can be done.)

---

### Post by VMC on 2011-02-25
> **eco2geek said:**
> I can confirm that nvidia-current now works when installed from the regular Ubuntu repos (at least on x64 hardware). I'm running Ubuntu from a daily-build live CD dated 2/23/11. When I installed nvidia-current, it automatically upgraded all or most all of the xorg packages. (Packages: nvidia-current v270.29; xserver-xorg-core v1.9.99.902 aka X.Org X Server 1.10.0 rc 2)

Oh, and look! Unity!

(Installing and running nvidia-current from a live CD is tedious but can be done.)

Are you sure you were using "daily-live 20110223/natty-desktop-amd64.iso " from Feb 23rd. Could you output the following of your ISO:


```
$ md5sum lucid-desktop-amd64.iso 
**c19e5139e10df2626055f1d9985856d7** lucid-desktop-amd64.iso
```

Your not having the same issue found [**_here_**]("http://ubuntuforums.org/showthread.php?t=1692326") ?

---

### Post by eco2geek on 2011-02-25
The MD5 sum is dd108dee770ae7847ef6a564162cd4cc.

[http://cdimage.ubuntu.com/daily-live/current/MD5SUMS](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS) --

e35d84befd7fc072edc2dc97b0a3a8a8 *natty-desktop-amd64+mac.iso
**dd108dee770ae7847ef6a564162cd4cc *natty-desktop-amd64.iso**
ce2dd8bf085480d85936e0c99c268f14 *natty-desktop-i386.iso
c5732f8e84d5bb6f3054699325a824ef *natty-desktop-powerpc.iso

(I actually downloaded it late last night, sometime around midnight.)

<edit> We're talking Natty here, not Lucid, right? So "regular repositories" mean "regular **Natty** repositories. Not Lucid.

---

### Post by VMC on 2011-02-25
> **eco2geek said:**
> The MD5 sum is dd108dee770ae7847ef6a564162cd4cc.

[http://cdimage.ubuntu.com/daily-live/current/MD5SUMS](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS) --

e35d84befd7fc072edc2dc97b0a3a8a8 *natty-desktop-amd64+mac.iso
**dd108dee770ae7847ef6a564162cd4cc *natty-desktop-amd64.iso**
ce2dd8bf085480d85936e0c99c268f14 *natty-desktop-i386.iso
c5732f8e84d5bb6f3054699325a824ef *natty-desktop-powerpc.iso

(I actually downloaded it late last night, sometime around midnight.)

<edit> We're talking Natty here, not Lucid, right? So "regular repositories" mean "regular **Natty** repositories. Not Lucid.
Your right, I've also been working with Lucid's ISO's updates. I read my md5sum of the latest natty and mine is the same as yours - dd108dee770ae7847ef6a564162cd4cc.

So using that natty ISO, you don't have it hanging with a wheel cursor right at the 3rd party selection?

---

### Post by eco2geek on 2011-02-26
I don't know -- I do it all from the command line, after stopping X Windows...I found using jockey (Ubuntu's proprietary driver installer) to be unreliable when running from a live CD.

(I am definitely not a fan of Unity - it's daft as a user interface on today's large, mouse-driven desktops -- but am going to install Natty and keep an eye on its progress.)

---

### Post by VMC on 2011-02-26
> **eco2geek said:**
> I don't know -- I do it all from the command line, after stopping X Windows...I found using jockey (Ubuntu's proprietary driver installer) to be unreliable when running from a live CD.

(I am definitely not a fan of Unity - it's daft as a user interface on today's large, mouse-driven desktops -- but am going to install Natty and keep an eye on its progress.)

Huh? Ubiquity won't install without X.

At any rate here's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/723990") on natty and ubiquity.

---

### Post by eco2geek on 2011-02-26
I think we're miscommunicating - I was talking about installing the proprietary nvidia drivers while running from the live CD. But we'll see how the installation goes.

<edit> Yes, the Ubuntu installer hung on the second screen ("Preparing to install Ubuntu") as in your bug report. Time to try the alternate installation CD.

<edit 2> The ncurses-based installer stopped working (as in, nothing was displayed on-screen and there was no way out except to reboot) after it said it was bringing up the partitioner. So that's the end of that, at least for now.

---

### Post by Harry33 on 2011-02-26
> **BegbieThesec said:**
> I can remove xserver-xorg-video-packages, but when I want to remove xserver-xorg-input-evdev (all other -input aren't causing any trouble), Synaptic wants to remove also xorg, xserver-xorg and xserver-xorg-core.

And I have those updated, at least no updates available 
- x11-common (to version 7.6~3ubuntu8 )
- xorg (to version 7.6~3ubuntu8 )
- xserver-common (to version 1.9.99.902-2ubuntu1)

When I try to update nvidia-current:
nvidia-current:
 Requires: xorg-video-abi-9
  Requires: xserver-xorg-core (>=2:1.9.99.902-2ubuntu1~). but there must be installed 2:1.9.0-0ubuntu7.3 (I translated to english, but guess it's ok)

Do I have to maybe downgrade xserver-xorg-core package?

Please note that I never instructed to remove xserver-xorg-input-evdev.
Without that package you are in trouble, do not remove it. It is the basic package to enable you to input anything with mouse and keyboard.
In fact a desktop PC does not need any other input driver than that.

I asked you to remove the two meta packages:
- xserver-xorg-input-all
- xserver-xorg-video-all
Did you do that?

Do you have exactly the same versions of packages x11-common, xorg and xserver-common installed that I asked?

But what is the your xserver version right now?
It seems it is 1.9.0-0ubuntu7.3 ??
That is Maverick's xserver.
This is Natty Development Forum, do you use Maverick?

Here are all of the Natty xserver versions:
1.9.0-0ubuntu7
1.9.0.902-1ubuntu1
1.9.0.902-1ubuntu2
1.9.0.902-1ubuntu3
1.9.0.902-1ubuntu4
1.9.99.901+git20110131.be3be758-0ubuntu1
1.9.99.901+git20110131.be3be758-0ubuntu3
1.9.99.901+git20110131.be3be758-0ubuntu4
1.9.99.901+git20110131.be3be758-0ubuntu5
1.9.99.901+git20110131.be3be758-0ubuntu6
1.9.99.902-2ubuntu1

---

### Post by sparker256 on 2011-02-26
> **VMC said:**
> Your right, I've also been working with Lucid's ISO's updates. I read my md5sum of the latest natty and mine is the same as yours - dd108dee770ae7847ef6a564162cd4cc.

So using that natty ISO, you don't have it hanging with a wheel cursor right at the 3rd party selection?
I had that problem when I decided to reinstall and used the 02/18/11 i386 daily live. I tried 23, 22, 21 and then went to 18 which I had used to install in the past. Using the 18th everything updated correctly and I am using the 270.29 driver.

Bill

---

### Post by BegbieThesec on 2011-02-26
Ah, I misunderstood you Harry, because I don't have those two packages installed (xserver-xorg-input-all and xserver-xorg-video-all) and I thought you meant all -video and all -input, sorry about that.

- x11-common (version 7.6~3ubuntu8 )
- xorg (version 7.6~3ubuntu8 )
- xserver-common (version 1.9.99.902-2ubuntu1) I have exactly those versions. I think maybe I updated them manually when the rest was causing those troubles to see if that way I will manage to update every one.

I use Natty of course, I upgraded my Maverick when first Alpha was released.

You mean my xserver-xorg-core? It is 2:1.9.0-0ubuntu7.3 and waiting for update to 2:1.9.99.902-2ubuntu1. As I said when trying it wants to remove a lot of xorg packages. I had to messed up something!

---

### Post by zika on 2011-02-26
Let me make it clear (for me):
If I purge 
```
xserver-xorg-video-all
xserver-xorg-input-all
xserver-xorg-video-* 
xserver-xorg-input-*
```leaving, only, 
```
xserver-xorg-video-vesa
xserver-xorg-video-ati 
xserver-xorg-input-evdev
```I'll be OK, missing nothing on an (2+ years old) desktop PC...?

As far as I remember, I've done this twice. Once it was OK, once, due to some other turbulence, I've doomed my install...

Update: It works, except I left vmware and mouse...
But, it seems that dependencies will undo my effort in next upgrade, I'm afraid... :D

---

### Post by Harry33 on 2011-02-26
> **BegbieThesec said:**
> Ah, I misunderstood you Harry, because I don't have those two packages installed (xserver-xorg-input-all and xserver-xorg-video-all) and I thought you meant all -video and all -input, sorry about that.

- x11-common (version 7.6~3ubuntu8 )
- xorg (version 7.6~3ubuntu8 )
- xserver-common (version 1.9.99.902-2ubuntu1) I have exactly those versions. I think maybe I updated them manually when the rest was causing those troubles to see if that way I will manage to update every one.

I use Natty of course, I upgraded my Maverick when first Alpha was released.

You mean my xserver-xorg-core? It is 2:1.9.0-0ubuntu7.3 and waiting for update to 2:1.9.99.902-2ubuntu1. As I said when trying it wants to remove a lot of xorg packages. I had to messed up something!

Well yes it is a bit difficult to say what has happened with your setup.
But, one thing is sure, xserver-xorg-core_1.9.0-0ubuntu7.3 is the latest xserver from Maverick (Maverick-updates), it has never been in Natty.
Please see the complete list of xserver Natty version in my post above.

---

### Post by VMC on 2011-02-26
> **sparker256 said:**
> I had that problem when I decided to reinstall and used the 02/18/11 i386 daily live. I tried 23, 22, 21 and then went to 18 which I had used to install in the past. Using the 18th everything updated correctly and I am using the 270.29 driver.

Bill

Thanks for reply Bill. My problem is I now only kept the 19th. It boot correctly but left with a blank screen. Tried nomodeset plus several other options. So I can't use ubiquity to re-install.
Hopefully ubiquity will get looked into by one of the devs.

---

### Post by eco2geek on 2011-02-26
> **VMC said:**
> Thanks for reply Bill. My problem is I now only kept the 19th. It boot correctly but left with a blank screen. Tried nomodeset plus several other options. So I can't use ubiquity to re-install.
Hopefully ubiquity will get looked into by one of the devs.

You could always grab Alpha 2, install from that, and dist-upgrade.

---

### Post by VMC on 2011-02-26
> **eco2geek said:**
> You could always grab Alpha 2, install from that, and dist-upgrade.

Thanks for reply, but I already tried that. It didn't quite work. I'll wait until Monday and see if we have a working ubiquity.

---

### Post by gnomeuser on 2011-02-28
The nouveau gallium driver now runs Unity again, however there are a lot of issues with odd drawing especially of menus where one will momentarily see the background or the window below scrambled before the menu appears. It is usable but kinda.. ugly. Also the Plymouth boot splash is mangled.

---

### Post by ratcheer on 2011-03-02
This morning, I received several new xorg modules. I did not go ahead with a safe-upgrade. Are these the new version of xorg that will break the nVidia driver again, or are they safe to go ahead and install?

Thanks,
Tim

---

### Post by dino99 on 2011-03-02
you can install them, works well here: 8500 gt no compiz on i386

---

### Post by portis on 2011-03-02
Safe to upgrade. No new xserver coming.

> **ratcheer said:**
> This morning, I received several new xorg modules. I did not go ahead with a safe-upgrade. Are these the new version of xorg that will break the nVidia driver again, or are they safe to go ahead and install?

Thanks,
Tim

---

### Post by ratcheer on 2011-03-02
Thanks, dino99 and portis.

Tim

---

### Post by Shiba on 2011-03-07
[http://www.nvnews.net/vbulletin/showthread.php?p=2399427](http://www.nvnews.net/vbulletin/showthread.php?p=2399427)

270.30 should support xserver 1.10. Someone wants to try them?

---

### Post by portis on 2011-03-07
Already tried with xserver 1.10 (I compiled xserver packages myself).
It works smoothly.

> **Shiba said:**
> [http://www.nvnews.net/vbulletin/showthread.php?p=2399427](http://www.nvnews.net/vbulletin/showthread.php?p=2399427)

270.30 should support xserver 1.10. Someone wants to try them?

---

### Post by Shiba on 2011-03-07
> **portis said:**
> Already tried with xserver 1.10 (I compiled xserver packages myself).
It works smoothly.

Does it work with natty's xserver?

---

### Post by Harry33 on 2011-03-07
> **Shiba said:**
> Does it work with natty's xserver?

NVidia Corp says this:
* Added support for xserver ABI 10 (xorg-server 1.10).
* Dropped support for xserver ABI 9 (which was only used with xorg-server 1.10 RC2
   due to a last-minute xserver change).

So basically it mean the Natty xserver 1.10rc2, which has ABI 9, is not any more supported.
However, adding these lines in xorg.conf does help:
```

Section "ServerFlags"
 Option "IgnoreABI" "True" 
EndSection

```

---

### Post by VinDSL on 2011-03-08
> **Harry33 said:**
> So basically it mean the Natty xserver 1.10rc2, which has ABI 9, is not any more supported.
However, adding these lines in xorg.conf does help:
```

Section "ServerFlags"
 Option "IgnoreABI" "True" 
EndSection

```
OMG!  Thanks for the warning!

Time to go pin things down (again)...  ;)

---

### Post by Harry33 on 2011-03-08
> **VinDSL said:**
> OMG!  Thanks for the warning!

Time to go pin things down (again)...  ;)

However, neither of these (new xserver 1.10 final and new nvidia-current_270.30) is in Natty repos yet.

---

### Post by trust-no-one on 2011-03-09
> **Roger E Critchlow Jr said:**
> Mine has been a total botch all along.  No menus work on the desktop, it never writes a usable grub.cfg, and today it just black screens on boot.

Boot the natty "recovery" image from the grub menu, drop into a root shell, do: 

    apt-get update && apt-get dist-upgrade && reboot

until it gets better.  I promise, it will get better, but I can't promise when it will get better.

If you've lost the grub entry for an alternate system on your disk because update-grub reported the partition as unwritable (why is update-grub trying to mount with write permission?) as it did for /dev/sda5 on my machine, then

  mount /dev/sda5 /mnt && umount /dev/sda5 && update-grub

may succeed in recovering the missing boot entries.  It's easier than rewriting grub.cfg by hand.

Personally, I think I'll just check back for updates sometime next week,

-- rec --

Thanks man, I just updated my main os (i'm kinda stupid) and can no longer boot, so i'll print this and try it tomorrow

---

### Post by Harry33 on 2011-03-09
> **Harry33 said:**
> However, neither of these (new xserver 1.10 final and new nvidia-current_270.30) is in Natty repos yet.

For those, who want to test new xserver1.10.0 stable release,
you can add into your sources.list xorg-edgers PPA.

You will find there:
1) xserver 1.10 stable release
    xorg-xserver1.10.0+git20110307+server-1.10-branch.35503964-0ubuntu0sarvatt

2) xserver video drivers supporting xserver 1.10, like
   xserver-xorg-video-ati_6.14.99+git20110307.6319a33c-0ubuntu0sarvatt
   xserver-xorg-video-intel_2.14.901+git20110307.34f9a333-0ubuntu0sarvatt
   xserver-xorg-video-nouveau_0.0.16+git20110307.92db2bc1-0ubuntu0sarvatt
   xserver-xorg-video-vesa_2.3.0+git20110307.0b02c685-0ubuntu0sarvatt
   ...

3) xserver input drivers for xserver 1.10, like
   xserver-xorg-input-evdev_2.6.0+git20110307.d9001a6b-0ubuntu0sarvatt
   xserver-xorg-input-synaptics_3.99+git20110116.0e27ce3a-0ubuntu8~edgers
   ...

4) nvidia proprietary drivers supporting xserver 1.10
   nvidia-current_270.30-0ubuntu1~edgers

These are there for testing (they do, however work now) and they will be uploaded into Natty repos soon.

Note, that there are still no ATI proprietary drivers available (fglrx) for xserver 1.10.

---

### Post by zika on 2011-03-09
> **Harry33 said:**
> For those, who want to test new xserver1.10.0 stable release,
you can add into your sources.list xorg-edgers PPA.

You will find there:
1) xserver 1.10 stable release
    xorg-xserver1.10.0+git20110307+server-1.10-branch.35503964-0ubuntu0sarvatt

2) xserver video drivers supporting xserver 1.10, like
   xserver-xorg-video-ati_6.14.99+git20110307.6319a33c-0ubuntu0sarvatt
   xserver-xorg-video-intel_2.14.901+git20110307.34f9a333-0ubuntu0sarvatt
   xserver-xorg-video-nouveau_0.0.16+git20110307.92db2bc1-0ubuntu0sarvatt
   xserver-xorg-video-vesa_2.3.0+git20110307.0b02c685-0ubuntu0sarvatt
   ...

3) xserver input drivers for xserver 1.10, like
   xserver-xorg-input-evdev_2.6.0+git20110307.d9001a6b-0ubuntu0sarvatt
   xserver-xorg-input-synaptics_3.99+git20110116.0e27ce3a-0ubuntu8~edgers
   ...

4) nvidia proprietary drivers supporting xserver 1.10
   nvidia-current_270.30-0ubuntu1~edgers

These are there for testing (they do, however work now) and they will be uploaded into Natty repos soon.

Note, that there are still no ATI proprietary drivers available (fglrx) for xserver 1.10.
Thank You. Back to XE after a short break... Looking (and working) nice...

---

### Post by kansasnoob on 2011-03-18
Thought I'd mention this here even though I already did so here:

[http://ubuntuforums.org/showthread.php?t=1709374](http://ubuntuforums.org/showthread.php?t=1709374)

About 7AM US Central Daylight time the US server offers this:

> ubuntu-desktop will be removed
xorg will be removed
xserver-xorg will be removed
xserver-xorg-video-all will be removed
xserver-xorg-video-apm will be removed
xserver-xorg-video-ark will be removed
xserver-xorg-video-ati will be removed
xserver-xorg-video-chips will be removed
xserver-xorg-video-cirrus will be removed
xserver-xorg-video-fbdev will be removed
xserver-xorg-video-geode will be removed
xserver-xorg-video-i128 will be removed
xserver-xorg-video-i740 will be removed
xserver-xorg-video-intel will be removed
xserver-xorg-video-mach64 will be removed
xserver-xorg-video-mga will be removed
xserver-xorg-video-neomagic will be removed
xserver-xorg-video-nouveau will be removed
xserver-xorg-video-nv will be removed
xserver-xorg-video-openchrome will be removed
xserver-xorg-video-r128 will be removed
xserver-xorg-video-radeon will be removed
xserver-xorg-video-rendition will be removed
xserver-xorg-video-s3 will be removed
xserver-xorg-video-s3virge will be removed
xserver-xorg-video-savage will be removed
xserver-xorg-video-siliconmotion will be removed
xserver-xorg-video-sis will be removed
xserver-xorg-video-sisusb will be removed
xserver-xorg-video-tdfx will be removed
xserver-xorg-video-trident will be removed
xserver-xorg-video-tseng will be removed
xserver-xorg-video-v4l will be removed
xserver-xorg-video-vesa will be removed
xserver-xorg-video-vmware will be removed
xserver-xorg-video-voodoo will be removed
exiv2 (version 0.21.1-0ubuntu1) will be upgraded to version 0.21.1-0ubuntu2
gir1.2-atk-1.0 (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libatk1.0-0 (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libatk1.0-data (version 1.33.6-0ubuntu1) will be upgraded to version 1.33.6-0ubuntu2
libexiv2-10 (version 0.21.1-0ubuntu1) will be upgraded to version 0.21.1-0ubuntu2
libpam-modules (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
libpam-runtime (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
libpam0g (version 1.1.2-2ubuntu3) will be upgraded to version 1.1.2-2ubuntu4
xserver-common (version 2:1.9.99.902-2ubuntu2) will be upgraded to version 2:1.10.0-0ubuntu1
xserver-xorg-core (version 2:1.9.99.902-2ubuntu2) will be upgraded to version 2:1.10.0-0ubuntu1
libpam-modules-bin (version 1.1.2-2ubuntu4) will be installed 

I'm sure it'll resolve with patience but undoubtedly someone will opt for the partial upgrade w/o studying first :p

---

### Post by zika on 2011-03-18
> **zika said:**
> Thank You. Back to XE after a short break... Looking (and working) nice...Until couple of days ago when screen became sluggish and slow. Back to no-XE...

---

### Post by Harry33 on 2011-03-18
At the moment, xserver 1.10 final is OK, but only a few drivers are OK.
At least nvidia-current and ati cannot be upgraded.
So do not upgrade yet, you might break your X.

---

### Post by zika on 2011-03-18
> **Harry33 said:**
> At the moment, xserver 1.10 final is OK, but only a few drivers are OK.
At least nvidia-current and ati cannot be upgraded.
So do not upgrade yet, you might break your X.
Back to XE... X-server and ATI work fine one with the other...

---

### Post by VinDSL on 2011-03-18
Come on in... 

The water is fine!

No turbulence (love that title)...  LoL!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-18-mar-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-mar-2011.png")[/INDENT]

---

### Post by wakady on 2011-03-18
> **VinDSL said:**
> Come on in... 

The water is fine!

No turbulence (love that title)...  LoL!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-18-mar-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-mar-2011.png")[/INDENT]
hey VinDSL
i love ur side bar "conky" if i'm not mistaken....can u tell me how to make it look exactly this way =]
samething with how to make the top panel transparent
thx

---

### Post by VinDSL on 2011-03-18
> **wakady said:**
> hey VinDSL
i love ur side bar "conky" if i'm not mistaken....can u tell me how to make it look exactly this way =]
Good eye!  Yes, it's a mixture of Conky, conkyForecast, and Lua.

Here's my March Data Dump(s):

[INDENT][http://ubuntuforums.org/showthread.php?p=10543931#post10543931](http://ubuntuforums.org/showthread.php?p=10543931#post10543931)[/INDENT]


> **wakady said:**
> same thing with how to make the top panel transparent
thx
You do that in the CompizConfig Settings Manager aka CCSM (you may have to install CCSM).

In CCSM...

[LIST]
[*]Click the Ubuntu Unity Plugin
[*]Then, click the Experimental Tab
[*]Adjust Panel Opacity
[/LIST]

My Panel Opacity is set to "0.0000"  ;)

---

### Post by Quackers on 2011-03-18
I've not used lua before in my conky display. I am presently poring over your .conkyrc to see where I can improve :wink:
Sadly, I've forgotten most of what I did, so will have to re-learn a bit before I tackle it :-)

---

### Post by cariboo on 2011-03-19
Seeing as the graphics driver problems seem to be mostly resolved, I'm going to unstick this thread in a couple of days.

---

### Post by dino99 on 2011-03-19
yeah everything fine on nvidia side i386, only get silly warnings about non installed driver(s) like nv or vesa i dont need/want to install

---

### Post by wakady on 2011-03-19
> **VinDSL said:**
> Good eye!  Yes, it's a mixture of Conky, conkyForecast, and Lua.

Here's my March Data Dump(s):

[INDENT][http://ubuntuforums.org/showthread.php?p=10543931#post10543931](http://ubuntuforums.org/showthread.php?p=10543931#post10543931)[/INDENT]



You do that in the CompizConfig Settings Manager aka CCSM (you may have to install CCSM).

In CCSM...

[LIST]
[*]Click the Ubuntu Unity Plugin
[*]Then, click the Experimental Tab
[*]Adjust Panel Opacity
[/LIST]

My Panel Opacity is set to "0.0000"  ;)

awesome ...thx mate :D

---

### Post by bzarnsy on 2011-03-20
i'm still having display problems. natty boots up fine but after
a few seconds the screen goes blank for about 3 seconds then 
comes on for about 30 seconds then goes blank over and over again.
dell dimension 4700
ati radeon x1300 pro
p4 3.2 gig
3gigs ddr2

---

### Post by Harry33 on 2011-03-20
> **bzarnsy said:**
> i'm still having display problems. natty boots up fine but after
a few seconds the screen goes blank for about 3 seconds then 
comes on for about 30 seconds then goes blank over and over again.
dell dimension 4700
ati radeon x1300 pro
p4 3.2 gig
3gigs ddr2

And you are using fully upgraded/updated Natty
with
ATI open source drivers installed:
xserver-xorg-video-ati (version 6.14.0-0ubuntu4)
and
You do not have this file /etc/X11/xorg.conf?

---

### Post by bzarnsy on 2011-03-20
fully upgraded updated
no xorg.conf

---

### Post by Harry33 on 2011-03-20
> **bzarnsy said:**
> fully upgraded updated
no xorg.conf

OK. Then what graphical shell are you using (what session)?

If you use Unity (Gnome Desktop) with compiz, first try uninstalling compiz packages.
If that does not help, try using Gnome Classic.

---

### Post by bzarnsy on 2011-03-20
ok. i did sudo apt-get remove compiz compiz-core
but when i logged out and back in all i got was the background and the cursor.
alt f1, alt f2... nothing so i control alt delete to restart and log in to
gnome classic (no effects)
now i have my panels and menus etc but the screen off and on thing is still doing it

---

### Post by bzarnsy on 2011-03-20
ok. i did sudo apt-get remove compiz compiz-core
but when i logged out and back in all i got was the background and the cursor.
alt f1, alt f2... nothing so i control alt delete to restart and log in to
gnome classic (no effects)
now i have my panels and menus etc but the screen off and on thing is still doing it

---

### Post by kyleabaker on 2011-03-27
I'm still unable to get the proprietary nvidia drivers working. Is it just me? I've reverted back to using libgl1-mesa-dri-experimental inorder to use unity on several occasions.

This last time, the drivers install and booted into Unity fine, except that the desktop did not appear to respond to any input. As it turns out, I was able to open a terminal (Ctrl+Alt+T), killall compiz, and then menus and desktop icons responded as expected. Any ideas?

---

### Post by sgage on 2011-03-27
I don't know what to suggest - the proprietary drivers have been working fine here ever since the X upgrade dust settled. 

I guess I'd take careful inventory of my installed X components - maybe even remove them and reinstall the critical pieces. I'd remove nvidia-current and nvidia settings, boot into nouveau/ClassicNoEffects, then run jocky and hope for the best. 

Perhaps you've already been there, done that.

---

### Post by kyleabaker on 2011-03-27
> **sgage said:**
> Perhaps you've already been there, done that.
I have, but thanks for trying to help! I'm back in nouveau now, but I'm downloading a natty iso and going to try a fresh install. I've been upgrading since Alpha 1 so I'm hoping there was just an upgrade issue along the way that never resolved itself.

I really should wait for Beta 1 next week, but since I have time today I might as well give it a go. Will report back if anything changes. :)

---

### Post by kyleabaker on 2011-03-27
On a clean install, fully updated, after installing nvidia-current via Additional Drivers and rebooting the compiz interface appears frozen.

Like before, I'm able to open a terminal and kill compiz in order to see input and applications appear. Would that make this a compiz bug or nvidia bug?

---

### Post by mc4man on 2011-03-27
> **kyleabaker said:**
> On a clean install, fully updated, after installing nvidia-current via Additional Drivers and rebooting the compiz interface appears frozen.

Like before, I'm able to open a terminal and kill compiz in order to see input and applications appear. Would that make this a compiz bug or nvidia bug?
You may wish to post your basic hardware specs (laptop or desktop, cpu, amount of ram, video adapter  ect. 
You could file a bug against either, it will be adjusted if needed

---

### Post by doctordruidphd on 2011-03-27
For what it's worth, I am running 64-bit with dual nvidia cards in sli configuration, with the nvidia-current driver. I normally run kde, but I started unity to see what would happen, and it is running without problems here. The only graphics problem I am having on the system is that when I close GIMP (and only gimp, not firefox or libreoffice) I get screen corruption -- flashes, what looks like noise all over the place, missing menu bars. That, and I have lost the bootup text -- I do not run plymouth or splash, but I get no text until after the fscks have run.  No outright crashes or startup failures on either kdm/kde or gdm/unity at this point.

Might want to check your /var/log/Xorg.0.log file and see if it mentions any problems.

---

### Post by siegi on 2011-03-27
> **mc4man said:**
> You may wish to post your basic hardware specs (laptop or desktop, cpu, amount of ram, video adapter  ect. 
You could file a bug against either, it will be adjusted if needed

I have the same problem i think.
I have a dell D830 laptop
cpu T7100, 2gb ram, nvidia Quadro NVS140M 

If i look in dmesg I see the following error:
[  124.604650] compiz[2466]: segfault at 2 ip 00007f0eeb2f9e40 sp 00007fffa59cf160 error 4 in libgdk-x11-2.0.so.0.2400.3[7f0eeb2db000+ae000]

if i run unity --reset i get.
(<unknown>:3123): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed
Segmentation fault (core dumped)

EDIT: I just opened a bug report: [https://bugs.launchpad.net/unity/+bug/743853](https://bugs.launchpad.net/unity/+bug/743853)

---

### Post by kyleabaker on 2011-03-27
3.0 Ghz AMD Athlon 64 X2 Dual Core Processor 6000+
2.0 GiB Memory
Nvidia 7300le 256mb video card
Dual monitors

Worked well with compiz in the past with the proprietary nvidia drivers. Any tips/suggestions?

---

### Post by siegi on 2011-03-28
[https://bugs.launchpad.net/unity/+bug/743853](https://bugs.launchpad.net/unity/+bug/743853)
I can't find a .crash file related to this bug so i can't make any progres.

---

### Post by cariboo on 2011-03-28
I was looking at the nVidia web site the other day and I noticed that the Quadro NVS140M  uses a different driver from nvidia-current, have you tried that driver?

---

### Post by siegi on 2011-03-28
> **cariboo907 said:**
> I was looking at the nVidia web site the other day and I noticed that the Quadro NVS140M  uses a different driver from nvidia-current, have you tried that driver?

I don't know, I just use the latest nvidia-current driver out of the repo's. which is 270.**

---

### Post by cariboo on 2011-03-28
Like I said, I only had a look, the version there is 270.19

---

### Post by mc4man on 2011-03-28
> **siegi said:**
> [https://bugs.launchpad.net/unity/+bug/743853](https://bugs.launchpad.net/unity/+bug/743853)
I can't find a .crash file related to this bug so i can't make any progres.

Are there any <whatever>.crash files in /var/crash? (should be something
If so I'd go in as root, delete them all, then do whatever causes the segfault above and see if a new <whatever>.crash shows up.
If it does r. click on, ect.

nvidia shows support for the NVS 140M in the 270.26 beta so would assume your still good with nvidia-current (270.30

---

### Post by siegi on 2011-03-29
I thought the compiz.crash wasn't related, but it seems that it's created at every starup.
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745092](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745092)

---

### Post by kyleabaker on 2011-04-02
I just installed Ubuntu 11.04 beta 1, ran all updates, rebooted, installed nvidia-current and I still get the same problem. It "appears" to only load what you see in the screenshot below, but I used keyboard shortcuts to open the terminal, print out a dmesg, take a screenshot and restart.

[IMG]http://img269.imageshack.us/img269/4455/screenshotkw.png[/IMG]

So everything seems to actually load. Anyone care to have a look at the dmesg log to see where the problem may be?

[http://dl.dropbox.com/u/145249/u1104/dmesg.txt](http://dl.dropbox.com/u/145249/u1104/dmesg.txt)

EDIT:
Maybe this xorg log will be useful as well?
[http://dl.dropbox.com/u/145249/u1104/Xorg.0.log](http://dl.dropbox.com/u/145249/u1104/Xorg.0.log)

---

### Post by cariboo on 2011-04-02
Neither of the log files show anything that would stop unity from starting, are you sure you selected Ubuntu from the session menu? That looks looks like the normal classic desktop.

---

### Post by kyleabaker on 2011-04-02
I'm positive that its Unity. Notice the spacing and vertical separater on the Ubuntu button.

I can use Unity (as I am at the moment) with the mesa experimental driver, but performance is sluggish for some things. The nvidia-current driver seems to have some conflict with my 7300le card, but no one else seems to have the same issue. Odd, cause I've not modified anything else at all.

Are there any other logs or details that might be useful in tracking down this problem?

---

### Post by FalFire on 2011-04-04
I am having problems with OpenGL performance, even after downgrading xserver to 1.9.0 by using the script posted on page 11 of this topic (64-bit version).

I did a clean install of beta 1, which installed xserver 1.10 along with the nvidia driver 270.30, which I understand is still in beta. When running my self-written, very simple OpenGL program which ran beautifully under maverick, I got very very choppy framerates. I then downgraded to xserver 1.9.0 and installed the binary nvidia driver 260.19.40 from the nvidia website (on maverick I had 260.19.06), which brought no improvements to the framerate. The weird thing is that ogv files play perfectly fine.

Could this be a problem with my development headers of OpenGL? Before running the script posted on page 11 I purged all packages nvidia-*, they are all uninstalled now, only the downloaded binary nvidia driver is. Along that I have installed freeglut3(dev), libgl1-mesa-dev, libglu1-mesa(-dev), and mesa-common-dev. Synaptic does complain about broken packages "xorg" and "xserver-xorg-video-qxl" since downgrading. 

Any help/hints would be greatly appreciated, I am kinda confused which packages I should have installed/not installed, how to fix those broken packages and how to fix my sudden framerate drops in self-written and compiled opengl programs.

---

### Post by lucazade on 2011-04-04
> **FalFire said:**
> I am having problems with OpenGL performance, even after downgrading xserver to 1.9.0 by using the script posted on page 11 of this topic (64-bit version).

I did a clean install of beta 1, which installed xserver 1.10 along with the nvidia driver 270.30, which I understand is still in beta. When running my self-written, very simple OpenGL program which ran beautifully under maverick, I got very very choppy framerates. I then downgraded to xserver 1.9.0 and installed the binary nvidia driver 260.19.40 from the nvidia website (on maverick I had 260.19.06), which brought no improvements to the framerate. The weird thing is that ogv files play perfectly fine.

Could this be a problem with my development headers of OpenGL? Before running the script posted on page 11 I purged all packages nvidia-*, they are all uninstalled now, only the downloaded binary nvidia driver is. Along that I have installed freeglut3(dev), libgl1-mesa-dev, libglu1-mesa(-dev), and mesa-common-dev. Synaptic does complain about broken packages "xorg" and "xserver-xorg-video-qxl" since downgrading. 

Any help/hints would be greatly appreciated, I am kinda confused which packages I should have installed/not installed, how to fix those broken packages and how to fix my sudden framerate drops in self-written and compiled opengl programs.

Synaptic does complain about broken package "xorg" because the downgrade script doesn't install this package for xorg 1.9. 
In a default installation this package instead is included.
So, to update from a downgraded 1.9 to 1.10 you have to remove all packages installed by the script and then install xorg 1.10 by hand.
(I know is a bit tricky but xorg package could not be downgraded in the script because of his dependencies!)

"xserver-xorg-video-qxl" is a new entry in repos and it complains because of the missing "xorg" package I told you above.

I don't know anyway why you get a framerate drop in your software :/

---

### Post by FalFire on 2011-04-04
> **lucazade said:**
> 
So, to update from a downgraded 1.9 to 1.10 you have to remove all packages installed by the script and then install xorg 1.10 by hand.


Actually I don't want to upgrade to 1.10 again because I thought that was the source of my trouble in combination with my nvidia driver. How can I make synaptic stop complaining about this package (without going back to 1.10)? I have to downgrade it too? How do I do this? It's currently at version 1:7.6+4ubuntu1, the latest.

---

### Post by lucazade on 2011-04-04
> **FalFire said:**
> Actually I don't want to upgrade to 1.10 again because I thought that was the source of my trouble in combination with my nvidia driver. How can I make synaptic stop complaining about this package (without going back to 1.10)? I have to downgrade it too? How do I do this? It's currently at version 1:7.6+4ubuntu1, the latest.

ok..
"xorg" is just a metapackage you can safely remove it.. xorg related files are included in xserver-xorg package.
(anyway when uninstalling be aware it doesn't remove anything else!)

---

