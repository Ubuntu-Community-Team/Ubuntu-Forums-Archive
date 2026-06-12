---
title: "New Linux headers crashed my desktop"
date: 2010-11-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-11-20
I installed version 5 of the 2.6.37 kernel a day or so ago and apart from the odd disappearing windows borders and minimize/maximize buttons, all was well. I have been using my Natty installation all the time for the last couple of weeks. 
However, just before going for a snooze I noticed new Linux headers were available (still version 5 though) so I installed them. Oh dear! Compiz now uses 100% of one processor and the desktop locks up. The cursor moves and conky updates, but everything else is unusable :-(
I rebooted with reisub and chose the version 4 kernel and that's the same.
I am posting from my Maverick install. It's been a while since I've needed to use it :-)
What happened? What do the Linux headers do, when they are the same number that I already had?
Anyone else suffering similar?

---

### Post by Quackers on 2010-11-20
Update
It's usable (without windows borders and max/min buttons) unless you try metacity --replace or compiz --replace or try to enable desktop effects, then it freezes up and not even system monitor can be started. Cairo dock doesn't work fully either - it displays in a black rectangular background, rather than what is set. Presumably that would be solved if desktop effects could be enabled.

---

### Post by dino99 on 2010-11-20
just checked for updates and see that 2.6.37-5.14 available, so i've checked it to upgrade: when it want to rebuilt grub.cfg it completly freeze when it find an other distro/partition.

Will force the upgrade dialog box to close and see what happen.

---

### Post by Quackers on 2010-11-20
Yes, that's the one I'm having problems with, but, curiously when I installed it there was no grub.cfg content.
I went in to gconf editor and changed the instances of usr/bin/compiz to usr/bin/metacity, so compiz doesn't start up now and I have windows borders and max/min buttons back, but whenever I try to start desktop effects things go badly :-).I've just run a few more updates but they were mainly X11 and xrandr. No change in problems as yet.
On another note does Alt+F2 still work for others? It hasn't worked for me in quite some time - in fact, I'm not sure it has worked in Natty at all.

---

### Post by autocrosser on 2010-11-20
Are you guys using x86 or x86-64? I'm on 64 bit--am downloading the -14 kernel & will report back....

---

### Post by Quackers on 2010-11-20
x86-64 here. hope yours goes better :-)

---

### Post by autocrosser on 2010-11-20
Well-I updated my Unity-testing install. Went without a hitch--not sure what happened to your install---I'm in the -14 kernel as I type this.  I'll update my regular install  that I test Gnome Shell with next......

---

### Post by Quackers on 2010-11-20
Ah that's good. I don't have Unity on here. Maybe I should :-)
Thanks for the feedback.

---

### Post by cariboo on 2010-11-20
I have the default setup on my home system, running the latest kernel update with no problems. I don't have gnome-shell or Unity on that system. I'm in the process of updating two other systems, one with unity and the other running gnome-shell.

---

### Post by autocrosser on 2010-11-20
OK--just updated the regular install--also went good. Desktop didn't show the Gnome-panel until I clicked somewhere....I'm at a loss what went wrong with yours.....Do you only have one install??

As for Unity---I'm starting to warm up to it--not sure if I like it better than Gnome-Shell, so I'm giving both equal time. If you want to try Unity, look at the threads & get the PPA info...It's working very well right now--I'm using AWN as my panel until more function is available.

---

### Post by Quackers on 2010-11-20
I only have one Natty install and to be honest, apart from one hiccup it's run ok.
I think my problem is due to a new nvidia-current which seems to have been ionstalled with the new Linux headers. That is conflicting with compiz I would guess. 
I have removed the Linux Headers and the nvidia-current update and now 11.04 won't boot at all :-) even on the older kernel. I'm trying to fix using the live cd and chroot. Will be in touch.
If the worst has happened and I need to re-install, it's no major problem. It may even be a benefit. It's purely a testing installation anyway, although I have been using it all the time for 2 weeks or so.
No biggy.
Thanks again for the feedback though :-)

---

### Post by cariboo on 2010-11-20
Both system came up OK here, I should add that Unity is running on a 32-bit system. The rest are 64-bit systems.

---

### Post by Quackers on 2010-11-20
Well I'm up and running again on version 4. I'll try updating again :-)

---

### Post by Quackers on 2010-11-20
Couldn't fix it well enough so I'm re-installing. Back later :-)

---

### Post by Harry33 on 2010-11-20
Could you please test new 6 series 2.6.37-6.15 kernel on Natty.
In my system (64-bit) it completely fails to load and ends up in busybox.
4 and 5 series like each one before that are OK.
Here:
[https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15](https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15)

---

### Post by Quackers on 2010-11-20
> **Harry33 said:**
> Could you please test new 6 series 2.6.37-6.15 kernel on Natty.
In my system (64-bit) it completely fails to load and ends up in busybox.
4 and 5 series like each one before that are OK.
Here:
[https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15](https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15)

I'm, still repairing my system from 2.6.37.5.14 
Give me a chance :D

---

### Post by Harry33 on 2010-11-20
> **Quackers said:**
> I'm, still repairing my system from 2.6.37.5.14 
Give me a chance :D

Sure, right on.
The 2.6.37-6.15 bugger did not mesh up my system.
I just removed it and now I am back to 2.6.37-5.14.

---

### Post by Quackers on 2010-11-20
The plot thickens!
I re-installed 10.10 then upgraded to 11.04 and things are still the same but I made a mistake. I used the wrong 10.10 disc and I now have 32 bit 11.04 which isn't working. That's both 32 bit and 64 bit systems both baulking with the 2.6.37.5.14 Linux headers in the same day.
Not good.
I have no windows borders or max/min buttons and when I try metacity --replace compiz uses 100% of one cpu and freezes everything. I daren't try compiz --replace!

---

### Post by Quackers on 2010-11-20
It's all very silly now.
I decided to re-install using the daily alternate cd (well dvd actually). ALl went well but it took a long time to install and I couldn't use the user name I wanted to. No problem I thought, I can create a new one later to go with the /home folder and partition I didn't format. Nope. Users and groups does not appear in the System > Admin menu. So now I have a user and home folder I don't want, but have to use, and I don't have the user I want to have which goes with the /home folder I want to use, which is available, but not to me as I don't own it.
I think I've wasted 6 hours. 
2.6.37.5.14 has not done me any favours. I still have some of the same problems now, and compiz isn't even installed in this new install.
It's all very messy.
I think I may have to retire from Natty :-)

---

### Post by autocrosser on 2010-11-20
If you are burned out right now---don't worry....wait until things settle out a bit. A1 is just around the corner & things "ought" to settle a bit by then....

Sorry 'bout the bad luck...it happens to all of us that tread this early in the cycle.....:D

I "generally" wait until A1 to do a install from testing---before that I use the last stable & do a sources.list update/upgrade--not quite as messy---but "just" ;)

---

### Post by Quackers on 2010-11-20
It's not that I'm burned out really (even though it's 4-25am here :-) ) I'm more perturbed that having saved older kernels as a safety net (I thought) and having booted into those kernels and had exactly the same problems it just seems like it was a waste of time, especially as those kernels worked fine before today's update.
If you think you've got a safety net and it turns out you haven't it sort of makes it a futile gesture to save them. Or so it seems.

---

### Post by wilee-nilee on 2010-11-20
> **Quackers said:**
> It's not that I'm burned out really (even though it's 4-25am here :-) ) I'm more perturbed that having saved older kernels as a safety net (I thought) and having booted into those kernels and had exactly the same problems it just seems like it was a waste of time, especially as those kernels worked fine before today's update.
If you think you've got a safety net and it turns out you haven't it sort of makes it a futile gesture to save them. Or so it seems.

I haven't been able to get a install in virtualbox or a sdhc card at all. I could only get a upgrade from Maverick that broke, but it's early in the dev. Loads to a thumb okay but with errors every time on running.

---

### Post by Quackers on 2010-11-20
> **wilee-nilee said:**
> I haven't been able to get a install in virtualbox or a sdhc card at all. I could only get a upgrade from Maverick that broke, but it's early in the dev. Loads to a thumb okay but with errors every time on running.

Oh that's not very nice! I sympathise :-)
To be honest I've been quite lucky I think. I upgraded from 10.10 and all 5 previous Linux headers/kernels worked more or less fine.
It just seems a bit silly that because of a new Linux header installed last night all the previous kernels stopped working as well. 2.6.37.4 was fine a couple of days ago and 2.6.37.5.13 was fine yesterday, so why installing 2.6.37.5.14 would goose all previous kernels as well seems to me to be a serious failing in the system. 
Maybe because I don't fully understand the kernel system and its updates I misunderstand these things. It just seems odd that a kernel that worked when it was last used should now have problems because of an update to a later kernel :o
I appreciate your input though guys :-)

---

### Post by dino99 on 2010-11-21
might need this bug fixed to go ahead:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/675641](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/675641)

---

### Post by Quackers on 2010-11-21
Well, after re-installs and re-upgrades I've narrowed it down to the new nvidia-current driver or the 5.14 kernel, or a mixture of both. 
I've uninstalled compiz completely and then run metacity --replace in the terminal and that brought back windows borders and max/min buttons, but only for 2 seconds. Then compiz started using 100% of one cpu and about 10% of the second, so nothing else on the desktop was usable. I had to shut down and start again.
I re-installed compiz and tried compiz --replace and that just pegged the cpu again and I had to shut down again.
If I try to enable desktop effects it pegs the cpu again.
Cairo dock is working but not displaying correctly.
All windows have no borders and no max/min/shutdown buttons.
Sometimes the windows list in the bottom panel won't even shutdown anything.
I have no choice but to wait for further developments :-)

---

### Post by Harry33 on 2010-11-22
> **Quackers said:**
> Well, after re-installs and re-upgrades I've narrowed it down to the new nvidia-current driver or the 5.14 kernel, or a mixture of both. 
I've uninstalled compiz completely and then run metacity --replace in the terminal and that brought back windows borders and max/min buttons, but only for 2 seconds. Then compiz started using 100% of one cpu and about 10% of the second, so nothing else on the desktop was usable. I had to shut down and start again.


Well I have found out that the kernel 2.6.37-6 is useless, however version 2.6.37-5 works fine in my systems. Also, nvidia-current has always worked well.
I am using right now the lates one: 260.19.21-0ubuntu1.

Window borders and buttons are handled by window managers.
So, it is mutter in gnome-shell, and metacity in gnome-panel.
If compiz is installed then it that is the window-manager.
It is possible that the fault lies in compiz.

I did not quite understand, when you wrote you uninstalled completely compiz and then compiz started using 100 % of one CPU. How come?

Please uninstall all compiz packages, also folders and files in the /home partition.
Reboot, then try metacity --replace.

---

### Post by RJARRRPCGP on 2010-11-22
> **Quackers said:**
> I installed version 5 of the 2.6.37 kernel a day or so ago and apart from the odd disappearing windows borders and minimize/maximize buttons, all was well. I have been using my Natty installation all the time for the last couple of weeks. 
However, just before going for a snooze I noticed new Linux headers were available (still version 5 though) so I installed them. Oh dear! Compiz now uses 100% of one processor and the desktop locks up. The cursor moves and conky updates, but everything else is unusable :-(
I rebooted with reisub and chose the version 4 kernel and that's the same.
I am posting from my Maverick install. It's been a while since I've needed to use it :-)
What happened? What do the Linux headers do, when they are the same number that I already had?
Anyone else suffering similar?

Is your graphics hardware Nvidia and did you check the XOrg log file for any signs of the glx library getting messed up? 

=> Specifically, if X.Org is telling you it's using the glx extension from X.Org instead of Nvidia. 

And is glxinfo reporting the software rasterizer being used?

---

### Post by Quackers on 2010-11-22
> **Harry33 said:**
> 

I did not quite understand, when you wrote you uninstalled completely compiz and then compiz started using 100 % of one CPU. How come?

Please uninstall all compiz packages, also folders and files in the /home partition.
Reboot, then try metacity --replace.

Me too, Harry! That wasn't a typo! I will try your suggestion again later, But to be honest rebooting can be a bit of a lottery too :-)

RJARRRPCGP

Yes my graphics card is nvidia 8600M GT 
Xorg.0.log shows
```
[    25.528] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    25.528] (II) Loading sub module "ramdac"
[    25.528] (II) LoadModule: "ramdac"
[    25.528] (II) Module "ramdac" already built-in
[    25.528] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    25.528] (==) NVIDIA(0): RGB weight 888
[    25.528] (==) NVIDIA(0): Default visual is TrueColor
[    25.528] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.528] (**) NVIDIA(0): Option "NoLogo" "True"
[    25.528] (**) NVIDIA(0): Enabling RENDER acceleration
[    25.528] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    25.528] (II) NVIDIA(0):     enabled.
[    26.132] (II) NVIDIA(0): NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)
[    26.132] (--) NVIDIA(0): Memory: 524288 kBytes
[    26.132] (--) NVIDIA(0): VideoBIOS: 60.84.42.00.24
[    26.132] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    26.132] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    26.132] (--) NVIDIA(0): Connected display device(s) on GeForce 8600M GT at PCI:1:0:0:
[    26.132] (--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
[    26.132] (--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 330.0 MHz maximum pixel
[    26.132] (--) NVIDIA(0):     clock
[    26.132] (--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
[    26.149] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    26.149] (==) NVIDIA(0): 
[    26.149] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    26.149] (==) NVIDIA(0):     will be used as the requested mode.
[    26.149] (==) NVIDIA(0): 
[    26.149] (II) NVIDIA(0): Validated modes:
[    26.149] (II) NVIDIA(0):     "nvidia-auto-select"
[    26.149] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    27.167] (--) NVIDIA(0): DPI set to (152, 152); computed from "UseEdidDpi" X config
[    27.167] (--) NVIDIA(0):     option
[    27.167] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    27.167] (--) Depth 24 pixmap format is 32 bpp
[    27.173] (II) NVIDIA(0): Initialized GPU GART.
[    27.183] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    27.519] (II) Loading extension NV-GLX
[    27.578] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    27.596] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    27.596] (==) NVIDIA(0): Backing store disabled
[    27.596] (==) NVIDIA(0): Silken mouse enabled
[    27.603] (**) NVIDIA(0): DPMS enabled
[    27.603] (II) Loading extension NV-CONTROL
[    27.603] (==) RandR enabled
[    27.603] (II) Initializing built-in extension Generic Event Extension
[    27.603] (II) Initializing built-in extension SHAPE
[    27.603] (II) Initializing built-in extension MIT-SHM
[    27.603] (II) Initializing built-in extension XInputExtension
[    27.603] (II) Initializing built-in extension XTEST
[    27.603] (II) Initializing built-in extension BIG-REQUESTS
[    27.603] (II) Initializing built-in extension SYNC
[    27.604] (II) Initializing built-in extension XKEYBOARD
[    27.604] (II) Initializing built-in extension XC-MISC
[    27.604] (II) Initializing built-in extension SECURITY
[    27.604] (II) Initializing built-in extension XINERAMA
[    27.604] (II) Initializing built-in extension XFIXES
[    27.604] (II) Initializing built-in extension RENDER
[    27.604] (II) Initializing built-in extension RANDR
[    27.604] (II) Initializing built-in extension COMPOSITE
[    27.604] (II) Initializing built-in extension DAMAGE
[    27.604] (II) Initializing built-in extension GESTURE
[    27.604] (II) Initializing extension GLX
```
but not too sure what it means!
Xorg.1.log shows
```
[    23.660] (--) NV: Found NVIDIA GeForce 8600M GT at 01@00:00:0
[    23.661] (EE) NV: Kernel modesetting driver in use, refusing to load
[    23.661] (EE) No devices detected.
[    23.661] 
Fatal server error:
[    23.661] no screens found
[    23.661] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    23.661] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    23.661]
```
right at the end, which is not great, I think.  And Xorg.2.log ends in a similar way.

Actually I've just seen this in Xorg.1.log
```
  23.651] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.651] (II) Module dbe: vendor="X.Org Foundation"
[    23.651] 	compiled for 1.9.0.902, module version = 1.0.0
[    23.651] 	Module class: X.Org Server Extension
[    23.651] 	ABI class: X.Org Server Extension, version 4.0
[    23.651] (II) Loading extension DOUBLE-BUFFER
[    23.651] (II) LoadModule: "glx"
[    23.651] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.651] (II) Module glx: vendor="X.Org Foundation"
[    23.651] 	compiled for 1.9.0.902, module version = 1.0.0
[    23.651] 	ABI class: X.Org Server Extension, version 4.0
[    23.651] (==) AIGLX enabled
[    23.651] (II) Loading extension GLX
[    23.651] (II) LoadModule: "record"
[    23.652] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.652] (II) Module record: vendor="X.Org Foundation"
[    23.652] 	compiled for 1.9.0.902, module version = 1.13.0
[    23.652] 	Module class: X.Org Server Extension
```
Does that mean anything to you?
Thanks for the help :-)

---

### Post by Quackers on 2010-11-22
Ok, I've completely deleted compiz - screenshot 1.
My windows have no max/min/close buttons - like before. If I run metacity --replace in a terminal I get them back ot 2) but as soon as I close the terminal the top bar disappears, but leaves a space where it was. Then everything in the bottom panel disappears, so I can't close any screens or move anything around. Basically unusable again :-)

---

### Post by Harry33 on 2010-11-22
> **Quackers said:**
> Ok, I've completely deleted compiz - screenshot 1.
My windows have no max/min/close buttons - like before. If I run metacity --replace in a terminal I get them back ot 2) but as soon as I close the terminal the top bar disappears, but leaves a space where it was. Then everything in the bottom panel disappears, so I can't close any screens or move anything around. Basically unusable again :-)

Yes using terminal that happens, but use alt+F2 and then write the command metacity --replace there.
The reboot.

---

### Post by Harry33 on 2010-11-22
Also you may go into appearance properties and set "no desktop effects" from there.

---

### Post by Quackers on 2010-11-22
Alt+F2 hasn't worked at all since the new headers were installed. So I entered metacity --replace in the Startup Applications and that worked.
Sadly, I then re-installed compiz and now on every boot compiz pegs one of the cpu's at 100%.
I've chrooted into the system from the live cd and removed compiz and the plugins.
It now reports that compiz is not installed. However on rebooting the cpu is still pegged at 100% and --- nothing, and I mean nothing, is clickable on the desktop.
Conky reports that compiz is the culprit. Sometimes the panels don't even load but when they do I can move the pointer and click on things but guess what! Yup, nothing happens.
My Natty install is now officially fubar. 
Even an older kernel doesn't boot any better.
Kaput! Finito! No more. I've suffered enough :-)
4 re-installs and 40 hours is enough to try and fix a dodgy update!
I'm back on Meerkat now, and I'm staying there :-)
Thanks for all help offered guys.

There are no desktop effects enabled.

---

### Post by Quackers on 2010-11-22
I had one last go :-)
I re-installed for the 5th time. I installed nothing apart from updates and conky. I didn't use my saved /home partition, I formatted that, just in case there was something in it that the kernel didn't like.
System rebooted after upgrading to 11.04 to a normal desktop. 
Any opened windows had no menu bar. I ran metacity --replace and the menu bar came back. So I used Startup Applications to create a metacity --replace command (because Alt+F2 still didn't work).
I rebooted and...........no panels, no menus, one cpu is pegged at 100% by compiz (or so conky says).
Nothing to click on, no menus, nothing. Absolutely useless.....again.
What a disaster this kernel has been! Not only has it fubar'd itself, but every other preceding kernel too! What a bonus!
I'm going for a sleep now.

---

### Post by Quackers on 2010-11-22
I'm back :-)
```
natty64@natty64-laptop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu natty (development branch)"

```
At first I had no wireless and some top panel icons were missing. I had no desktop effects enabled but wobbly windows worked. I have the menu bar on screens now and max/min/shutdown buttons - unless I unmaximize the screen which makes them disappear again.
On third reboot I got a wireless connection, but no icon for it in the top panel. I have a couple of other top panel applets missing still.
This is as stable as I've had this kernel running and I daren't do too much :-)

I re-installed 10.10 then updated until the upgrade appeared, when it offered me a Partial Upgrade - no thanks I said. So I went to Synaptic and checked each one manually, looking at what was being done with it - there were a lot of updates :-)
I did not select the nvidia updates at that time. 
So I ran all the updates and rebooted. No top bar on screens again and no borders to them either - just like before. So the problem almost certainly lies with the kernel, not the nvidia driver.
Strangely compiz is running fine! It doesn't like to shutdown on reboot though.
I have since installed the nvidia-current et all and things are still stable-ish.
My best effort so far it seems! Don't know why that is though.

---

### Post by autocrosser on 2010-11-22
Well--I do know that Compiz is being "modified" a bit to work nice with Unity, so that may have a fair amount to do with your problem. You might try the Unity PPA & see if that works for you...but you may not have a good downgrade path if it is a problem......

If a USB stick works for you that might be the best test path.

---

### Post by Quackers on 2010-11-22
I haven't had any kind of downgrade path for a few days :-)
I'm not using Unity yet (using desktop version).

I rebooted a while ago and only one panel item returned and no wireless connection at all. If I reboot again it happens again, unless I connect an ethernet cable. Then all the panel items return and after the initial ethernet connection I can disconnect the cable and wireless will take over! If I reboot then without the cable, all the panel icons disappear and I have no internet connection! Lol.

---

### Post by autocrosser on 2010-11-23
" ain't test'n fun?" :D

Really, It's looking like you've had the dogs worst week...Got to say "welcome to the crowd"...We all have had days/weeks like that & suddenly a update will come along & its smooth sailing again....

Sounds like you are "kind'a" stable right now, so hang in there & keep your "progress" posted.

I'm waiting for the axe to fall on my Unity install...it's just crashing if I edit/restart Conky or look cross-eyed at it for too long......bound to be some major breakage soon.....

---

### Post by Quackers on 2010-11-23
Lol, I know what you mean :-)
I'm waiting for a new kernel before I do anything else!

---

### Post by Quackers on 2010-11-24
Update
Installed 2.6.37.6.17 and all the old problems are resolved :-)
One new one though :-) an update removed parts of evolution and they won't re-install due to dependencies problems. Oh well.

---

### Post by zika on 2010-11-24
> **Quackers said:**
> Update
Installed 2.6.37.6.17 and all the old problems are resolved :-)
One new one though :-) an update removed parts of evolution and they won't re-install due to dependencies problems. Oh well.Partial upgrade. Synaptick or UpdateMangler...? Aptitude and apt-get work OK... Evolution* waiting for upgrade...

---

### Post by Harry33 on 2010-11-24
Yeah some packages in evolution complex have changed their names:
libcamel1.2-19, libebook1.2-10, libecal1.2-8, libedata-book1.2-8, libedata-cal1.2-10, libedataserver1.2-14, libedataserverui1.2-1.
So old packages cannot be removed due to the dependencies of gnome-panel and gnome-control-center.

---

### Post by Quackers on 2010-11-24
Hmm, so evolution is unusable due to it being removed. You can't re-install it due to dependencies. Fantastic :-) Thunderbird here I come! 
My new Natty install is even worse! Most of the old problems are back and no evolution as well :-) even with the new kernel. Oh dear :-(

---

### Post by Quackers on 2010-11-24
Just had some evolution updates :-)  - still no good :-(
It really does seem to be a lottery booting this kernel. Sometimes there are no panel applets that I get error messages about. Sometimes no internet. Sometimes desktop effects are enabled and sometimes not :-) 
Still no Alt+F2 :-(
Ah well, it's a laugh :-)

---

### Post by Harry33 on 2010-11-24
New evolution-data-server (2.32) dependency problems:
It depends on libebook1.2-10 and libecal1.2-8 among others.

1) Gnome-control-center (2.32.1) depends on libebook1.2-9
But new libebook1.2-10 replaces libebook1.2-9.
 
2) Gnome-panel (2.32.1) depends on libecal1.2-7
But new libecal1.2-8 replaces libecal1.2-7.

So we have to wait new gnome-control-center and gnome-panel flavours with renewed dependencies.

---

### Post by Quackers on 2010-11-24
Thanks for that Harry33. How do you find out this stuff? :-)

---

### Post by Harry33 on 2010-11-24
> **Quackers said:**
> Thanks for that Harry33. How do you find out this stuff? :-)

You may use Synaptic for that. Just click once on the package you are interested in. Then click the "Properties" button and "Dependencies" tab there.

Or you can go to launchpad, the evolution-data-server 2.32 page is here (64 bit):
Then click any of those binary packages to see more info, like dependencies.

BTW. I did install the evolution-data-server packages. That went fine, some packages got upgraded, but now I have old and new versions of some packages installed.
I have removed evolution from my system in favor of thunderbird, so I did not have any other issues.
Due to gnome-panel and gnome-control-center dependencies I cannot get rid of the data-server stuff.

---

### Post by Harry33 on 2010-11-24
> **Quackers said:**
> Thanks for that Harry33. How do you find out this stuff? :-)

You may use Synaptic for that. Just click once on the package you are interested in. Then click the "Properties" button and "Dependencies" tab there.

Or you can go to launchpad, the evolution-data-server 2.32 page is here (64 bit):
Then click any of those binary packages to see more info, like dependencies.

BTW. I did install the evolution-data-server packages. That went fine, some packages got upgraded, but now I have old and new versions of some packages installed.
I have removed evolution from my system in favor of thunderbird, so I did not have any other issues.
Due to gnome-panel and gnome-control-center dependencies I cannot get rid of the data-server stuff.

---

### Post by Harry33 on 2010-11-24
You may use Synaptic for that. Just click once on the package you are interested in. Then click the "Properties" button and "Dependencies" tab there.

Or you can go to launchpad, the evolution-data-server 2.32 page is here (64 bit):
Then click any of those binary packages to see more info, like dependencies.

BTW. I did install the evolution-data-server packages. That went fine, some packages got upgraded, but now I have old and new versions of some packages installed.
I have removed evolution from my system in favor of thunderbird, so I did not have any other issues.
Due to gnome-panel and gnome-control-center dependencies I cannot get rid of the data-server stuff.

---

### Post by Harry33 on 2010-11-24
Aargh, sorry for the triple post. Something wrong with the server upstreams.

---

### Post by cariboo on 2010-11-24
@Harry33, I removed the extra posts.

---

### Post by Quackers on 2010-11-24
Thanks for that info Harry33
I have another update :-)
A few more updates have been run but after running them Synaptic still wouldn't let me re-install evolution due to dependency issues.
But Software Centre did allow the installation of evolution - and it's running fine! I just got my emails for the last few hours.

Also it seems the more I boot this new kernel (6.17) the more stable it gets! 
My last couple of reboots have been much happier. Only one missing applet that on clicking the reload button in the error message loads up the network manager applet fine. That didn't happen before - they just wouldn't reload.

Alt + F2 still doesn't do anything so I loaded the Run Application Applet in  Startup Applications to at least get the use of it.

---

