---
title: "Yesterdays updates made ubuntu extremely unstable"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-08-21
Yesterday I installed new kernel, and other updates, it made ubuntu unstable. I installed some updates today, and it made it even worse.

So far randomly in past 24 hours:
1. GRUB appears and no countdown timer, have to press enter (sometimes boot normally). About 4 different kernels listed, although I think there should be only 2 as I thought I cleaned out old kernels a week ago.
2. ubuntu splash screen appears and never goes away. sometimes when booting lots of text rapidly goes on screen.
3. when/if it gets to desktop crash reporter (which seems to report crashes non stop for several months), today reported kernel crash.
4. today when updating it got part way through updating and stalled at gtk (see attachment). I think had to kill the process.
5. when browsing gmail firefox would freeze.
6. when browsing my 10.10 install (alpha2+updates?) from 10.10 daily liveusb, I can not access folders in /home directory. So if my install stops working no way to backup firefox profile and other folders because of permission issues.
I'm pretty sure when I installed 10.10 I didn't encrypt, and I remember with previous ubuntu versions you could always access data from liveusb. How do I get permission on liveusb to copy/paste from installed version?

I downloaded and ran liveusb of 20100820 but get kernel crash immediately after desktop appears (although desktop appears fine). But I noticed that no wireless connection available, sound was muted at startup (why hasn't that bug been fixed yet? it's been there for years). Just booted liveusb again and internet works and sound not muted. So that is weird.

Either way I've found 10.10 to be more unstable than others on a day to day basis with crash report icon always being on top right corner with random apps/services supposedly crashing.
This computer is used 99% for firefox.

Once I figure out how to backup data from install->liveusb->spare usb I will be installing daily to try and fix things, but doesn't look like it will fix much since liveusb has kernel crashes.

EDIT:
I tried the installer on liveusb and now there are only 3 steps?? 1. language 2. make sure plugged in, download updates while installing screen, non opensource option 3. install side by side, entire disk, manual partition : then click install. I stopped at that step since it says install (doesn't even ask for username/pass?)
This new installer so far is really bad if those are only steps available.

EDIT:
on installed 10.10 I had to input password to check for updates in update-manager (never had to in previous ubuntu releases). On liveusb of daily it did not ask for password. Was this fixed?

---

### Post by cariboo on 2010-08-21
Ubiquity seems to run hit or miss I tried it in a vm, I got to the partitioning section and it locked. Yesterday Live CD booted to the desktop, but no panels, and no icons on the desktop. I opened a terminal and started ubiquity from the command line, and did the complete install. It's still broken, give it a couple of days and try again.

---

### Post by andrewabc on 2010-08-21
I see shotwell is now installed by default, but they still have f-spot installed. Wonder when they are uninstalling f-spot?
[Shotwell 0.7 Released](http://www.yorba.org/blog/lucas/2010/08/shotwell-07-released.html) - hopefully they continue to update that app, as there are big improvements. Most important feature for this version is that it can import f-spot, which would be good for people updating.

Another crash I have had for several months is screenshot app crashes.

apps->accessories->take screenshot app->crashes. Had same problem 2 months ago. crash report is constantly saying it is crashing when trying to use it. Very reproduceable, and I assume others have same problem.


I am assuming my install is mostly hosed with lots of bad defaults from early alphas, so important thing is how to get privileges to backup data without booting into install? I am runing liveusb of daily and can browse my SSD 10.10 install, but can not access most folders in /home.

---

### Post by ranch hand on 2010-08-22
I have not installed since the A3 RC ISO.  Most of my installs are upgrades.

This one was upgraded from 9.04 to 9.10 testing and on from there, another was installed from 9.10A1 and on from there.  I am not having any problems with any installs.

Mine seem to be getting more stable.  Ah the vagaries of hardware in testing OS'.

---

### Post by andrewabc on 2010-08-22
I tried liveusb with storage space (to remember settings on restart), and I ended up with wallpaper and desktop icons loading, but no panels. Could move mouse and select icons, but within 10 seconds icon selection froze and left with only moving mouse. I ctrl+shift+f1 to get terminal. So that worked, but I manually power button off computer.

Looks like I will have to install 10.04.1 until things get sorted out. Too much time troubleshooting all the various problems. Still need to access (privileges) folders/data on 10.10 install though!

---

### Post by mc4man on 2010-08-22
> no way to backup firefox profile...
...but can not access most folders in /home.
Can't see why  you can't access most folders in your installed 10.10 from liveusb or livecd that aren't . files or folders

If overall  it's simply no access permissions then try, while on the live <whatever>, creating a new user.
Name it exactly the same as the username you use on the install you want to copy from, when done then logout and login in as that user. (logout, not restart

You then should have read permissions on everything in home dir. including all .<whatever> dir.'s and files such as .mozilla (and write also)

---

### Post by ranch hand on 2010-08-22
If he is using 10.04 I can believe there are problems.  I have file access problems there and the terminal doesn't work very well either.

Chroot scripts will not run.  Entering line by line works.  I thought the bash completion bug was fixed.  Frankly I have given up on 10.04.  Doesn't boot well, shut down does work now (thats nice, at least you can get out of it), Nautilus doesn't work right, Terminal doesn't work right.  The RC worked better than the up to date current 10.04 does.

If you want an OS that will work with 10.10 use 9.10.  The LTS is just a waste of time.

---

### Post by andrewabc on 2010-08-22
> **mc4man said:**
> Can't see why  you can't access most folders in your installed 10.10 from liveusb or livecd that aren't . files or folders

Can't access any . folders, and can not access a folder I created called 'Scan'.

> **mc4man said:**
> 
If overall  it's simply no access permissions then try, while on the live <whatever>, creating a new user.
Name it exactly the same as the username you use on the install you want to copy from, when done then logout and login in as that user. (logout, not restart

You then should have read permissions on everything in home dir. including all .<whatever> dir.'s and files such as .mozilla (and write also)
Thank you this worked perfectly. I am using 10.04.1 liveusb to do this.

> **ranch hand said:**
> If he is using 10.04 I can believe there are problems.  I have file access problems there and the terminal doesn't work very well either.

Chroot scripts will not run.  Entering line by line works.  I thought the bash completion bug was fixed.  Frankly I have given up on 10.04.  Doesn't boot well, shut down does work now (thats nice, at least you can get out of it), Nautilus doesn't work right, Terminal doesn't work right.  The RC worked better than the up to date current 10.04 does.

If you want an OS that will work with 10.10 use 9.10.  The LTS is just a waste of time.

It was 10.10 liveusb that would not access files. Although it seems to happen on 10.04.1 as well. 10.04 ran well on this old nettop, I upgraded to 10.10 testing because I put a SSD in it and 10.04 doesn't properly support SSD.

I agree that 10.04 was a letdown, mostly because they had to be safe, which meant out of date drivers/kernel. Hopefully they fix most problems with 10.10 as the updated kernel/drivers/software are good.

---

### Post by VMC on 2010-08-22
> **andrewabc said:**
> I tried liveusb with storage space (to remember settings on restart), and I ended up with wallpaper and desktop icons loading, but no panels. Could move mouse and select icons, but within 10 seconds icon selection froze and left with only moving mouse. I ctrl+shift+f1 to get terminal. So that worked, but I manually power button off computer.

Looks like I will have to install 10.04.1 until things get sorted out. Too much time troubleshooting all the various problems. Still need to access (privileges) folders/data on 10.10 install though!

Also try Ctrl+Alt+T , you should get a terminal from there. Instead of power off, try Alt+PrtScr+B.

---

### Post by andrewabc on 2010-08-22
I've installed 10.04.1 for now. Works fine.

I'll wait until beta release before installing again.

---

### Post by seeker5528 on 2010-08-23
> **andrewabc said:**
> I see shotwell is now installed by default, but they still have f-spot installed. Wonder when they are uninstalling f-spot?

Wha-a-a-a-a-t!?! :shock:

Due to quirks in dependency resolution there always seems to be something I nave to re-install after a distribution upgrade, but these are the exceptions rather than the rule. And there may be some minority of cases where lower level stuff should be uninstalled during an upgrade when the default has changed, also an exception rather than a rule.

At the application level in particular, if they decided to uninstall stuff just because it was decided something different should be included on the CD, that wouldn't be good at all.

Later, Seeker

---

### Post by andrewabc on 2010-08-23
> **seeker5528 said:**
> Wha-a-a-a-a-t!?! :shock:

Due to quirks in dependency resolution there always seems to be something I nave to re-install after a distribution upgrade, but these are the exceptions rather than the rule. And there may be some minority of cases where lower level stuff should be uninstalled during an upgrade when the default has changed, also an exception rather than a rule.

At the application level in particular, if they decided to uninstall stuff just because it was decided something different should be included on the CD, that wouldn't be good at all.

Later, Seeker

So I assume you were against GIMP being removed from default install?

Shotwell replaces f-spot pretty good from what I've seen and heard. There is no reason to have two photo managers installed at same time. That would be like having Transmission and Deluge both installed by default.

Unless you mean that people upgrading from 10.04 etc to 10.10 should not have f-spot removed, and it will not be. I meant it should be removed from the install cd as a default install since shotwell has replaced it.

---

### Post by seeker5528 on 2010-08-23
> **andrewabc said:**
> So I assume you were against GIMP being removed from default install?

I had no problem with that. Personally I'm likely to do a minimal install and add the stuff I want anyway, don't think generally speaking that the average user will care all that much either. 

It also doesn't seem like that big of an ordeal to me to run the live session from the DVD and install GIMP into the live session from the DVD in cases where there is no internet access or internet access is slow.  

> Unless you mean that people upgrading from 10.04 etc to 10.10 should not have f-spot removed, and it will not be. I meant it should be removed from the install cd as a default install since shotwell has replaced it.

To my way of thinking, when referring to the CD you should use included/not included, since you don't really have a choice there, you can install or uninstall things from the running live session, but that is a different thing. Installed would apply to what gets installed when you upgrade or do a new install, and uninstalled would only apply to things that get uninstalled when you upgrade. Maybe that's just me. ;)

F-spot is not on the [manifest](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.manifest) so I am assuming it stopped being included at the same time or very shortly after Shotwell was included, but I don't follow what's current on the installation medium at any given time, so couldn't say what the time frame really was.

EDIT: Gthumb seems like a saner choice to me, but that's a whole other discussion. 

Later, Seeker

---

### Post by Baul on 2010-08-24
Ref:  Sticky:    WARNING: X-server breakage coming soon to a computer near you

I have to say that once I got past that reinstall nvidia problem -  updating has been really smooth - perhaps it is a hardware problem?  

Then again I am a noobi - not dumb, just learning!  Not sure of all the issues.

However my upgrade path from Lucid to Maverick Alpha 3 - has been remarkably painless other than the above.

My machine is an AMD X2 4800+ cpu (socket 939) plus a Palit 9800GT graphics card - Maxtor hard-drive and 4gigs RAM.

---

### Post by stone1343 on 2010-08-25
> **cariboo907 said:**
> Ubiquity seems to run hit or miss I tried it in a vm, I got to the partitioning section and it locked. Yesterday Live CD booted to the desktop, but no panels, and no icons on the desktop. I opened a terminal and started ubiquity from the command line, and did the complete install. It's still broken, give it a couple of days and try again.

I've found this as well, once you fix syslinux.cfg, the install itself is more miss than hit. I've tried a bunch of different ISOs and only once actually got a running Maverick. Will be trying again in the next few days...

---

### Post by andrewabc on 2010-08-27
I have some serious problems with ubuntu now.

On my nettop, I had 10.10, but due to issues in this thread I installed 10.04.1 on it. I ended up having a new and worse issue: Constant suspending of the OS (or hibernate/sleep, not sure exactly which one you would define it as). Turn on computer, ubuntu is loading and before it gets to desktop it goes into sleep mode. Sometimes it makes it to loaded desktop and goes into suspend mode. I press power button to bring out of suspend mode and asks for password, and before I can type it in it goes into suspend mode again. sometimes it gets to desktop, sometimes it doesn't before suspend mode.

I tried todays daily of 10.10 liveusb same problem (while in liveusb!). I tried lots of stuff but no solution. So I assumed maybe my nettop was having a motherboard/power problem. I tried different plug outlets, unplugged printer/sound, same problem.

So I hooked up my 8 year old pentium 4. Installed 10.04.1. Everything was fine, I installed updates (new kernel), and restarted computer. As the computer was starting back up before it got to desktop it went into sleep mode!!! On my 8 year old tower. So definitely not hardware problem, but probably a kernel problem that is for some reason constantly looping suspend (or hibernate/sleep, not sure how to tell the difference). The power light is constantly blinking, so I think it is 'suspend' mode.

Someone else must be having this exact same problem since it occurs for me on 10.04.1 and 10.10 on two different hardware (atom n270 + GMA950 nettop and pentium 4 +i865? desktop).

This is a pretty serious issue. I'm not going to try other distros and try putting 9.10 on the nettop.

On my nettop when coming out of suspend mode, and desktop shows up, the screen 'blinks', and this I don't think is done by the monitor, but by OS itself. It dims really fast (near pitch black in 1 second) but returns to normal. Then 4 seconds later it goes back into suspend mode.

So maybe some patch that went into kernel (or other software? only like 10 listed in total after fresh install) after 10.04.1 (there is 1 kernel upgrade after fresh install), also got into 10.10 and now both don't work for me?

EDIT:
Where are the logfiles located that would show what happens when it goes into suspend mode on its own? That should tell what is going on? EDIT: log viewer in sys->admin

EDIT:
forgot to mention it happens with default 10.04.1 livecd/usb as well.

part pf log that shows suspend
```
Aug 27 08:52:32 tom-desktop kernel: [   20.468401] PM: Syncing filesystems ... done.
Aug 27 08:52:33 tom-desktop kernel: [   20.492082] PM: Preparing system for mem sleep
Aug 27 08:52:33 tom-desktop kernel: [   20.492093] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug 27 08:52:33 tom-desktop kernel: [   20.493914] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Aug 27 08:52:33 tom-desktop kernel: [   20.494215] PM: Entering mem sleep
Aug 27 08:52:33 tom-desktop kernel: [   20.494239] Suspending console(s) (use no_console_suspend to debug)
Aug 27 08:52:33 tom-desktop kernel: [   20.564033] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Aug 27 08:52:33 tom-desktop kernel: [   20.566446] sd 0:0:0:0: [sda] Stopping disk
Aug 27 08:52:33 tom-desktop kernel: [   20.666818] PM: suspend of drv:sd dev:0:0:0:0 complete after 102.789 msecs
Aug 27 08:52:33 tom-desktop kernel: [   20.667358] ACPI handle has no context!
Aug 27 08:52:33 tom-desktop kernel: [   20.667410] ACPI handle has no context!
Aug 27 08:52:33 tom-desktop kernel: [   20.667501] rt2860 0000:02:00.0: PCI INT A disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.667511] ACPI handle has no context!
Aug 27 08:52:33 tom-desktop kernel: [   20.680212] ata_piix 0000:00:1f.2: PCI INT B disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.696035] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.696049] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.696061] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.696072] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.696083] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.800104] HDA Intel 0000:00:1b.0: PCI INT A disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.816038] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.937 msecs
Aug 27 08:52:33 tom-desktop kernel: [   20.857016] i915 0000:00:02.0: PCI INT A disabled
Aug 27 08:52:33 tom-desktop kernel: [   20.872115] PM: suspend of devices complete after 377.591 msecs
Aug 27 08:52:33 tom-desktop kernel: [   20.872122] PM: suspend devices took 0.380 seconds
Aug 27 08:52:33 tom-desktop kernel: [   20.872297] r8169 0000:03:00.0: PME# enabled
Aug 27 08:52:33 tom-desktop kernel: [   20.904192] PM: late suspend of devices complete after 32.061 msecs
Aug 27 08:52:33 tom-desktop kernel: [   20.904284] ACPI: Preparing to enter system sleep state S3
Aug 27 08:52:33 tom-desktop kernel: [   20.920018] Disabling non-boot CPUs ...
Aug 27 08:52:33 tom-desktop kernel: [   20.920053] CPU0 attaching NULL sched-domain.
Aug 27 08:52:33 tom-desktop kernel: [   20.920059] CPU1 attaching NULL sched-domain.
Aug 27 08:52:33 tom-desktop kernel: [   20.984021] CPU0 attaching NULL sched-domain.
Aug 27 08:52:33 tom-desktop kernel: [   20.985194] Breaking affinity for irq 20
Aug 27 08:52:33 tom-desktop kernel: [   21.088025] CPU 1 is now offline
Aug 27 08:52:33 tom-desktop kernel: [   21.088030] SMP alternatives: switching to UP code
Aug 27 08:52:33 tom-desktop kernel: [   21.094290] Back to C!
Aug 27 08:52:33 tom-desktop kernel: [   21.094290] CPU0: Thermal monitoring enabled (TM2)
Aug 27 08:52:33 tom-desktop kernel: [   21.094290] Enabling non-boot CPUs ...
Aug 27 08:52:33 tom-desktop kernel: [   21.094290] SMP alternatives: switching to SMP code
Aug 27 08:52:33 tom-desktop kernel: [   21.099790] Booting processor 1 APIC 0x1 ip 0x6000
Aug 27 08:52:33 tom-desktop kernel: [   21.093388] Initializing CPU#1
Aug 27 08:52:33 tom-desktop kernel: [   21.093388] Atom PSE erratum detected, BIOS microcode update recommended
Aug 27 08:52:33 tom-desktop kernel: [   21.093388] CPU: L1 I cache: 32K, L1 D cache: 24K
Aug 27 08:52:33 tom-desktop kernel: [   21.093388] CPU: L2 cache: 512K
Aug 27 08:52:33 tom-desktop kernel: [   21.093388] CPU: Physical Processor ID: 0
Aug 27 08:52:33 tom-desktop kernel: [   21.093388] CPU: Processor Core ID: 0
Aug 27 08:52:33 tom-desktop kernel: [   21.093388] CPU1: Thermal monitoring enabled (TM2)
Aug 27 08:52:33 tom-desktop kernel: [   21.188112] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Aug 27 08:52:33 tom-desktop kernel: [   21.188137] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 27 08:52:33 tom-desktop kernel: [   21.208282] CPU0 attaching NULL sched-domain.
Aug 27 08:52:33 tom-desktop kernel: [   21.232025] CPU0 attaching sched-domain:
Aug 27 08:52:33 tom-desktop kernel: [   21.232032]  domain 0: span 0-1 level SIBLING
Aug 27 08:52:33 tom-desktop kernel: [   21.232038]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Aug 27 08:52:33 tom-desktop kernel: [   21.232049]   domain 1: span 0-1 level MC
Aug 27 08:52:33 tom-desktop kernel: [   21.232053]    groups: 0-1 (cpu_power = 1178)
Aug 27 08:52:33 tom-desktop kernel: [   21.232062] CPU1 attaching sched-domain:
Aug 27 08:52:33 tom-desktop kernel: [   21.232067]  domain 0: span 0-1 level SIBLING
Aug 27 08:52:33 tom-desktop kernel: [   21.232071]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Aug 27 08:52:33 tom-desktop kernel: [   21.232081]   domain 1: span 0-1 level MC
Aug 27 08:52:33 tom-desktop kernel: [   21.232085]    groups: 0-1 (cpu_power = 1178)
Aug 27 08:52:33 tom-desktop kernel: [   21.236030] CPU1 is up
Aug 27 08:52:33 tom-desktop kernel: [   21.236217] ACPI: Waking up from system sleep state S3
Aug 27 08:52:33 tom-desktop kernel: [   21.237137] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Aug 27 08:52:33 tom-desktop kernel: [   21.237200] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Aug 27 08:52:33 tom-desktop kernel: [   21.237268] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0x40114001)
Aug 27 08:52:33 tom-desktop kernel: [   21.237279] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0xf0, writing 0x1010)
Aug 27 08:52:33 tom-desktop kernel: [   21.237296] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
Aug 27 08:52:33 tom-desktop kernel: [   21.237362] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x1fff1, writing 0x40514041)
Aug 27 08:52:33 tom-desktop kernel: [   21.237371] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0xfff0, writing 0x40304020)
Aug 27 08:52:33 tom-desktop kernel: [   21.237381] pcieport 0000:00:1c.2: restoring config space at offset 0x7 (was 0xf0, writing 0x2020)
Aug 27 08:52:33 tom-desktop kernel: [   21.237398] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100104, writing 0x100507)
Aug 27 08:52:33 tom-desktop kernel: [   21.237466] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 08:52:33 tom-desktop kernel: [   21.237506] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 08:52:33 tom-desktop kernel: [   21.237546] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 08:52:33 tom-desktop kernel: [   21.237586] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 08:52:33 tom-desktop kernel: [   21.237634] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
Aug 27 08:52:33 tom-desktop kernel: [   21.237883] r8169 0000:03:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Aug 27 08:52:33 tom-desktop kernel: [   21.238077] PM: early resume of devices complete after 1.072 msecs
Aug 27 08:52:33 tom-desktop kernel: [   21.241107] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 27 08:52:33 tom-desktop kernel: [   21.241116] i915 0000:00:02.0: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360173] PM: resume of drv:i915 dev:0000:00:02.0 complete after 119.085 msecs
Aug 27 08:52:33 tom-desktop kernel: [   21.360200] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 27 08:52:33 tom-desktop kernel: [   21.360212] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360260] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 27 08:52:33 tom-desktop kernel: [   21.360270] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360301] usb usb2: root hub lost power or was reset
Aug 27 08:52:33 tom-desktop kernel: [   21.360329] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 27 08:52:33 tom-desktop kernel: [   21.360339] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360366] usb usb3: root hub lost power or was reset
Aug 27 08:52:33 tom-desktop kernel: [   21.360409] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Aug 27 08:52:33 tom-desktop kernel: [   21.360419] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360447] usb usb4: root hub lost power or was reset
Aug 27 08:52:33 tom-desktop kernel: [   21.360473] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
Aug 27 08:52:33 tom-desktop kernel: [   21.360483] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360510] usb usb5: root hub lost power or was reset
Aug 27 08:52:33 tom-desktop kernel: [   21.360537] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 27 08:52:33 tom-desktop kernel: [   21.360547] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360587] pci 0000:00:1e.0: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.360607] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 27 08:52:33 tom-desktop kernel: [   21.360615] ata_piix 0000:00:1f.2: setting latency timer to 64
Aug 27 08:52:33 tom-desktop kernel: [   21.365048] r8169 0000:03:00.0: PME# disabled
Aug 27 08:52:33 tom-desktop kernel: [   21.365072] rt2860 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 27 08:52:33 tom-desktop kernel: [   21.520029] PM: resume of drv:usb dev:usb1 complete after 154.759 msecs
Aug 27 08:52:33 tom-desktop kernel: [   21.524369] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Aug 27 08:52:33 tom-desktop kernel: [   21.524378] ata1.00: ACPI cmd ef/03:08:00:00:00:a0 (SET FEATURES) filtered out
Aug 27 08:52:33 tom-desktop kernel: [   21.526241] ata1.00: ACPI cmd c6/00:01:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Aug 27 08:52:33 tom-desktop kernel: [   21.548513] ata1.00: configured for UDMA/133
Aug 27 08:52:33 tom-desktop kernel: [   21.572504] ata1.00: configured for UDMA/133
Aug 27 08:52:33 tom-desktop kernel: [   21.572511] ata1: EH complete
Aug 27 08:52:33 tom-desktop kernel: [   21.768028] PM: resume of drv:usb dev:usb3 complete after 247.979 msecs
Aug 27 08:52:33 tom-desktop kernel: [   21.768651] sd 0:0:0:0: [sda] Starting disk
Aug 27 08:52:33 tom-desktop kernel: [   21.892029] usb 1-6: reset high speed USB device using ehci_hcd and address 4
Aug 27 08:52:33 tom-desktop kernel: [   22.031471] PM: resume of drv:usb dev:1-6 complete after 250.478 msecs
Aug 27 08:52:33 tom-desktop kernel: [   22.288024] usb 3-1: reset low speed USB device using uhci_hcd and address 2
Aug 27 08:52:33 tom-desktop kernel: [   22.595093] PM: resume of drv:usb dev:3-1 complete after 563.607 msecs
Aug 27 08:52:33 tom-desktop kernel: [   22.704024] usb 3-2: reset full speed USB device using uhci_hcd and address 3
Aug 27 08:52:33 tom-desktop kernel: [   23.068027] PM: resume of drv:usb dev:3-2 complete after 472.921 msecs
Aug 27 08:52:33 tom-desktop kernel: [   23.141108] usb 3-2.1: reset full speed USB device using uhci_hcd and address 4
Aug 27 08:52:33 tom-desktop kernel: [   23.258117] PM: resume of drv:usb dev:3-2.1 complete after 190.066 msecs
Aug 27 08:52:33 tom-desktop kernel: [   23.258243] PM: resume of devices complete after 2020.124 msecs
Aug 27 08:52:33 tom-desktop kernel: [   23.258502] PM: resume devices took 2.020 seconds
Aug 27 08:52:33 tom-desktop kernel: [   23.258564] PM: Finishing wakeup.
Aug 27 08:52:33 tom-desktop kernel: [   23.258568] Restarting tasks ... done.
Aug 27 08:52:33 tom-desktop anacron[1610]: Anacron 2.3 started on 2010-08-27
Aug 27 08:52:33 tom-desktop anacron[1610]: Will run job `cron.daily' in 5 min.
Aug 27 08:52:33 tom-desktop anacron[1610]: Jobs will be executed sequentially
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  Waking up...
Aug 27 08:52:33 tom-desktop kernel: [   23.712553] r8169: eth0: link down
Aug 27 08:52:33 tom-desktop kernel: [   23.713160] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (eth0): now managed
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (eth0): bringing up device.
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (eth0): preparing device.
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (wlan0): now managed
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (wlan0): bringing up device.
Aug 27 08:52:33 tom-desktop kernel: [   23.728150] RX DESC f0299000  size = 2048
Aug 27 08:52:33 tom-desktop kernel: [   23.728758] <-- RTMPAllocTxRxRingMemory, Status=0
Aug 27 08:52:33 tom-desktop kernel: [   23.768073] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Aug 27 08:52:33 tom-desktop kernel: [   23.768086] 1. Phy Mode = 0
Aug 27 08:52:33 tom-desktop kernel: [   23.768091] 2. Phy Mode = 0
Aug 27 08:52:33 tom-desktop kernel: [   23.795630] 3. Phy Mode = 0
Aug 27 08:52:33 tom-desktop kernel: [   23.818532] MCS Set = 00 00 00 00 00
Aug 27 08:52:33 tom-desktop kernel: [   23.820188] <==== RTMPInitialize, Status=0
Aug 27 08:52:33 tom-desktop kernel: [   23.820265] 0x1300 = 00073200
Aug 27 08:52:33 tom-desktop ntpdate[1438]: sendto(91.189.94.4): Network is unreachable
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (wlan0): preparing device.
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 27 08:52:33 tom-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 27 08:52:34 tom-desktop ntpdate[1438]: sendto(91.189.94.4): Network is unreachable
Aug 27 08:52:35 tom-desktop ntpdate[1438]: no server suitable for synchronization found
Aug 27 08:52:35 tom-desktop avahi-daemon[620]: Registering new address record for fe80::225:d3ff:fe3c:9cae on wlan0.*.
Aug 27 08:52:35 tom-desktop kernel: [   26.189788] CPU0 attaching NULL sched-domain.
Aug 27 08:52:35 tom-desktop kernel: [   26.189804] CPU1 attaching NULL sched-domain.
Aug 27 08:52:35 tom-desktop kernel: [   26.212151] CPU0 attaching sched-domain:
Aug 27 08:52:35 tom-desktop kernel: [   26.212163]  domain 0: span 0-1 level SIBLING
Aug 27 08:52:35 tom-desktop kernel: [   26.212172]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Aug 27 08:52:35 tom-desktop kernel: [   26.212188]   domain 1: span 0-1 level MC
Aug 27 08:52:35 tom-desktop kernel: [   26.212196]    groups: 0-1 (cpu_power = 1178)
Aug 27 08:52:35 tom-desktop kernel: [   26.212211] CPU1 attaching sched-domain:
Aug 27 08:52:35 tom-desktop kernel: [   26.212217]  domain 0: span 0-1 level SIBLING
Aug 27 08:52:35 tom-desktop kernel: [   26.212224]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Aug 27 08:52:35 tom-desktop kernel: [   26.212238]   domain 1: span 0-1 level MC
Aug 27 08:52:35 tom-desktop kernel: [   26.212245]    groups: 0-1 (cpu_power = 1178)
Aug 27 08:52:38 tom-desktop kernel: [   29.220075] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 209
Aug 27 08:52:38 tom-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto TRENDnet'
Aug 27 08:52:38 tom-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 27 08:52:38 tom-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
```

---

### Post by andrewabc on 2010-08-27
```
Aug 27 09:01:22 tom-desktop wpa_supplicant[677]: Failed to disable WPA in the driver.
Aug 27 09:01:39 tom-desktop kernel: [  532.917356] PM: Syncing filesystems ... done.
Aug 27 09:01:39 tom-desktop kernel: [  532.945039] PM: Preparing system for mem sleep
Aug 27 09:01:39 tom-desktop kernel: [  532.945047] Freezing user space processes ... (elapsed 0.00 seconds) done.
Aug 27 09:01:39 tom-desktop kernel: [  532.946982] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Aug 27 09:01:39 tom-desktop kernel: [  532.947208] PM: Entering mem sleep
Aug 27 09:01:39 tom-desktop kernel: [  532.947232] Suspending console(s) (use no_console_suspend to debug)
Aug 27 09:01:39 tom-desktop kernel: [  533.020038] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Aug 27 09:01:39 tom-desktop kernel: [  533.115537] sd 0:0:0:0: [sda] Stopping disk
Aug 27 09:01:39 tom-desktop kernel: [  533.116135] ACPI handle has no context!
Aug 27 09:01:39 tom-desktop kernel: [  533.116187] ACPI handle has no context!
Aug 27 09:01:39 tom-desktop kernel: [  533.116278] rt2860 0000:02:00.0: PCI INT A disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.116288] ACPI handle has no context!
Aug 27 09:01:39 tom-desktop kernel: [  533.132215] ata_piix 0000:00:1f.2: PCI INT B disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.148038] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.148052] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.148064] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.148075] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.148086] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.252139] HDA Intel 0000:00:1b.0: PCI INT A disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.268031] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.927 msecs
Aug 27 09:01:39 tom-desktop kernel: [  533.313728] i915 0000:00:02.0: PCI INT A disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.328116] PM: suspend of devices complete after 380.601 msecs
Aug 27 09:01:39 tom-desktop kernel: [  533.328123] PM: suspend devices took 0.384 seconds
Aug 27 09:01:39 tom-desktop kernel: [  533.328299] r8169 0000:03:00.0: PME# enabled
Aug 27 09:01:39 tom-desktop kernel: [  533.360350] PM: late suspend of devices complete after 32.219 msecs
Aug 27 09:01:39 tom-desktop kernel: [  533.360451] ACPI: Preparing to enter system sleep state S3
Aug 27 09:01:39 tom-desktop kernel: [  533.376019] Disabling non-boot CPUs ...
Aug 27 09:01:39 tom-desktop kernel: [  533.376053] CPU0 attaching NULL sched-domain.
Aug 27 09:01:39 tom-desktop kernel: [  533.376060] CPU1 attaching NULL sched-domain.
Aug 27 09:01:39 tom-desktop kernel: [  533.440024] CPU0 attaching NULL sched-domain.
Aug 27 09:01:39 tom-desktop kernel: [  533.544060] CPU 1 is now offline
Aug 27 09:01:39 tom-desktop kernel: [  533.544066] SMP alternatives: switching to UP code
Aug 27 09:01:39 tom-desktop kernel: [  533.550116] Back to C!
Aug 27 09:01:39 tom-desktop kernel: [  533.550116] CPU0: Thermal monitoring enabled (TM2)
Aug 27 09:01:39 tom-desktop kernel: [  533.550116] Enabling non-boot CPUs ...
Aug 27 09:01:39 tom-desktop kernel: [  533.550116] SMP alternatives: switching to SMP code
Aug 27 09:01:39 tom-desktop kernel: [  533.555587] Booting processor 1 APIC 0x1 ip 0x6000
Aug 27 09:01:39 tom-desktop kernel: [  533.549294] Initializing CPU#1
Aug 27 09:01:39 tom-desktop kernel: [  533.549294] Atom PSE erratum detected, BIOS microcode update recommended
Aug 27 09:01:39 tom-desktop kernel: [  533.549294] CPU: L1 I cache: 32K, L1 D cache: 24K
Aug 27 09:01:39 tom-desktop kernel: [  533.549294] CPU: L2 cache: 512K
Aug 27 09:01:39 tom-desktop kernel: [  533.549294] CPU: Physical Processor ID: 0
Aug 27 09:01:39 tom-desktop kernel: [  533.549294] CPU: Processor Core ID: 0
Aug 27 09:01:39 tom-desktop kernel: [  533.549294] CPU1: Thermal monitoring enabled (TM2)
Aug 27 09:01:39 tom-desktop kernel: [  533.644157] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Aug 27 09:01:39 tom-desktop kernel: [  533.644182] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 27 09:01:39 tom-desktop kernel: [  533.664338] CPU0 attaching NULL sched-domain.
Aug 27 09:01:39 tom-desktop kernel: [  533.692028] CPU0 attaching sched-domain:
Aug 27 09:01:39 tom-desktop kernel: [  533.692034]  domain 0: span 0-1 level SIBLING
Aug 27 09:01:39 tom-desktop kernel: [  533.692040]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Aug 27 09:01:39 tom-desktop kernel: [  533.692051]   domain 1: span 0-1 level MC
Aug 27 09:01:39 tom-desktop kernel: [  533.692055]    groups: 0-1 (cpu_power = 1178)
Aug 27 09:01:39 tom-desktop kernel: [  533.692064] CPU1 attaching sched-domain:
Aug 27 09:01:39 tom-desktop kernel: [  533.692069]  domain 0: span 0-1 level SIBLING
Aug 27 09:01:39 tom-desktop kernel: [  533.692073]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Aug 27 09:01:39 tom-desktop kernel: [  533.692083]   domain 1: span 0-1 level MC
Aug 27 09:01:39 tom-desktop kernel: [  533.692087]    groups: 0-1 (cpu_power = 1178)
Aug 27 09:01:39 tom-desktop kernel: [  533.696028] CPU1 is up
Aug 27 09:01:39 tom-desktop kernel: [  533.696213] ACPI: Waking up from system sleep state S3
Aug 27 09:01:39 tom-desktop kernel: [  533.697138] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Aug 27 09:01:39 tom-desktop kernel: [  533.697201] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Aug 27 09:01:39 tom-desktop kernel: [  533.697270] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0x40114001)
Aug 27 09:01:39 tom-desktop kernel: [  533.697281] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0xf0, writing 0x1010)
Aug 27 09:01:39 tom-desktop kernel: [  533.697297] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
Aug 27 09:01:39 tom-desktop kernel: [  533.697363] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x1fff1, writing 0x40514041)
Aug 27 09:01:39 tom-desktop kernel: [  533.697373] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0xfff0, writing 0x40304020)
Aug 27 09:01:39 tom-desktop kernel: [  533.697382] pcieport 0000:00:1c.2: restoring config space at offset 0x7 (was 0xf0, writing 0x2020)
Aug 27 09:01:39 tom-desktop kernel: [  533.697399] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100104, writing 0x100507)
Aug 27 09:01:39 tom-desktop kernel: [  533.697467] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 09:01:39 tom-desktop kernel: [  533.697508] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 09:01:39 tom-desktop kernel: [  533.697547] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 09:01:39 tom-desktop kernel: [  533.697587] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Aug 27 09:01:39 tom-desktop kernel: [  533.697636] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
Aug 27 09:01:39 tom-desktop kernel: [  533.697885] r8169 0000:03:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Aug 27 09:01:39 tom-desktop kernel: [  533.698078] PM: early resume of devices complete after 1.073 msecs
Aug 27 09:01:39 tom-desktop kernel: [  533.701110] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 27 09:01:39 tom-desktop kernel: [  533.701119] i915 0000:00:02.0: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820185] PM: resume of drv:i915 dev:0000:00:02.0 complete after 119.093 msecs
Aug 27 09:01:39 tom-desktop kernel: [  533.820213] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 27 09:01:39 tom-desktop kernel: [  533.820225] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820273] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 27 09:01:39 tom-desktop kernel: [  533.820284] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820313] usb usb2: root hub lost power or was reset
Aug 27 09:01:39 tom-desktop kernel: [  533.820341] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 27 09:01:39 tom-desktop kernel: [  533.820351] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820378] usb usb3: root hub lost power or was reset
Aug 27 09:01:39 tom-desktop kernel: [  533.820420] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Aug 27 09:01:39 tom-desktop kernel: [  533.820430] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820458] usb usb4: root hub lost power or was reset
Aug 27 09:01:39 tom-desktop kernel: [  533.820484] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
Aug 27 09:01:39 tom-desktop kernel: [  533.820494] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820521] usb usb5: root hub lost power or was reset
Aug 27 09:01:39 tom-desktop kernel: [  533.820548] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 27 09:01:39 tom-desktop kernel: [  533.820558] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820597] pci 0000:00:1e.0: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.820616] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 27 09:01:39 tom-desktop kernel: [  533.820625] ata_piix 0000:00:1f.2: setting latency timer to 64
Aug 27 09:01:39 tom-desktop kernel: [  533.825049] r8169 0000:03:00.0: PME# disabled
Aug 27 09:01:39 tom-desktop kernel: [  533.825074] rt2860 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 27 09:01:39 tom-desktop kernel: [  533.980076] PM: resume of drv:usb dev:usb1 complete after 154.803 msecs
Aug 27 09:01:39 tom-desktop kernel: [  533.984375] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Aug 27 09:01:39 tom-desktop kernel: [  533.984384] ata1.00: ACPI cmd ef/03:08:00:00:00:a0 (SET FEATURES) filtered out
Aug 27 09:01:39 tom-desktop kernel: [  533.986211] ata1.00: ACPI cmd c6/00:01:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Aug 27 09:01:39 tom-desktop kernel: [  534.008516] ata1.00: configured for UDMA/133
Aug 27 09:01:39 tom-desktop kernel: [  534.032507] ata1.00: configured for UDMA/133
Aug 27 09:01:39 tom-desktop kernel: [  534.032513] ata1: EH complete
Aug 27 09:01:39 tom-desktop kernel: [  534.228071] PM: resume of drv:usb dev:usb3 complete after 247.973 msecs
Aug 27 09:01:39 tom-desktop kernel: [  534.228693] sd 0:0:0:0: [sda] Starting disk
Aug 27 09:01:39 tom-desktop kernel: [  534.352051] usb 1-6: reset high speed USB device using ehci_hcd and address 4
Aug 27 09:01:39 tom-desktop kernel: [  534.491430] PM: resume of drv:usb dev:1-6 complete after 251.150 msecs
Aug 27 09:01:39 tom-desktop kernel: [  534.748048] usb 3-1: reset low speed USB device using uhci_hcd and address 2
Aug 27 09:01:39 tom-desktop kernel: [  535.055472] PM: resume of drv:usb dev:3-1 complete after 564.027 msecs
Aug 27 09:01:39 tom-desktop kernel: [  535.164025] usb 3-2: reset full speed USB device using uhci_hcd and address 3
Aug 27 09:01:39 tom-desktop kernel: [  535.524025] PM: resume of drv:usb dev:3-2 complete after 468.540 msecs
Aug 27 09:01:39 tom-desktop kernel: [  535.597484] usb 3-2.1: reset full speed USB device using uhci_hcd and address 4
Aug 27 09:01:39 tom-desktop kernel: [  535.715494] PM: resume of drv:usb dev:3-2.1 complete after 191.444 msecs
Aug 27 09:01:39 tom-desktop kernel: [  535.715620] PM: resume of devices complete after 2017.499 msecs
Aug 27 09:01:39 tom-desktop kernel: [  535.715878] PM: resume devices took 2.016 seconds
Aug 27 09:01:39 tom-desktop kernel: [  535.715938] PM: Finishing wakeup.
Aug 27 09:01:39 tom-desktop kernel: [  535.715942] Restarting tasks ... done.
Aug 27 09:01:39 tom-desktop anacron[2992]: Anacron 2.3 started on 2010-08-27
Aug 27 09:01:39 tom-desktop anacron[2992]: Normal exit (0 jobs run)
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  Waking up...
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (eth0): now managed
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (eth0): bringing up device.
Aug 27 09:01:39 tom-desktop kernel: [  535.935779] r8169: eth0: link down
Aug 27 09:01:39 tom-desktop kernel: [  535.936473] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (eth0): preparing device.
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (wlan0): now managed
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (wlan0): bringing up device.
Aug 27 09:01:39 tom-desktop kernel: [  535.949554] RX DESC f0387000  size = 2048
Aug 27 09:01:39 tom-desktop kernel: [  535.950114] <-- RTMPAllocTxRxRingMemory, Status=0
Aug 27 09:01:39 tom-desktop kernel: [  535.953980] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Aug 27 09:01:39 tom-desktop kernel: [  535.953991] 1. Phy Mode = 0
Aug 27 09:01:39 tom-desktop kernel: [  535.953995] 2. Phy Mode = 0
Aug 27 09:01:39 tom-desktop kernel: [  535.980926] 3. Phy Mode = 0
Aug 27 09:01:39 tom-desktop kernel: [  536.003716] MCS Set = 00 00 00 00 00
Aug 27 09:01:39 tom-desktop kernel: [  536.005346] <==== RTMPInitialize, Status=0
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (wlan0): preparing device.
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 27 09:01:39 tom-desktop kernel: [  536.005424] 0x1300 = 00073200
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 27 09:01:39 tom-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 27 09:01:40 tom-desktop anacron[3126]: Anacron 2.3 started on 2010-08-27
Aug 27 09:01:40 tom-desktop anacron[3126]: Normal exit (0 jobs run)
Aug 27 09:01:40 tom-desktop kernel: [  536.643697] CPU0 attaching NULL sched-domain.
Aug 27 09:01:40 tom-desktop kernel: [  536.643710] CPU1 attaching NULL sched-domain.
Aug 27 09:01:40 tom-desktop kernel: [  536.664178] CPU0 attaching sched-domain:
Aug 27 09:01:40 tom-desktop kernel: [  536.664193]  domain 0: span 0-1 level SIBLING
Aug 27 09:01:40 tom-desktop kernel: [  536.664206]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Aug 27 09:01:40 tom-desktop kernel: [  536.664232]   domain 1: span 0-1 level MC
Aug 27 09:01:40 tom-desktop kernel: [  536.664242]    groups: 0-1 (cpu_power = 1178)
Aug 27 09:01:40 tom-desktop kernel: [  536.664264] CPU1 attaching sched-domain:
Aug 27 09:01:40 tom-desktop kernel: [  536.664274]  domain 0: span 0-1 level SIBLING
Aug 27 09:01:40 tom-desktop kernel: [  536.664284]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Aug 27 09:01:40 tom-desktop kernel: [  536.664308]   domain 1: span 0-1 level MC
Aug 27 09:01:40 tom-desktop kernel: [  536.664318]    groups: 0-1 (cpu_power = 1178)
Aug 27 09:01:41 tom-desktop avahi-daemon[620]: Registering new address record for fe80::225:d3ff:fe3c:9cae on wlan0.*.
Aug 27 09:01:44 tom-desktop kernel: [  541.056126] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 209
Aug 27 09:01:44 tom-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto TRENDnet'
Aug 27 09:01:44 tom-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 27 09:01:44 tom-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 27 09:01:44 tom-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 27 09:01:44 tom-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 27 09:01:44 tom-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 27 09:01:44 tom-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
```
another part where suspend happens. for some reason it is not occuring now. but i have taken nettop to another room, hooked up to another monitor, have different keyboard/mouse hooked up, and no suspend happened yet. so power supply in wall sucks all of a sudden or a device on plugged into it doesn't work good. hmm

EDIT:
So far swapping of keyboard/mouse and nothing else plugged in is working. So now to wait and see if it continues to work fine, and to slowly add speakers and printer. Maybe the keyboard had the suspend key jammed up or something since it is 8 year old keyboard. Hopefully this was problem.

---

