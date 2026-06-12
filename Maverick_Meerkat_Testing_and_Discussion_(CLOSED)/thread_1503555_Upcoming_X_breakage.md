---
title: "Upcoming X breakage"
date: 2010-06-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Catharsis on 2010-06-06
Source: [https://lists.ubuntu.com/archives/ubuntu-x/2010-June/000897.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-June/000897.html)

Summary for the impatient:
********************************************************************
A new X server is about to be uploaded which requires all the drivers to be rebuilt.  Be careful when upgrading in the next few days.
********************************************************************

So far in Maverick X has been a relatively sedentary beast, not much changed from Lucid.  It's time for X to get a bit more interesting…

We're going to be merging the new 1.8 X server and associated drivers from Debian over the next couple of days.  This server has a new input and video ABI, which means existing driver packages will break.

The server needs to be uploaded first so the new drivers build against the correct ABI, which means that there will be a period where safe upgrades will have held-back packages.  The dependencies should ensure that you won't accidentally get a non-working combination of Xserver and drivers, but be careful if an upgrade wants to remove X packages.

There will be another X transition later in the Maverick cycle when we switch to X server 1.9.  I'll send out a similar notice then, too.

Happy testing!

---

### Post by ranch hand on 2010-06-07
Thank you.  Very interesting.

Looking forward to the FUN.

---

### Post by wilee-nilee on 2010-06-07
Thanks for the warning, let the borkage begin.

---

### Post by autocrosser on 2010-06-07
Of course, you could use the xorg-edgers PPA & already have most of it.....waiting for the b0rkage!!!!!!  Bring on the breakage...:):guitar:

---

### Post by zika on 2010-06-07
So, if we are using xorg-edgers, we are (relatively) safe?

---

### Post by _khAttAm_ on 2010-06-07
I'm adding xorg-edgers to see how the breakage looks like. :D

---

### Post by wojox on 2010-06-07
Breakage was minimal. It started in Low-Graphics-Mode upon reboot from this mornings upgrades and rebuilt itself and went back to normal on second reboot. :P

---

### Post by philinux on 2010-06-07
Nice heads up cheers.

---

### Post by ELD on 2010-06-07
Just a note it means anyone wanting to use Proprietary ATi drivers are out of luck, they don't support 1.8 yet, we need to wait for ATi to push out a new driver, hopefully this months driver will include at least 1.8.

---

### Post by gnomeuser on 2010-06-07
> **zika said:**
> So, if we are using xorg-edgers, we are (relatively) safe?

I expect, given that you are using xorg-edgers, safe might not be a word used to describe your computing experience.. 

However if it works now using the ppa, I think it is a good indication that mainline Maverick will work.

---

### Post by _khAttAm_ on 2010-06-07
> **_khAttAm_ said:**
> I'm adding xorg-edgers to see how the breakage looks like. :D

Startup time suffered, which is normal, I guess.. Hope further startups will be fine...

No other breakups/freezes so far...

On-Board Intel GMA 3000 here.

---

### Post by zika on 2010-06-07
> **gnomeuser said:**
> I expect, given that you are using xorg-edgers, safe might not be a word used to describe your computing experience.. 

However if it works now using the ppa, I think it is a good indication that mainline Maverick will work.I had one and only one breakage in this whole 2010. and it was solved with ppa-purge and abstinence on xorg-edgers for several hours until things settled. I think that that was the moment when XE did the step that Maverick is about to do... :)

---

### Post by ronacc on 2010-06-07
I didn't get a new Xserver this AM , a new kernel (2.6.35-1 ) came down but the only X file I got was xinit . I'm amd64/nvidia and using the main server for updates .

---

### Post by gnomeuser on 2010-06-07
> **zika said:**
> I had one and only one breakage in this whole 2010. and it was solved with ppa-purge and abstinence on xorg-edgers for several hours until things settled. I think that that was the moment when XE did the step that Maverick is about to do... :)

don't get me wrong I've used xorg-edgers on all my machines for months, it is still git snapshot builds and errors can happen. E.g. right now I have this odd issue where nouveau will run compiz but after a few hours it seems to crash irrecoverably. 

I am very happy that it is so easy to test the upcoming changes and most of all that it's is opt-in and easy to revert. 

Now back to juggling those wobbly windows.

---

### Post by zika on 2010-06-07
> **gnomeuser said:**
> don't get me wrong I've used xorg-edgers on all my machines for months, it is still git snapshot builds and errors can happen. E.g. right now I have this odd issue where nouveau will run compiz but after a few hours it seems to crash irrecoverably. 

I am very happy that it is so easy to test the upcoming changes and most of all that it's is opt-in and easy to revert. 

Now back to juggling those wobbly windows.:) ATI here...

---

### Post by autocrosser on 2010-06-07
I'm on edgers & have not had any issues--nvidia here. Lots of xorg stuff over the last week & nothing but xinit today....

---

### Post by ronacc on 2010-06-07
I'm on the 195.36.24 repo Nvidia driver right now and it's working fine .

---

### Post by Jordanwb on 2010-06-07
I'm already getting breakage with the nvidia drivers and and the xorg package that came with the alpha 1 release.

*Disregard this* After deleting /etc/X11/xorg.conf and remaking it with nivida-xconfig it seems to be working now.

---

### Post by jppr on 2010-06-07
> **Jordanwb said:**
> I'm already getting breakage with the nvidia drivers and and the xorg package that came with the alpha 1 release.

*Disregard this* After deleting /etc/X11/xorg.conf and remaking it with nivida-xconfig it seems to be working now.

sudo nvidia-xconfig works always :popcorn:

---

### Post by Technoviking on 2010-06-07
*From the ubuntu-devel mailing list.*

[B]****************************************************************
A new X server is about to be uploaded which requires all the
drivers to be rebuilt.  Be careful when upgrading in the next few
days.
****************************************************************[/B]

So far in Maverick X has been a relatively sedentary beast, not much changed from Lucid.  It's time for X to get a bit more interesting…

We're going to be merging the new 1.8 X server and associated drivers from Debian over the next couple of days.  This server has a new input and video ABI, which means existing driver packages will break.

The server needs to be uploaded first so the new drivers build against the correct ABI, which means that there will be a period where safe upgrades will have held-back packages.  The dependencies should ensure that you won't accidentally get a non-working combination of Xserver and drivers, but be careful if an upgrade wants to remove X packages.

There will be another X transition later in the Maverick cycle when we switch to X server 1.9.  I'll send out a similar notice then, too.

Happy testing!
--
Ubuntu-devel-discuss mailing list
[email]Ubuntu-devel-discuss@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

---

### Post by zika on 2010-06-07
[http://ubuntuforums.org/showthread.php?t=1503555](http://ubuntuforums.org/showthread.php?t=1503555)

---

### Post by bapoumba on 2010-06-07
Threads merged.

---

### Post by Catharsis on 2010-06-07
And so it begins.

[https://lists.ubuntu.com/archives/maverick-changes/2010-June/001321.html](https://lists.ubuntu.com/archives/maverick-changes/2010-June/001321.html)

---

### Post by donniezazen on 2010-06-07
Just added xorg-edgers ppa and do i need to install anything. I upgraded and everything works fine.

---

### Post by autocrosser on 2010-06-07
Sit down, hold on tight & wait........:guitar:

---

### Post by Starks on 2010-06-07
> **ELD said:**
> Just a note it means anyone wanting to use Proprietary ATi drivers are out of luck, they don't support 1.8 yet, we need to wait for ATi to push out a new driver, hopefully this months driver will include at least 1.8.
You may need to wait until early October.

---

### Post by alphacrucis2 on 2010-06-07
> **Starks said:**
> You may need to wait until early October.

It is typical that we are at least at beta before ATI ship a catalyst update that works with the new stuff.

---

### Post by eumel on 2010-06-10
> **soham_1207 said:**
> Just added xorg-edgers ppa and do i need to install anything. I upgraded and everything works fine.

I can confirm that. I've done this few days age due to the known problems with older ati radeon's. I own a Thinkpad with mobility radeon x1400 in it. Now, with Gallium from edgers ppa it simply works! Thanks to all the devs who made this possible!

---

### Post by demosdemon on 2010-06-10
Doh! I wish I read this before I blindly full-upgraded.

For me, nvidia glx drivers went bye bye, and xorg refused to start. Had to manually reset the xorg configuration via ssh.

---

### Post by eumel on 2010-06-10
> **demosdemon said:**
> Doh! I wish I read this before I blindly full-upgraded.

For me, nvidia glx drivers went bye bye, and xorg refused to start. Had to manually reset the xorg configuration via ssh.

I also had problems with xorg and ati drivers etc (also with karmic,...) and in the case xorg doesn't start i booted up with recovery modus from grub. There you can drop to a root shell instead of doing it remotely via ssh. Alternatively you can drop to a tty with STRG + ALT + F1 when xorg shows nothing, log in and modify it there. but i think you've solved your problem  so take this as a hint if you don't know that already ;)

---

### Post by bennachie on 2010-06-10
Despite the warnings (which were much appreciated - I refrained from any updates until the complete set of X packages became available) the switch to the new setup has so far been entirely trouble-free on my, admittedly plain vanilla, Lenovo desktop PC.

From my limited perspective, Meerkat is actually a good deal more solid and reliable at the moment than a number of other distros that are allegedly at (or very close) to their final releases. No doubt there are bumpier days ahead ...

---

### Post by DougieFresh4U on 2010-06-11
I let it run the 100+ updates/upgrades and all was good after reboot.
AMD Athlon 64  5200x2
ATI RADEON HD3200
2.26.35 kernel
I shall try my other partitions later :)

---

### Post by null_pointer_us on 2010-06-11
Although I had fglrx installed (Evergreen, e.g. HD5770) and was aware of the breakage, I chose to upgrade xorg this morning. Upon reboot, I got a warning that Ubuntu was starting in low graphics mode. How nice that was! I remember when a failed xorg/XFree86 start often resulted in black screen hangs, perpetual gdm crashes, etc.

I uninstalled fglrx, which went smoothly. I want to try the new HD5770 stuff in xorg 1.8 / kernel 2.6.35. On the next boot, the KMS in plymouth was a pleasant surprise. Of course, I've probably got zero 2D acceleration with my Evergreen card, but for simple web browsing and light work this is fine. Excellent work so far!

---

### Post by jerrylamos on 2010-06-11
Busted.  Entirely.  This is intel i845G which was running fine, KMS, intel driver, the whole bit with Alpha 1 kernel 2.6.34-5.  That kernel still does.

Kernel 2.6.35-2 hangs black screen solid partway into boot and won't respond to any key but power off.  ssh from another pc finds no one home.

i915.modeset=0 in the linux boot line enables boot in recovery mode however sudo startx gets some limited x screen that won't do anything.  With 

/etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

it's up and running with 2.6.35-2.  Lucid had the same? similar? problem and got a fix as in launchpad bug #539772.  I don't know if that lucid-proposed fix would work for maverick.

Launchpad bug # is 592802.

Jerry

---

### Post by VMC on 2010-06-11
> **jerrylamos said:**
> Busted.  Entirely.  This is intel i845G which was running fine, KMS, intel driver, the whole bit with Alpha 1 kernel 2.6.34-5.  That kernel still does.

...
Launchpad bug # is 592802.

Jerry

Mine is busted as well. I have an Intel i865 chip. *nomodeset* at least allows me to boot, but then a dialog appears telling me I'm in low graphics mode and no matter what option I choose, It then freezes.

---

### Post by kansasnoob on 2010-06-11
Many thanks to whoever made this a sticky :D

I am, and will be, toast for a while dealing with "stuff" but I really appreciate this.

---

### Post by skabdulraheemneo on 2010-06-12
hi 
i am testing the ubuntu maverick
after upgrade to kernel 2.6.35 i am facing black screen hangup after the grub 
however the system is running fine with the kernel 2.6.34-5
i am running ubuntu on an old desktop with integrated intel graphics card 82845GL
please redirect me if this is not the right forum
i also have a blocked PCI ID 8086:2562 since i upgraded to lucid.
thanks in advance

---

### Post by VMC on 2010-06-12
> **skabdulraheemneo said:**
> hi 
i am testing the ubuntu maverick
after upgrade to kernel 2.6.35 i am facing black screen hangup after the grub 
however the system is running fine with the kernel 2.6.34-5
i am running ubuntu on an old desktop with integrated intel graphics card 82845GL
please redirect me if this is not the right forum
i also have a blocked PCI ID 8086:2562 since i upgraded to lucid.
thanks in advance

I have a 82865 and have same problem regardless of which kernel I use. I did find out that if I add "*i915.modeset=0*" to the boot string I can then boot but have low graphics dialog pop up and only allowed 640x480 mode. Older Intel graphics seem to be the only ones suffering right now, from what I'm reading. Changing xorg.conf makes no difference.

---

### Post by timosha on 2010-06-12
My 5 cents:

On a Thinkpad R51 - 2887 with Intel graphics chip 855GM everything works fine except for Compiz.

On the same Thinkpad on another partition with the xorg-edgers drivers everything works fine as well and even Compiz is working on this installation.

---

### Post by 3vi1 on 2010-06-12
From the way you guys are talking, I gather that the packages were all uploaded?

My system's acting like they're still held back or waiting on some other dependency.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-openchrome
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.

evil@saturn:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  xserver-xorg-video-all xserver-xorg-video-tseng
The following NEW packages will be installed:
  libx11-xcb1 libxcb-dri2-0
The following packages have been kept back:
  xserver-xorg xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-openchrome
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 2 newly installed, 2 to remove and 36 not upgraded.
Need to get 100kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

evil@saturn:~$ sudo apt-get install xserver-xorg xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-core: Breaks: xserver-xorg-video-6
E: Broken packages

```

---

### Post by ranch hand on 2010-06-12
Have you checked in synaptic to find out what the broken packages are?

---

### Post by 3vi1 on 2010-06-12
> **ranch hand said:**
> Have you checked in synaptic to find out what the broken packages are?

There are no broken packages (the Broken section is empty).  I think it's saying it can't install the new one because it will break xorg.

---

### Post by ranch hand on 2010-06-12
Could be your mirror is behind a little.  Good things come to those who wait.

You could see what synaptic says if you try to mark the troublesome packages for upgrade and find out what is happening a little more.

---

### Post by LaneLester on 2010-06-12
I just downloaded and installed Maverick 64-bit Minimal CD today (6/12), and when I asked Synaptic to install nvidia-current for me, it said, "Sure, but I'm going delete everything with "xorg" in its name." I decided against it, since an X driver with no X didn't seem worthwhile.

I have a fairly-new nVidia motherboard chipset, so the video won't be very good until this problem goes away.

Lane

---

### Post by 3vi1 on 2010-06-12
> **ranch hand said:**
> Could be your mirror is behind a little.  Good things come to those who wait.

You could see what synaptic says if you try to mark the troublesome packages for upgrade and find out what is happening a little more.

I switched my mirror to the main repo yesterday and still get the same symptoms.

Marking the packages with Synaptic shows me the same symptoms as with apt-get.  :\

Basically, it refuses to update -core.

> evil@saturn:~$ sudo apt-get install xserver-xorg xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev  xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-openchrome  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
[sudo] password for evil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-core: Breaks: xserver-xorg-video-6
E: Broken packages
evil@saturn:~$ 


Package xserver-xorg-video-6 is a virtual package provided by:
  xserver-xorg-video-glamo 0.0.0+20091108.git9918e082-1
  virtualbox-ose-guest-x11 3.2.0-dfsg-1ubuntu1
  nvidia-current 195.36.24-0ubuntu1
  nvidia-96 96.43.17-0ubuntu1
  nvidia-173 173.14.22-0ubuntu11

So, I'm guessing that it doesn't want to do it with the "current" nvidia-current drivers.

---

### Post by cariboo on 2010-06-12
Many of us are using the Nvidia 256.29 driver from the [xorg-edger]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa. I haven't had the problem on two systems using Nvida graphics cards. My netbook with Intel 945 graphics chipset finally installed all the drivers yesterday, after waiting for it seems forever. :)

---

### Post by LaneLester on 2010-06-12
> **cariboo907 said:**
> Many of us are using the Nvidia 256.29 driver from the [xorg-edger]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa.

I have several partitions on my "operating system" drive, so I can afford to take chances. I'd like to try this ppa, but after looking around the site and some of the links, I'm not clear on just what I should do. Is this all that's involved:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
```
And then use apt-get to, what, get nvidia-current? Or something else?

When I did that with the standard repositories, that's when I got the information that xorg would be removed.

**Later**: Being an impatient person, I went ahead and booted to Ubuntu Maverick Minimal CD 64-bit  (plus my favorite goodies), used the above commands, ran synaptic, and installed nvidia-current. I noted with pleasure that this time there was no warning that xorg would be removed. And the install was successful.

Lane

---

### Post by cariboo on 2010-06-12
There are instructions at the bottom of the page on how to enable the ppa.

Once it is enabled, just do an update, then an upgrade, it will replace the driver you are using now.

---

### Post by ronacc on 2010-06-13
what should be the currently installed xserver-xorg and xserver-xorg-core ? I have the xserver-common 2.1.8.1.901 but the newer versions of xserver-xorg and ~-core are being held back along with a lot of other xorg stuff .

---

### Post by 3vi1 on 2010-06-13
> **cariboo907 said:**
> Many of us are using the Nvidia 256.29 driver from the [xorg-edger]("https://launchpad.net/~xorg-edgers/+archive/ppa") ppa. I haven't had the problem on two systems using Nvida graphics cards. My netbook with Intel 945 graphics chipset finally installed all the drivers yesterday, after waiting for it seems forever. :)

Thanks for the info, Cariboo!

I replaced my video drivers with the edgers 256 package and, as I suspected, was then able to do the Xorg upgrade.  Everything appears to work great so far.

Now, if the KDE/plasma packages would just get past the breakage that keeps resetting that desktop to default wallpaper/no plasmoids...  Oh well, it's giving me some time to experiment and submit items for the Gnome wishlist.

Thanks again!

---

### Post by cariboo on 2010-06-13
> **ronacc said:**
> what should be the currently installed xserver-xorg and xserver-xorg-core ? I have the xserver-common 2.1.8.1.901 but the newer versions of xserver-xorg and ~-core are being held back along with a lot of other xorg stuff .

That's what I have, I don't have anything held back.

---

### Post by ronacc on 2010-06-13
I found what was blocking those packages for me . I had the repo 195 nvidia driver already enabled . I removed that rebooted into low graphics , then everything updated . Then I added the xorg-edgers ppa and installed the 256 driver .

---

### Post by plun on 2010-06-13
> **ronacc said:**
> I found what was blocking those packages for me . I had the repo 195 nvidia driver already enabled . I removed that rebooted into low graphics , then everything updated . Then I added the xorg-edgers ppa and installed the 256 driver .

Just remember ppa-purge if something goes wrong....):P

> To revert to official packages, you can install the ppa-purge package and run "sudo ppa-purge xorg-edgers"

Xorg-edgers can be really unstable.... but next major upgrade comes later this summer when the 1.9 version will be in. (maybe also breaks nvidia and ABI, who knows...:-\")

---

### Post by ronacc on 2010-06-13
I normally just hand install the driver from Nvidia but this time it bitched about wrong gcc version so I went with the PPA . I zsync the daily live so worst case I'll reinstall .

---

### Post by philinux on 2010-06-13
I never do work arounds during testing. I'll sit tight till it sorts itself out as usual. 8)

---

### Post by ronacc on 2010-06-13
> **philinux said:**
> I never do work arounds during testing. I'll sit tight till it sorts itself out as usual. 8)

thats hardly the kind of quote I would expect from captain Kirk :lolflag:

---

### Post by cecilpierce on 2010-06-13
just added xorg-edgers and now my mouse doesn't have the three button emulation with the left and right buttons together, instead its hold down the mouse-wheel.
has anybody else have this or a fix ?

---

### Post by philinux on 2010-06-14
> **ronacc said:**
> thats hardly the kind of quote I would expect from captain Kirk :lolflag:

Yes but we have the xorg on the starboard bow!

[edit] All sorted now. xorg has been assimilated!

---

### Post by ronacc on 2010-06-14
you mean theres on one left for Piccard to wrestle with :confused:

---

### Post by kansasnoob on 2010-06-14
Late yesterday I was finally able to update with nothing held back and all seems well ATM :guitar:

---

### Post by MacUntu on 2010-06-14
> **ronacc said:**
> I normally just hand install the driver from Nvidia but this time it bitched about wrong gcc version so I went with the PPA .
AFAIK that's because you had the nouveau module loaded. Blacklist it, remove xserver-xorg-video-nouveau (just to make sure), reboot to command line and try the installer again - should work fine.

---

### Post by ronacc on 2010-06-14
I did not have the noveau driver loaded , that was from a recovery terminal with no gui loaded .

---

### Post by philinux on 2010-06-15
Looks like I'll be able to install nvidia-current soon without borking X.

[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01557.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01557.html)

Got accepted today.

---

### Post by MacUntu on 2010-06-15
> **ronacc said:**
> that was from a recovery terminal with no gui loaded .

This has nothing to do with X - the kernel module gets loaded unless you blacklist it, and with a loaded nouveau module the installer won't work. ;)

---

### Post by philinux on 2010-06-15
nvidia-current came through. Installed and rebooted all ok.

Even got fan speed showing for first time in nvidia settings manager.

---

### Post by recluce on 2010-06-15
Aptitude held back all the x.org updates until today, when the new nvidia-current became available. In just one upgrade session, new kernel, new x.org and new nvidia drivers. I was sure that borkage was in my future.

And.... nothing. Just rebooted, everything works, no problems whatsoever. The meerkat is almost disgustingly tame for an alpha version beast! :lolflag:

---

### Post by 23meg on 2010-06-15
No longer a sticky, since 1.8 has pretty much landed.

---

### Post by ronacc on 2010-06-15
> **MacUntu said:**
> This has nothing to do with X - the kernel module gets loaded unless you blacklist it, and with a loaded nouveau module the installer won't work. ;)

thanks , I hadn't run into that before so I wasn't aware of nouveau being loaded by default .

---

