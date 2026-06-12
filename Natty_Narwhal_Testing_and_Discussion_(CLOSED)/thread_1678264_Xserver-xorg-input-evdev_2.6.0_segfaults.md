---
title: "Xserver-xorg-input-evdev 2.6.0 segfaults"
date: 2011-01-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Aterus on 2011-01-29
Just upgraded to 11.04 Alpha to get my hands on a bit of bug tracking work and got a completely dead system.

Upon boot the system goes past the logo stage and then goes in to a non-ending loop. The screen becomes black, then a quick flash of some command lines, which is followed by screen going black again, then the command lines... And this goes on forever.

Has anyone else came across the same problem?

---

### Post by MasterNetra on 2011-01-29
> **Aterus said:**
> Just upgraded to 11.04 Alpha to get my hands on a bit of bug tracking work and got a completely dead system.

Upon boot the system goes past the logo stage and then goes in to a non-ending loop. The screen becomes black, then a quick flash of some command lines, which is followed by screen going black again, then the command lines... And this goes on forever.

Has anyone else came across the same problem?

Not me, but that said I've always done fresh installs. I've never trusted upgrading.

---

### Post by Aterus on 2011-01-29
When dealing with a fresh install, is all the information kept in home directory? Files are the obvious case, but what about things like bookmarks? It seems i may need to resort to a fresh install or a downgrade (if possible).

---

### Post by isaacahloe on 2011-01-29
you aren't alone, same here

---

### Post by Aterus on 2011-01-29
I'd love to give more detail on the obvious bug, but unless there is an output file lying somewhere on the HDD, the screen flashes too quick to read it.

---

### Post by Aterus on 2011-01-29
[isaacahloe]("http://ubuntuforums.org/member.php?u=842826") - did you an upgrade or a fresh install?

---

### Post by sgage on 2011-01-29
I experienced something similar. What graphics drivers are you using? I was able to boot into recovery mode, "failsafe graphics", and reverted my graphics from nvidia-current to nouveau. That seemed to fix it. Maybe something to do with the new kernel and the nvidia drivers? I will try re-installing nvidia-current later and see what happens.

---

### Post by Gladk on 2011-01-29
The same for me. But I use 11.04 about 1.5 months, the last update made my Dell Mini 10 unbootable.

---

### Post by Gladk on 2011-01-29
The problem was with wireless mouse. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/709664](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/709664)

Unplugging the mouse "solved" the problem for the moment.

---

### Post by Harry33 on 2011-01-29
> **Gladk said:**
> The same for me. But I use 11.04 about 1.5 months, the last update made my Dell Mini 10 unbootable.

I am quite sure the problem is the new xserver-xorg-input-evdev (2.6.0-1ubuntu1) drivers. This update showed up today earlier.
The issue is that it seems to work only with xserver 1.10 (not with xserver 1.9 series).
And that xserver does not exist yet in ubuntu repos.
So downgrade the evdev 2.6.0 to the version 2.3.2.
Here:
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1](https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1)

---

### Post by jerrylamos on 2011-01-29
> **Harry33 said:**
> I am quite sure the problem is the new xserver-xorg-input-evdev (2.6.0-1ubuntu1) drivers. This update showed up today earlier.
The issue is that it seems to work only with xserver 1.10 (not with xserver 1.9 series).
And that xserver does not exist yet in ubuntu repos.
So downgrade the evdev 2.6.0 to the version 2.3.2.
Here:
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1](https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1)
Harry33, 

Sure acts like xserver breakage here.  Intel N10 integrated video graphics on new netbook.  Boot was so dead after aptitude "safe-upgrade" (Ha!) there's not even any evidence on the logs that I could see.  Recovery mode works up to the text screen menu but starting gdm was instant death.

I downgraded by re-installing from the latest CD live which is 27 January.  For me, re-install is a standard Alpha & Beta procedure.

Hmm, CD daily build hasn't been updated for the last couple days, which is indicative that a newer build isn't ready yet.

Jerry

---

### Post by Harry33 on 2011-01-29
> **jerrylamos said:**
> Harry33, 

Sure acts like xserver breakage here.  Intel N10 integrated video graphics on new netbook.  Boot was so dead after aptitude "safe-upgrade" (Ha!) there's not even any evidence on the logs that I could see.  Recovery mode works up to the text screen menu but starting gdm was instant death.

I downgraded by re-installing from the latest CD live which is 27 January.  For me, re-install is a standard Alpha & Beta procedure.

Hmm, CD daily build hasn't been updated for the last couple days, which is indicative that a newer build isn't ready yet.

Jerry

Yes the xserver-xorg-input-evdev(2.6.0) leads to xserver breakage (segfaulting) with xserver 1.9 series.
This has been tested now also with vanilla evdev 2.6.0 in Linux Arch.

People experiencing this can solve this by downloading the previous xserver-xorg-input-evdev (2.3.2) from Launchpad (my previous post shows the direct link).
No need to reinstall system.
If you have only one PC and it cannot boot, you can use
```
wget www.**
```
command from terminal.
Then after downloading the file, go to the same folder and run this
```
sudo dpkg -i xserver-xorg-input-evdev_***

```
 (put the exact file name into the link).

And then just reboot the system.

---

### Post by donniezazen on 2011-01-29
> **Gladk said:**
> The problem was with wireless mouse. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/709664](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/709664)

Unplugging the mouse "solved" the problem for the moment.

Thanks it solved my problem.

---

### Post by donniezazen on 2011-01-29
> **Harry33 said:**
> Yes the xserver-xorg-input-evdev(2.6.0) leads to xserver breakage (segfaulting) with xserver 1.9 series.
This has been tested now also with vanilla evdev 2.6.0 in Linux Arch.

People experiencing this can solve this by downloading the previous xserver-xorg-input-evdev (2.3.2) from Launchpad (my previous post shows the direct link).
No need to reinstall system.
If you have only one PC and it cannot boot, you can use
```
wget www.**
```
command from terminal.
Then after downloading the file, go to the same folder and run this
```
sudo dpkg -i xserver-xorg-input-evdev_***

```
 (put the exact file name into the link).

And then just reboot the system.

Thanks worked like a charm.

---

### Post by Aterus on 2011-01-29
using the dpkg method did not work for me. It kept getting and error message. I went around it by installing the xserver-edge package. Will tell if it worked after a reboot.

---

### Post by paul_in_london on 2011-01-29
> **Harry33 said:**
> Yes the xserver-xorg-input-evdev(2.6.0) leads to xserver breakage (segfaulting) with xserver 1.9 series.
This has been tested now also with vanilla evdev 2.6.0 in Linux Arch.

People experiencing this can solve this by downloading the previous xserver-xorg-input-evdev (2.3.2) from Launchpad (my previous post shows the direct link).
No need to reinstall system.
If you have only one PC and it cannot boot, you can use
```
wget www.**
```
command from terminal.
Then after downloading the file, go to the same folder and run this
```
sudo dpkg -i xserver-xorg-input-evdev_***

```
 (put the exact file name into the link).

And then just reboot the system.

Yes, I was bitten by this as well. Thanks for the workaround.

---

### Post by mc4man on 2011-01-29
> the xserver-xorg-input-evdev(2.6.0) leads to xserver breakage (segfaulting) with xserver 1.9 series.
Only on certain hardware, is fine here w/ latest update on desktop  and laptop ( though based on description don't see it being used here, just installed - 
edit: though can boot and use 2 mice on laptop at the same time

---

### Post by Harry33 on 2011-01-30
This issue has been confirmed to be severe in systems with Nvidia graphics card and nvidia-current binary driver and with xserver 1.9 series.
These systems will not boot to gdm with this evdev 2.6.0.
Also this has been confirmed to happen in Arch Linux as well.

It seems this new evdev only supports xserver 1.10.
I have tested it in Natty with xserver 1.10rc1 and it works well.

Here is a bug report #709977 ( a lot of dublicates too):
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/709977](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/709977)

---

### Post by dino99 on 2011-01-30
it seems i'm one of the lucky: no trouble here
generic-pae
xserver 1.9.0.902-1ubuntu4
input-evdev 2.6.0-1ubuntu1
nvidia 260.19.29-0ubuntu1

):P

sidenote: compiz not installed

---

### Post by Harry33 on 2011-01-30
> **dino99 said:**
> it seems i'm one of the lucky: no trouble here
generic-pae
xserver 1.9.0.902-1ubuntu4
input-evdev 2.6.0-1ubuntu1
nvidia 260.19.29-0ubuntu1
...


Dini99, what kernel are you using?
Do you see any issues if you unplug adn re-plug the mouse?

---

### Post by dino99 on 2011-01-30
> **Harry33 said:**
> Dini99, what kernel are you using?
Do you see any issues if you unplug adn re-plug the mouse?

kernel 38-1

unplug/plug mouse: nothing strange, all normal

note: i'm only updating from genuine natty repo (no ppa)natty-update, natty-security

---

### Post by mc4man on 2011-01-30
same here as dino - no issues w/ nvidia-current,  fully updated inc.  ....evdev on a desktop and laptop.
Includes using wired or wireless mouse, 2 mice on laptop at same time.
 
Ex. desktop -
> 21.107] (II) config/udev: Adding input device Microsoft Microsoft USB Wireless Mouse (/dev/input/event2)
[    21.107] (**) Microsoft Microsoft USB Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    21.107] (**) Microsoft Microsoft USB Wireless Mouse: always reports core events
[    21.107] (**) Microsoft Microsoft USB Wireless Mouse: Device: "/dev/input/event2"
[    21.107] (--) Microsoft Microsoft USB Wireless Mouse: Found 9 mouse buttons
[    21.107] (--) Microsoft Microsoft USB Wireless Mouse: Found scroll wheel(s)
[    21.107] (--) Microsoft Microsoft USB Wireless Mouse: Found relative axes
[    21.107] (--) Microsoft Microsoft USB Wireless Mouse: Found x and y relative axes
[    21.108] (II) Microsoft Microsoft USB Wireless Mouse: Configuring as mouse
[    21.108] (II) Microsoft Microsoft USB Wireless Mouse: Adding scrollwheel support
[    21.108] (**) Microsoft Microsoft USB Wireless Mouse: YAxisMapping: buttons 4 and 5
[    21.108] (**) Microsoft Microsoft USB Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.108] (II) XINPUT: Adding extended input device "Microsoft Microsoft USB Wireless Mouse" (type: MOUSE)
[    21.108] (**) Microsoft Microsoft USB Wireless Mouse: (accel) keeping acceleration scheme 1
[    21.108] (**) Microsoft Microsoft USB Wireless Mouse: (accel) acceleration profile 0
[    21.108] (**) Microsoft Microsoft USB Wireless Mouse: (accel) acceleration factor: 2.000
[    21.108] (**) Microsoft Microsoft USB Wireless Mouse: (accel) acceleration threshold: 4
[    21.108] (II) Microsoft Microsoft USB Wireless Mouse: initialized for relative axes.
[    21.108] (II) config/udev: Adding input device Microsoft Microsoft USB Wireless Mouse (/dev/input/mouse0)

Would think this only  affects certain hardware, not in general

---

### Post by dino99 on 2011-01-30
> **mc4man said:**
> same here as dino - no issues w/ nvidia-current,  fully updated inc.  ....evdev on a desktop and laptop.
Includes using wired or wireless mouse, 2 mice on laptop at same time.
 
Ex. desktop -


Would think this only  affects certain hardware, not in general

 64 bits only ?

---

### Post by mc4man on 2011-01-30
> 64 bits only ?
Have 32 bit here, will try a 64 bit install though in the bug report says this
> only amd64 is affected

---

### Post by mc4man on 2011-01-30
with a 1/30 amd_64 iso and nvidia-current no issue with a wireless or 2 mice at once
So i'd think this definitely affects a limited some, but not in general for most.

---

### Post by zika on 2011-01-30
> **mc4man said:**
> with a 1/30 amd_64 iso and nvidia-current no issue with a wireless or 2 mice at once
So i'd think this definitely affects a limited some, but not in general for most.
+1
[http://ubuntuforums.org/showpost.php?p=10411312&postcount=29](http://ubuntuforums.org/showpost.php?p=10411312&postcount=29)

---

### Post by mc4man on 2011-01-30
The one specific thing I did notice here - while plugging  a wireles into a laptop after boot also works fine, pulling it out is causing a logout. 
If that's not right, then for the moment I'd probably logout/pullout instead.

---

### Post by ronacc on 2011-01-30
it does seem to be hardware specific , I have no problems here with my amd64 install . xserver 1.9.0.902 and Nvidia 2.60.29 and xserver----evdev 1.2.6.0-1 .

---

### Post by Framli on 2011-01-30
Had it last night, solved with : 
```
wget https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1/+buildjob/2109048/+files/xserver-xorg-input-evdev_2.3.2-6ubuntu3b1_amd64.deb
sudo dpkg -i xserver-xorg-input-evdev_2.3.2-6ubuntu3b1_amd64.deb
```
(the link to a working deb is also in the bug comments, but last night, my first reaction was to launch Lynx (the cli web browser) and come here to find the faulty package to downgrade ;))

---

### Post by e-San on 2011-01-30
Hi there!
 
Today i made update of my packages (via Synaptics).
after that rebooted my os i found my scrren wont turn on.
i can see splash for a while and then blank, some red artifacts blinking and it seems to be death.
 
i can try everything, ctrl+alt+del, alt+FX - no response
i can hit 'off' button on my laptop, after that i can see splash and computer turnes off.
 
i can hit 'sleep' button - it goes then to sleep.
i can switch vlan on/off.
 
have no idea what to do. i tried:
removeing xfce4 (my default manager), installing wdm and setting it as default istead of gdm. tried to blacklist i915. removed Xorg.conf.
tried to boot old kernel.
tried to run 'failsafe' mode for graphical (from recovery console) - it goes back to menu.
 
none of those helped. 
do not have to mention that windos does work?
 
about my pc:
asus eeepc 900
intel gma 915
1GB, hdd 16gb, 
ubuntu 11.04
 
have no idea where to report it.
plase help!
 
Regards!

---

### Post by Uuranor on 2011-01-30
Hello everyone, I've got a very annoying problem since I installed the upgrade who brought the new kernel, where annoying means 'I can't use my ubuntu machine'.

After the selection of the desired kernel (both the new and the old one), my notebook does something with a purple screen for a while before turning black and stopping to work. To reboot the computer I have to press the power button of the computer.

Watching at the grub commands, the only options I see are i915.modeset=1 and vt.handoff=7. Deleting them and put something as nomodeset not only it doesn't help, but it writes on the screen 'error: unknown command "set"' for all the lines of the grub (so, also for setparams and so on). 

Any idea on how to restore Ubuntu?
I suspect it could depends on the fact my notebook has 2 videocards, the i915 and a radeon one (but I never been able to make the second one working).

Best regards,
Mat.

---

### Post by dino99 on 2011-01-30
seems to be a video driver issue or xserver : have you update them recently ? Do you have ppa entries into synaptics ? (if so deactivate those providing xserver/video packages, then update)

sudo rm /etc/X11/xorg.conf

then reboot

if it still fail, on next reboot, add nomodeset to the boot line, before "quiet splash" which can be removed (hold "shift" key down at end of bios process to unhide the grub menu)

---

### Post by Uuranor on 2011-01-30
Nevermind, it was a wireless mouse issue as documented in other thread.
If a moderator wants to close and delete this thread, I'll be thankful :)

Sorry for the inconvenience.

---

### Post by e-San on 2011-01-30
did you read my post?

---

### Post by Iowan on 2011-01-30
Moved to Natty Narwhal Testing and Discussion

---

### Post by e-San on 2011-01-30
been looking for this place, thanks!

system does not hangup, i can connect to it via ssh.
nomodeset wont help.

edit.
propably there is a problem with xserver-xorg-video-intel, but have no idea how to check/repair it.

---

### Post by inportb on 2011-01-30
It appears that you're looking at one of the recent problems with the Xorg transition. It might be useful to have a look at some of the other threads regarding this.

---

### Post by David D. on 2011-01-30
Thanks for the post Framli, this fixed the problem with my laptop.  It must be an AMD64 problem as I have ATI graphics.

---

### Post by Framli on 2011-01-30
There seems to be a problem on some hardware with latest xserver-xorg-input-evdev, you should try to downgrade it : [http://ubuntuforums.org/showthread.php?t=1678264&page=2](http://ubuntuforums.org/showthread.php?t=1678264&page=2)

---

### Post by gnomeuser on 2011-01-30
> **David D. said:**
> Thanks for the post Framli, this fixed the problem with my laptop.  It must be an AMD64 problem as I have ATI graphics.

AMD64, the issue is very easy to trigger here, I just have to connect the dongle for my wireless trackball or the one for the wireless keyboard and X goes black. Happens with Nouveau (+experimental) and the proprietary driver. I concur that this is not related to the videocard and solely seems to affect amd64 machines. I will confirm this later using my netbook.

---

### Post by cariboo on 2011-01-30
merged three threads on essentially the same subject.

---

### Post by Harry33 on 2011-01-30
> **mc4man said:**
> The one specific thing I did notice here - while plugging  a wireles into a laptop after boot also works fine, pulling it out is causing a logout. 
If that's not right, then for the moment I'd probably logout/pullout instead.

There is new version of xserver-xorg-input-evdev (2.6.0-1ubuntu2) available in order to
fix the bug #709977

```
Disable patch 101-gestures.patch - Fix SIGSEGV in xserver.
```

Let's test it.
Here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2)

---

### Post by e-San on 2011-01-30
> **Framli said:**
> Had it last night, solved with : 
```
wget https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.3.2-6ubuntu3b1/+buildjob/2109048/+files/xserver-xorg-input-evdev_2.3.2-6ubuntu3b1_amd64.deb
sudo dpkg -i xserver-xorg-input-evdev_2.3.2-6ubuntu3b1_amd64.deb
```
(the link to a working deb is also in the bug comments, but last night, my first reaction was to launch Lynx (the cli web browser) and come here to find the faulty package to downgrade ;))

Helpful for me!
Many thanks

cariboo907, you made huge mess. what is this for?

---

### Post by mc4man on 2011-01-30
> **Harry33 said:**
> There is new version of xserver-xorg-input-evdev (2.6.0-1ubuntu2) available in order to
fix the bug #709977

```
Disable patch 101-gestures.patch - Fix SIGSEGV in xserver.
```

Let's test it.


With that in place the one issue I had with pulling out the wireless is gone - no logout (crash
So hopefully that will fix where there are extended issues like crash on boot

---

### Post by ikt on 2011-01-30
> **Harry33 said:**
> Yes the xserver-xorg-input-evdev(2.6.0) leads to xserver breakage (segfaulting) with xserver 1.9 series.
This has been tested now also with vanilla evdev 2.6.0 in Linux Arch.

People experiencing this can solve this by downloading the previous xserver-xorg-input-evdev (2.3.2) from Launchpad (my previous post shows the direct link).
No need to reinstall system.
If you have only one PC and it cannot boot, you can use
```
wget www.**
```
command from terminal.
Then after downloading the file, go to the same folder and run this
```
sudo dpkg -i xserver-xorg-input-evdev_***

```
 (put the exact file name into the link).

And then just reboot the system.

fixed it, well done sir. :)

---

### Post by Harry33 on 2011-01-30
> **mc4man said:**
> With that in place the one issue I had with pulling out the wireless is gone - no logout (crash
So hopefully that will fix where there are extended issues like crash on boot

Yes I can now also confirm the new version 2.6.0-1ubuntu2 does fix this segfaulting issue as well.
Marking this thread as solved now.

---

### Post by Harry33 on 2011-01-30
The segfaulting issue is now fixed and the wotking version of
xserver-xorg-input-evdev (2.6.0-1ubuntu2) is already in Natty repos (main server).

Others may download it from here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2)

This was fixed:
```

Disable patch 101-gestures.patch - Fix SIGSEGV in xserver

```

---

### Post by cariboo on 2011-01-30
merged another one.

---

### Post by paul_in_london on 2011-01-30
> **Harry33 said:**
> The segfaulting issue is now fixed and the wotking version of
xserver-xorg-input-evdev (2.6.0-1ubuntu2) is already in Natty repos (main server).

Others may download it from here:
[https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/xserver-xorg-input-evdev/1:2.6.0-1ubuntu2)

This was fixed:
```

Disable patch 101-gestures.patch - Fix SIGSEGV in xserver

```

Confirmed fixed here with **xserver-xorg-input-evdev (2.6.0-1ubuntu2)**.

---

