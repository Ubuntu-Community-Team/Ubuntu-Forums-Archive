---
title: "Ubuntu stopped working after Natty upgrade"
date: 2011-02-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Typhoid on 2011-02-02
I have recently upgraded from Ubuntu Netbook 10.10 to 11.04 (developer branch), and I have rebooted. Then, Ubuntu boots as normal, but an error message came up: "You do not have the hardware requirement to run Unity. Installing a new driver may be a help." Then it asks me if I want to try Ubuntu classic desktop, and it brings up two options: "Change user session" or "Close". after clicking on the former (I have tried the latter, too, with the same effect), the regular Ubuntu purple background shows, as well as the mouse cursor, but then nothing. No interface, no icons, menu, panel, no Unity. It is unusable. Logging in as root has the same effect. However, I was able to bring up the recovery console. Now what? Any help on this pressing issue would be greatly appreciated.

---

### Post by coffeecat on 2011-02-02
First, you should post Natty questions in the Natty testing subforum, here:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

I'll ask a mod to move this thread there, but first let's see if I can help. You are able to boot into the recovery console. Are you able to boot into the recovery console and then into "drop to root shell with networking"? And are you able to connect your netbook to your router with an ethernet cable? If yes to both then I'm hoping that an ordinary update will fix this because you chose to upgrade to Natty at a difficult time - we were in the midst of a major transition in the xserver and a couple of updates (temporarily) broke Unity.

Try this. Boot up in the recovery console and go into the root shell with networking. First:

```
apt-get update
```Note that you don't need sudo. Now install aptitude - it's probably safer at this stage of the game with occasional unmet dependencies in the testing repository.

```
apt-get install aptitude
```Now attempt a system update with aptitude:

```
aptitude safe-upgrade
```Take particular note of anything it wants to uninstall and post back if you're unsure. If it says it wants to install libglew1.5-dev_1.5.7.is.1.5.2-1 and libglewmx1.5-dev_1.5.7.is.1.5.2-1 that's good. There were bad libglew and libglewmx packages a day or so ago that broke Unity.

---

### Post by philinux on 2011-02-02
Thread moved to Natty testing forum.

---

### Post by Typhoid on 2011-02-02
coffeecat's solution seems to work, but Unity seems to crash once in a while, bringing me to a similar state to the one before the aptitude upgrade, forcing me to reboot. I think this might be related to the error message I got before about the hardware requirement to run Unity. I think this may be related to my graphics card/driver or to Compiz (my graphics driver is "fbdev" and the card is "Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)"). I have a Toshiba NB100 Netbook. Any ideas?

UPDATE: I ran```
glxgears
```to do a 3D test, and it worked very well at 50 FPS. Just saying.

---

### Post by cariboo on 2011-02-02
Unity isn't very stable at this moment, there is another update today that might help the stability a bit. We are using alpha software after all, so a bit of flakiness is expected.

I've got the same Intel chipset in my netbook, I've been using the i915 driver since the tool chain was uploaded, and haven't had any problems since very early in the testing cycle where you never knew whether it would  boot to a desktop or not. It's been really stable for the last month or more.

---

### Post by Harry33 on 2011-02-02
> **Typhoid said:**
> 
...
(my graphics driver is "fbdev" and the card is "Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)"). I have a Toshiba NB100 Netbook. Any ideas?
...


Xserver-xorg-video-fbdev is not the best possible driver for Intel 945.
You should try xserver-xorg-video-intel driver instead.
```
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
and i965 series chips.
This package also provides XvMC (XVideo Motion Compensation) drivers
for i810/i815 and i9xx and newer chipsets.
```

---

### Post by Typhoid on 2011-02-02
Now a new problem: after playing around in Compiz, I have turned the Unity Plugin off, which put me in the state discussed previously. How do I turn Unity back on? (I can't normally access Compiz or anything else)

---

### Post by cariboo on 2011-02-02
If you can open a terminal, type:

```
ccsm
```

at the prompt.

---

### Post by Typhoid on 2011-02-02
But I can't access the terminal. Would it work at the recovery console?

---

### Post by coffeecat on 2011-02-02
> **Typhoid said:**
> But I can't access the terminal. Would it work at the recovery console?

No.

If you press ctrl-alt-T that should bring a terminal up in the GUI.

---

### Post by mc4man on 2011-02-02
I'm not on natty atm but if you can't get the plugin enabled from the desktop there would likely be gconf command that could be run from recovery console.

Otherwise on the desktop you could also, if you can't get a terminal, try creating a desktop launcher with a command of ccsm

---

### Post by Typhoid on 2011-02-02
Ctrl+Alt+T doesn't work. Actually, an error message came up saying the Compiz has crashed. I selected the option to restart Compiz, and I turned the Unity Plugin back on from the Compiz window that came up, with no luck (even after reboot). I've also played around with Compiz in the Classic Desktop, but nothing seems to work. I've also tried```
aptitude safe-upgrade
```in the recovery console, as coffeecat proposed, but nothing changed. Anything else I can do?

---

### Post by coffeecat on 2011-02-02
I wonder if the problem is the fbdev driver. I don't think you can get 3d/compiz with that at all. You'd need the intel driver. How you do that I'll have to leave to those more knowledgeable about Intel video.

What I don't understand is how you got the fbdev driver in the first place. The system should default to the intel driver with the 945 chipset.

---

### Post by Typhoid on 2011-02-02
Right now I am on Ubuntu Classic Desktop, but I miss Unity. I like it so much more.

coffeecat, note that the```
glxgears
```worked fine for me, but I will try to install the Intel drivers.

After```
aptitude safe-upgrade
```everything worked fine (apart from occasional Unity crashes), until I accidentally turned the Unity Plugin off in Compiz. I can't seem to turn it back on with any conventional means, so now it's time for unconventional warfare. I guess I will try to install the standard Intel drivers (I'd be happy if I could be provided with instructions for that), then if that doesn't work, I'll safely reinstall Natty (I'd prefer instructions on that), and note that```
aptitude safe-upgrade
```doesn't seem to work for me anymore) and if any more problems arise, I will downgrade to Maverick (I'd appreciate instructions for that, too).

---

### Post by Typhoid on 2011-02-02
My last post detailed my goals on the long run. Even though Classic Desktop works fine, my goal here is to bring back Unity. I need to get to the root of this problem (no, I don't mean the user* root*). First I will install an Intel driver. In order to do this, I need to know exactly which driver I need to install, and how to install it. Please note that my current graphics card is Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) and the driver (of unknown origin) "fbdev". Any help with this would be greatly appreciated. Thanks in advance.

---

### Post by Typhoid on 2011-02-02
> **coffeecat said:**
> I wonder if the problem is the fbdev driver. I don't think you can get 3d/compiz with that at all. You'd need the intel driver. How you do that I'll have to leave to those more knowledgeable about Intel video.

What I don't understand is how you got the fbdev driver in the first place. The system should default to the intel driver with the 945 chipset.
Thanks to this post and the error message mentioned in my first post on this thread, I have concluded that I must install an Intel graphics driver. I have posted this thread to help me do that: [http://ubuntuforums.org/showthread.php?p=10423027#post10423027](http://ubuntuforums.org/showthread.php?p=10423027#post10423027). Any help in this thread would be greatly appreciated. Thanks in advance.

---

### Post by Typhoid on 2011-02-02
I have reinstalled xserver-xorg-video-intel driver. Nothing changed. Also, I have discovered that Unity (obviously) doesn't work in *Ubuntu Classic Desktop (no effects)*, works in Ubuntu Classic Desktop (although it's VERY unstable and has many items missing and will often crash), but doesn't work in the regular Ubuntu Desktop Edition interface (note that the Ubuntu Desktop Edition interface is actually the Netbook Interface). What gives?

I am coming to understand that this is an issue with Compiz, possible with my drivers, possibly with the software. I think that the reason for Unity not working is because Compiz crashes on startup of a regular session, but this doesn't happen on the Ubuntu Classic Desktop session. 

As instructed on the Compiz Wiki Troubleshooting page, I did```

compiz --replace ccp & emerald --replace &
```which gave me repeated```
** (<unknown>:2642): WARNING **: Unable to perform Sync() on panel service: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```then```
(<unknown>:2642): GLib-GIO-CRITICAL **: g_dbus_proxy_get_name_owner: assertion `G_IS_DBUS_PROXY (proxy)' failed

WARNING: Unable to connect to the unity-panel-service Error calling StartServiceByName for com.canonical.Unity.Panel.Service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity/unity-panel-service received signal 5

(<unknown>:2642): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:2642): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit

(<unknown>:2642): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

```then```
(<unknown>:2642): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:2642): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:2642): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

```Obviously something's wrong. Now if any of you could decode this or give me further troubleshooting tips...

---

### Post by mc4man on 2011-02-02
Don't know intel at all, but at least here nvidia (nouveau 3d), will not work with the current natty - unity/compiz/nux/xserver

This current bug, (same error as nvidia), was filed by a intel user so you may wish to keep an eye on if you can't get going.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/710588)

Edit: the bug was for nouveau only, misread the bug poster's info, was intel bios, not video

---

### Post by cariboo on 2011-02-02
@Typhoid is your system using the Intel driver? To check in a terminal type:

```
lsmod | grep i915
```

If the module is loaded it should show up in the listing from the above command.

I would concentrate on getting the system up and running properly before worrying about which interface is which. There is no difference between the netbook and desktop interface at this time, except for applications opening full screen in the the netbook version.

As an aside, my netbook (Compaq Mini 110) is using the latest xorg version without any problems.

---

### Post by Typhoid on 2011-02-03
All the listings say "i915", so I guess they're loaded up. 

I'm pretty much out of ideas. It's up to you guys to help me out here. If you guys are out, too, then I guess I can go ahead with the 10.10 downgrade. Then, I'll just wait until 11.04 is formally released. It would be nice if someone could tell me how to perform this downgrade, but only as a last resort. If you guys want to try something else out, then by all means, tell me. As you can probably tell, this whole thing is very exhausting, and is taking its toll on me. (hence, "I'm out of ideas").

*sigh* F My Life

---

### Post by Harry33 on 2011-02-03
> **Typhoid said:**
> All the listings say "i915", so I guess they're loaded up. 

I'm pretty much out of ideas. It's up to you guys to help me out here. If you guys are out, too, then I guess I can go ahead with the 10.10 downgrade. Then, I'll just wait until 11.04 is formally released. It would be nice if someone could tell me how to perform this downgrade, but only as a last resort. If you guys want to try something else out, then by all means, tell me. As you can probably tell, this whole thing is very exhausting, and is taking its toll on me. (hence, "I'm out of ideas").

*sigh* F My Life

First of all, you cannot downgrade Natty to Maverick.
Technically it might be possible but it is much easier to reinstall Maverick.

Secondly, I do not know how do you determine that your system is using xserver-xorg-video-fbdev as graphics driver.
If you have xserver-xorg-video-intel installed, your system would automatically pick it up on every boot.

But if you still have problems, check if you have this file in your system:
/etc/X11/xorg.conf
If you have it, please print here all it contains, and we will take a look at it.
With Intel graphics card, you can delete that file too, it is not needed after all.

---

### Post by jerrylamos on 2011-02-03
'''
The 2 February CD Daily build crashes Xorg on both new and old intel, ati, ...  It's essentially dead.
'''
Natty upgrades from Alpha 1 to current are also dead.  Won't even boot without a kernel crash.  Ever.
...
In particular on Aspire one netbook, Compaq Presario, ... the Natty level of Grub 2 screws up.  That's a red flag if there is ever one.  
Jerry

3 February could boot in recovery mode, did fix broken packages, now the Compaq ati radeon xpress 200 is running Unity.  Again.  For how long?

Do note I installed Grub-2 from Lucid 10.04 since I've got several backup partitions.

Don't know about the Aspire one notebook yet

Jerry

---

### Post by Typhoid on 2011-02-03
> **Harry33 said:**
> First of all, you cannot downgrade Natty to Maverick.
Technically it might be possible but it is much easier to reinstall Maverick.

Secondly, I do not know how do you determine that your system is using xserver-xorg-video-fbdev as graphics driver.
If you have xserver-xorg-video-intel installed, your system would automatically pick it up on every boot.

But if you still have problems, check if you have this file in your system:
/etc/X11/xorg.conf
If you have it, please print here all it contains, and we will take a look at it.
With Intel graphics card, you can delete that file too, it is not needed after all.
What's the difference between downgrading and just reinstalling an earlier version?

About the graphics card, I determined that I have the "fbdev" driver using this file. I checked it after installing the new driver but it stayed the same. I think we have to figure out how to get the system to actually use the new driver. Also, I don' know why, but the file that's supposed to be called "xorg.conf" is actually called (for me) "xorg.conf.failsafe. Anyway, here it is:```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Once again, I think what we must do now is to get the xserver-xorg-video-intel driver to be actually used by the system. Or is the system already using it? One more thing: when I log in, now it says that not only Compiz crashed but also "aptd" crashed. Also: the sound doesn't seem to work for me. Is this because I'm using *Ubuntu Classic Desktop (no effects)*? When I open sound control, a box shows up: "Waiting for sound system to respond..."

---

### Post by Typhoid on 2011-02-03
I think I found the problem. I installed and ran Compiz-Check, a program that checks if your current drivers are compatible with Compiz, and it gave me this:```

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```After that it opens up Additional Driver, which then says that no proprietary drivers are in use, so therefore I can't do anything from there. Therefore I need to get a good, compatible driver and ACTUALLY GET IT TO WORK! Speaking of which, I don't know anything about any vesa driver. I don't know how it got there. But it's there.

---

### Post by jerrylamos on 2011-02-03
"vesa" and "fbdev" are existing software drivers I think.  They've got some limitations in screen support.

In particular neither of them will run Compiz so the session to use is Ubuntu session no effects.

vesa and fbdev are fallbacks in case Compiz is busted as usual.

Jerry

---

### Post by Typhoid on 2011-02-03
Thanks Jerry. I am using Ubuntu with no effects. I have installed the xserver-xorg-video-intel driver, but the system seems to use vesa and fbdev. I want to get the system to use the intel driver. How do I do that?

---

### Post by jerrylamos on 2011-02-03
> **Typhoid said:**
> Thanks Jerry. I am using Ubuntu with no effects. I have installed the xserver-xorg-video-intel driver, but the system seems to use vesa and fbdev. I want to get the system to use the intel driver. How do I do that?

In the /etc/X11/xorg.conf example above replace "vesa" with "i915" and give it a go.  With no xorg.conf it "should" default to intel's i915.

You can run "lsmod" and look at the somewhat verbose output for i915 vs. vesa vs. fbdevhw to see what Ubuntu thinks it is using.

Jerry

---

### Post by Typhoid on 2011-02-03
> **jerrylamos said:**
> In the /etc/X11/xorg.conf example above replace "vesa" with "i915" and give it a go.  With no xorg.conf it "should" default to intel's i915.

You can run "lsmod" and look at the somewhat verbose output for i915 vs. vesa vs. fbdevhw to see what Ubuntu thinks it is using.

Jerry
Apparently, the system thinks it's using vesa, fbmod, and i915 all at the same time. In xorg.conf, it's using fbmod, in compiz-check, it's using vesa, and in lsmod, it's using i915. I've deleted xorg.conf, as I couldn't edit it as it was read-only. In lsmod, of those drivers it only seems to be using i915, there's no sign of fbmod or vesa. Shouldn't that mean that Compiz is good to use? But compiz-check still shows I'm using vesa! Should I ignore what compiz-check is saying? BTW, why is the driver called i915 if my card is 945? I ran```
glxgears
```and the 3D is fine, at 45 FPS.

---

### Post by Typhoid on 2011-02-03
I ran```
modinfo vesa
```and it gave me```
ERROR: modinfo: could  not find module vesa
```then I ran```
modinfo fbdev
```which  then gave me```
ERROR: modinfo: could not find module fbmod
```That  should mean that vesa and fbdev are not being used. then I  ran```
modinfo i915
```which gave me```

filename:       /lib/modules/2.6.38-1-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     763F3845B25892B66E1981E
alias:          pci:v00008086d0000010Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000126sv*sd*bc03sc*i*
alias:          pci:v00008086d00000116sv*sd*bc03sc*i*
alias:          pci:v00008086d00000106sv*sd*bc03sc*i*
alias:          pci:v00008086d00000122sv*sd*bc03sc*i*
alias:          pci:v00008086d00000112sv*sd*bc03sc*i*
alias:          pci:v00008086d00000102sv*sd*bc03sc*i*
alias:          pci:v00008086d00000046sv*sd*bc03sc*i*
alias:          pci:v00008086d00000042sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A011sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A001sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E92sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E32sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E22sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E02sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A02sv*sd*bc03sc*i*
alias:          pci:v00008086d000029D2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029C2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029B2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002992sv*sd*bc03sc*i*
alias:          pci:v00008086d00002982sv*sd*bc03sc*i*
alias:          pci:v00008086d00002972sv*sd*bc03sc*i*
alias:          pci:v00008086d000027AEsv*sd*bc03sc*i*
alias:          pci:v00008086d000027A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002772sv*sd*bc03sc*i*
alias:          pci:v00008086d00002592sv*sd*bc03sc*i*
alias:          pci:v00008086d0000258Asv*sd*bc03sc*i*
alias:          pci:v00008086d00002582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002572sv*sd*bc03sc*i*
alias:          pci:v00008086d0000358Esv*sd*bc03sc*i*
alias:          pci:v00008086d00003582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002562sv*sd*bc03sc*i*
alias:          pci:v00008086d00003577sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,video,i2c-algo-bit
vermagic:       2.6.38-1-generic SMP mod_unload modversions 686 
parm:           modeset:int
parm:           fbpercrtc:int
parm:           powersave:int
parm:           lvds_downclock:int
parm:           lvds_use_ssc:int
parm:           reset:bool

```Shouldn't that mean that everything's fine? But it's not fine! And compiz-check is still showing me```

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   Unknown
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

```Note that the rendering method AIGLX is in use. Now consider this fragment from the Wikipedia on Compiz:> Initially, Compiz only worked with 3D hardware which was supported by Xgl. Most [NVIDIA]("http://en.wikipedia.org/wiki/NVIDIA") and [ATI]("http://en.wikipedia.org/wiki/ATI_Technologies") graphics cards are known to work with Compiz on Xgl. Since May 22, 2006 Compiz works on the standard [X.Org Server]("http://en.wikipedia.org/wiki/X.Org_Server"), by using [AIGLX]("http://en.wikipedia.org/wiki/AIGLX"). Besides the [Intel GMA]("http://en.wikipedia.org/wiki/Intel_GMA") graphics cards, AIGLX also supports using the ATI graphics cards (including [R300]("http://en.wikipedia.org/wiki/R300"), R400 and R500 cards) using the open-source radeon driver which supports GLX_EXT_texture_from_pixmap since fall 2006.
 NVIDIA's binary drivers (since Version [1.0-9629]("http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html")) support GLX_EXT_texture_from_pixmap on standard X.Org server.
[ATI]("http://en.wikipedia.org/wiki/ATI")/[AMD]("http://en.wikipedia.org/wiki/AMD")'s binary drivers do since version 8.42.[[3]]("http://en.wikipedia.org/wiki/Compiz#cite_note-2")


---

### Post by cariboo on 2011-02-03
I would suggest you remove your /etc/X11/xorg.conf, as the Intel driver doesn't need one. Once you've removed it, reboot, and check whether you are using the correct driver.

---

### Post by Typhoid on 2011-02-03
> **cariboo907 said:**
> I would suggest you remove your /etc/X11/xorg.conf, as the Intel driver doesn't need one. Once you've removed it, reboot, and check whether you are using the correct driver.
I removed xorg.conf, rebooted. lsmod still shows i915, and compiz-check still shows vesa. According to everything except for compiz-check, I have the correct drivers, and compiz should work. Except it doesn't.

---

### Post by cariboo on 2011-02-03
Is the vesa driver loaded when you check lsmod? You may have to blacklist the vesa driver if it is still loading. You can add it to the bottom of /etc.modeprobe.d/blacklist.conf

---

### Post by Typhoid on 2011-02-03
> **cariboo907 said:**
> Is the vesa driver loaded when you check lsmod? You may have to blacklist the vesa driver if it is still loading. You can add it to the bottom of /etc.modeprobe.d/blacklist.conf
I have blacklisted vesa, but that was futile. Whenever I log into the regular desktop session, I am bombarded with error messages, including: "System program problem detected", "Compiz has crashed", and "unity-panel-service has crashed". The system is more or less normal in the classic desktop (no effects) session, however, the sound doesn't work. I did a lot of sound troubleshooting, which didn't work. I would now like to completely reinstall Natty. Can anyone give me advice on how I should do this?

---

### Post by cariboo on 2011-02-03
I get the same crashes on occasion, and I've had to use:

```
unity --reset
```

a couple of times, but  generally the system seems fairly stable once it gets over the initial crashes. :)

---

### Post by Typhoid on 2011-02-03
I have decided to _completely_ reinstall Natty Narwhal. How should I do that?

---

### Post by cariboo on 2011-02-03
I'd suggest you use the latest daily live CD available [here]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by arpanaut on 2011-02-03
If I were you, I would wait until Alpha2 is announced later today, then download the iso and do a fresh install using your existing natty partitions.  BACK-UP YOUR IMPORTANT DATA IN YOUR HOME FIRST.

In the meantime, a new Intel driver just came down the pipe, so you might want to upgrade through synaptic package manager and see if that works.  Be aware of what might be removed and act accordingly.

---

### Post by Harry33 on 2011-02-03
> **arpanaut said:**
> If I were you, I would wait until Alpha2 is announced later today, then download the iso and do a fresh install using your existing natty partitions.  BACK-UP YOUR IMPORTANT DATA IN YOUR HOME FIRST.

In the meantime, a new Intel driver just came down the pipe, so you might want to upgrade through synaptic package manager and see if that works.  Be aware of what might be removed and act accordingly.

Natty-alfa2 is already here:
[http://cdimage.ubuntu.com/releases/natty/alpha-2/](http://cdimage.ubuntu.com/releases/natty/alpha-2/)
But it will get upgrades and bug fixes all the time, so it is not so important which daily ISO is used anyway.

---

### Post by Harry33 on 2011-02-03
> **Typhoid said:**
> 
...
Also, I don' know why, but the file that's supposed to be called "xorg.conf" is actually called (for me) "xorg.conf.failsafe. Anyway, here it is:
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
...


Now that file surely is xorg.conf.failsafe (not xorg.conf) and it should be too.
You see that file is supposed to be used when default driver (in this case xserver-xorg-video-intel) is not working. Do not delete that file.
You can select "fail safe" session if you start Ubuntu's recovery mode.
"Fail safe" is one of the options you can choose from.

So if you do not have xorg.conf file in the folder /etc/X11/,
no problem, you should not have it (when you use open source drivers like intel).

---

### Post by arpanaut on 2011-02-03
Ah, I see what you mean. I just thought that the "Official" Alpha2 would be less of a moving target for the OP. 
Guess I was wrong.
Good Luck Typhoid!

---

### Post by Typhoid on 2011-02-03
I have a netbook (which doesn't have a CD drive), so is it alright to just install using a USB Drive?

---

### Post by Harry33 on 2011-02-03
> **Typhoid said:**
> I have a netbook (which doesn't have a CD drive), so is it alright to just install using a USB Drive?

Yes it is not only alright, it is the better and faster way.
No need to burn Cd-disks, not even RW ones.
USB-ISO installation is the fastest way to install, I always use that.

---

### Post by Typhoid on 2011-02-03
Three questions:

-What is a daily build?

-What will be the difference between Natty desktop and Netbook?

-Can I get a Netbook version of Natty Narwhal Alpha 2?

---

### Post by Harry33 on 2011-02-03
> **Typhoid said:**
> Three questions:
-What is a daily build?
...


Daily build is just the same kind of snapshot as the alfa2 release is.
It is just that it contains all updates up to date.

Here is latest now:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by cariboo on 2011-02-03
> **Typhoid said:**
> Three questions:

-What is a daily build?

-What will be the difference between Natty desktop and Netbook?

-Can I get a Netbook version of Natty Narwhal Alpha 2?

There is no Netbook version of Natty, there are some optimizations for them, but the Desktop and the Netbook versions use the same iso.

---

### Post by Typhoid on 2011-02-03
What's the warning "Do not install Ubuntu 11.04 developer on a production machine" before installing Natty? What does it mean?

---

### Post by cariboo on 2011-02-03
Yes.

---

### Post by Typhoid on 2011-02-03
> **cariboo907 said:**
> Yes.
I'm asking what the definition of "production machine" is.

---

### Post by coffeecat on 2011-02-03
> **Typhoid said:**
> I'm asking what the definition of "production machine" is.

A machine where you do your day-to-day work. What they're saying is not to risk your data and routine work/play files by using them in a pre-release version, which is what Natty is at now. I can't find the link atm, but somewhere the Ubuntu team recommend that you install a pre-release only to a spare machine or a spare partition.

The point of running a pre-release version of Ubuntu is for experienced (and adventurous) users to test it to help the development team by finding bugs. No, I'll rephrase that. The point of running a pre-release version of Ubuntu is for experienced (and adventurous) users to **have fun**, and **then** to help, etc, etc, etc. :) The alphas and betas are provided for people to test, not to be ahead of the game.

---

### Post by Typhoid on 2011-02-03
Is there a USB Drive creator than can run on Linux? Because all of the USB Drive creators I've seen run on Windows only.

---

### Post by cariboo on 2011-02-03
> **Typhoid said:**
> I'm asking what the definition of "production machine" is.

I answered your question before you edited it.

> Is there a USB Drive creator than can run on Linux? Because all of the USB Drive creators I've seen run on Windows only.

Startup Disk Creator has been installed by default for at least the last three versions, unetbootin is in the repositories. The Startup Disk Creator is only good for creating usb drives with Ubuntu, unetbootin will allow you to use any iso to create a usb drive.

---

### Post by Typhoid on 2011-02-03
> **cariboo907 said:**
> I answered your question before you edited it.



Startup Disk Creator has been installed by default for at least the last three versions, unetbootin is in the repositories. The Startup Disk Creator is only good for creating usb drives with Ubuntu, unetbootin will allow you to use any iso to create a usb drive.
Thanks a lot.

---

### Post by Typhoid on 2011-02-04
I will now reinstall Natty Narwhal and see if it works.

---

### Post by Typhoid on 2011-02-04
I have reinstalled Natty Narwhal Alpha 2. It seems to work fine, except that sometimes Unity crashes and the keyboard stops working (which means I can't start Terminal, even with Ctrl+Alt+T) forcing me to reboot. This happens whenever I disable or enable a plugin in Compiz, or when I start an email client (thunderbird, evolution). There may be more causes which I haven't come across. I will file a bug report in launchpad. Any suggestions as to how I can prevent this from happening?

---

