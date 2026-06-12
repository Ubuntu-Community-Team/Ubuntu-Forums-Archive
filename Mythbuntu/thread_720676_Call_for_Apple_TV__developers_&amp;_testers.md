---
title: "Call for Apple TV  developers &amp; testers"
date: 2008-03-10
forum: Mythbuntu
---

### Post by davilla on 2008-03-10
Consider this a call for developers/testers in creating an AppleTV based XBMC distribution. I've svn commited atv-bootloader, it's still a work in progress but the basics of a kexec based appletv bootloader are present and working. It does not auto-boot (manual kexec'ing works) a secondary kernel yet and that's where I need some assistance in creating bash script tools to automatically locate and parse the default grub menu.lst. All code contributed must be GNU v2.

The AppleTV, with nvidia xvmc assist, can decode and display 1080i mpeg2 content without problem. This makes the AppleTV a great inexpensive ($200 refurb) HD capable frontend for mythtv.

One of the initial targets is a USB pen drive based MythBuntu. The idea here is to create a USB pen drive based distro that one can boot MythBuntu without have to alter the original internal hard drive. Stick the USB pen in, re-boot and boot into MythBuntu instead of the AppleTV OS. It will most likely require at least a 4GB pen drive.

atv-bootloader is located here ([http://code.google.com/p/atv-bootloader/](http://code.google.com/p/atv-bootloader/)). The svn commit has both source and compiled bits so one does not need to recompile unless the initrd contents change. The initrd creation Makefile will be posted in a few days and it will support running a secondary bootloader script located outside the initrd.

atv-bootloader does not require EFI patches to the kernel and supports vesafb as a console framebuffer. I'm currently using standard 2.6.24.3 as the boot kernel but it should be able to kexec boot earlier kernels without problem. The 7.10 MythBuntu installer seems to have display device assumption problems so you will need some type of working Ubuntu based system as a direct boot to the MythBuntu LiveCD is not possible at the current time (working on it).

Send me a PM if you want to contribute and I'll PM back with my email address so we can take this off list until we have something to really brag about.

Scott

---

### Post by superm1 on 2008-03-11
Scott, I'm going to make this thread a sticky.  Best of luck with getting this project going.

---

### Post by davilla on 2008-03-11
Thanks for the sticky. I'm sure this will take off once a few more bits are in place that remove the amount of geekyness currently required.

Todays update:

boot parser is complete. I got tired of trying to do it in bash and wrote a c based command-line app last night. Pretty simple once you get the token parsing working. It and the make for the initramfs will be svn committed in a few days.

It will parse grub, kboot, syslinux, isolinux and mb_boot_tv config files for the default setting, extract and build the required kexec load command and eject this command as a string for other scripts to use.

Now to integrate this with the initramfs and scan for possible boot devices/partitions and soon -- auto boot.

Side note, not tried it yet but there are some boot params that can disable console during boot (fb=false and video=vga16:off). This might solve the boot hang while booting the LiveCD issue. This would enable a USB pen boot using the LiveCD.

---

### Post by superm1 on 2008-03-12
Once you've got something booted, you may consider hooking in with the -diskless stuff that we are doing for 8.04.  See the latest MCC for some info of what it does.

---

### Post by davilla on 2008-03-12
Yes, interested in the diskless, however that requires a working hardy install. I do most of my work under vmware on OSX and the vmware tools are currently broke (boo) for hardy. I'll try again once vmware tools are fixed or I install hardy to another real box.

---

### Post by superm1 on 2008-03-12
> **davilla said:**
> Yes, interested in the diskless, however that requires a working hardy install. I do most of my work under vmware on OSX and the vmware tools are currently broke (boo) for hardy. I'll try again once vmware tools are fixed or I install hardy to another real box.
Are you using the hardy image that is intended for virtualization?  There is such an image out there.

---

### Post by davilla on 2008-03-13
It's not a virtualization issue. The MythBuntu Hardy alpha boots and works fine. It's the vmtools, these enable drag and drop/copy paste from the host side. I could use ssh and scp but it's so much easer to do the other way.

---

### Post by davilla on 2008-03-14
Update:

I can't seem to get a LiveUSB (LiveCD -> USB pen) booting correctly under the AppleTV.  I have a USB pen made from a LiveCD, this boots on normal PC hardware. Same pen contents and boot args fails under AppleTV, can't see why and I think it's screen driver related. So I'm punting right now on getting the LiveCD boot working. 

But ... using the LiveCD to boot on normal pc hardware, then install MythBuntu to a pre-partitioned (using the patched parted) USB disk work fine. Console and splash don't work because vesafb is missing from the initrd but that can be fixed.

---

### Post by davilla on 2008-03-16
more svn commits and updated wiki pages at [http://code.google.com/p/atv-bootloader/](http://code.google.com/p/atv-bootloader/).

This should enable anyone to install MythBuntu 7.10 onto a disk for usage with the AppleTV.

---

### Post by SredniV on 2008-03-17
Hi Scott,

I really appreciate the work you've done on ATV.  It's great to see progress made on booting linux.

I went through the process yesterday and ran into the following problems before giving into sleep last night:

1)  I was able to get everything installed and was able to boot the ATV, but it didn't boot to mythbuntu.  It seemed to get stuck at the intermediate initrd (penbuntu maybe, can't see what it is now because of problem (2).  I'm not sure what went wrong here.  I poked around on the drive a bit and tried to look at what the boot script was looking for in order to kick over to linux, but couldn't tell.  

In the mythbuntu setup, I specificially told it not to install a bootloader.  Is there a trick that needs to happen to get grub written to the disk without having it install to the MBR?

2)  Right now, the big problem I have is that it won't boot anymore!  I've tested this with two different drives and the results are the same:  I plug the ATV in and it boots to an alternating Linux/ATV logo and an ATV with a "?" over it.  I'm guessing it's decided it can't find the drive anymore, but I'm not sure what would have caused this.  All I did this morning was plug it back in.  Using a different drive didn't help, either.  Neither did using the remote to direct it to the recovery partition (Menu + '-').

Any thoughts on what might have gotten hosed there?

Thanks!
Jason

---

### Post by davilla on 2008-03-17
There was a late fixed problem last night with not seeing USB devices during the probe for boot config files (grub menu.lst). This would then drop to the console login. The boot probe is a script called "boot_linux.sh" so you could just type "boot_linux.sh" and enter after loging on and getting a shell prompt. penbuntu is the hostname set during inird process.

The MBR skip step is paranoia and does not seem to affect my install testing. Grub and the MBR that grub installs are not used at all. atv-bootloader only looks at grubs menu.lst to find the boot params. I'm still investigating the effects of grub writing a MBR but so far it does not seem to cause any problems. GPT supports a legacy MBR and EFI should not even look at it.

If you see the Linux/ATV logo, then efi firmware loaded boot.efi and boot.efi found com.apple.boot.plist  and it trying to load the mach kernel. So it is finding the drive but something bad happens during loading the mach kernel and boot.efi aborts, show the bad disk logo and tries again.

Add "-v" to Kernel Flags in com.apple.boot.plist on the Recovery/OSBoot partition. The default Kernel Flags are "atv-boot=auto video=vesafb".

The "-v" is "verbose" mode and will disable the boot logo so you can see what the problem might be.

Also just a comment, if you try booting with the internal ata drive removed, then it takes about 30-40 seconds for efi firmware to finally decide to try the external USB devices. You can see it probing them by watching the access LED on the USB device but for some reason if the internal ata drive is missing, it searches around more.

If the internal ata drive is present, then power-on to Linux/ATV logo is about 10-15 seconds.

---

### Post by SredniV on 2008-03-17
Hi Scott,

Thanks for the feedback.  I'm glad to hear that I might not have completely bricked my ATV.  (It would be a pretty brick, though.)

When I installed mythbuntu, and it booted to the penbuntu login, I poked around on my sda4 partition but didn't see any grub files.  They don't seem to have been installed.  At the end of the install process, I told it not to install a bootloader at all, but I never saw a choice to install it to the MBR.  I'm guessing the fact that grub's menu.lst isn't on there is why I didn't get into mythbuntu at all.

> If you see the Linux/ATV logo, then efi firmware loaded boot.efi and boot.efi found com.apple.boot.plist and it trying to load the mach kernel. So it is finding the drive but something bad happens during loading the mach kernel and boot.efi aborts, show the bad disk logo and tries again.

Any ideas of what might have happened overnight?  I literally didn't do anything to the system from the time I got the penbuntu login to when I got the bad disk logo this morning other than unplug it.  From there, I got the same results with another disk I prepped this morning.

> The "-v" is "verbose" mode and will disable the boot logo so you can see what the problem might be.

I'll give that a try when I get home tonight.

Thanks again!
Jason

---

### Post by davilla on 2008-03-17
efi firmware can do some strange things. When I created my first install disk, I forgot to copy over boot.efi into Recovery/OSBoot partitions. efi firmware looked around before going back to the internal and booting an older linux install that was present. Even after I added boot.efi, it refused to consider the drive as bootable until after I pulled the internal drive. 

Check with the patched parted that the Recovery partition has the correct "atvrec" flag. If that's not present, it will not boot.

Also, you say "I poked around on my sda4 partition", sda is usually the internal unless the internal disk is not present. What is your disk configuration? 


It's pretty hard to brick the AppleTV as long as you stay away from the original internal disk. Even then, as long as you have a copy of the contents of the Recovery partition, it's pretty easy to reconstruct. Even lacking that you can recover using the downloadable AppleTV update.

I'll check the install procedure again tonight, I have to reinstall again too. Hosed current one playing around with adding a myth backend after I already had a frontend installed (which was pointed to my productionl mythbackend).  Hopefully I did not hose my productionl mythbackend, that's going to take a bit to rebuild as I need to be careful about PVR-150 IR blaster support.

---

### Post by SredniV on 2008-03-17
> Check with the patched parted that the Recovery partition has the correct "atvrec" flag. If that's not present, it will not boot.

I'll double check that.  I remember during setup that things were correct.

> Also, you say "I poked around on my sda4 partition", sda is usually the internal unless the internal disk is not present. What is your disk configuration?

I pulled the original internal disk and put my own in there for testing.  I didn't have any issues with voiding the warranty.  It also gave me a chance to make a full disk image of the original disk.

So, it was /dev/sda when I was working in there.  I'll probably switch to using the drive via USB for a while until I get things ironed out, then drop it in to the unit once it's done.


Jason

---

### Post by davilla on 2008-03-18
I've been testing some configurations. For some reason, it's taking an internal drive about 60+ seconds to be found by efi firmware, where same drive mounted on USB is about 11 second to Linux/ATV boot logo.

My previous linux internal was also about 11 seconds to logo so something is different that causes efi firmware to skip trying the drive if it is mounted internal.

So if you are doing an internal ata drive, give it about 60+ seconds before think something is wrong.

Oh and forget about trying a combined front/backend with a HDHomeRun. Myth 0.21 fixes is a real pig now and the system swaps like crazy trying to do 1080i, 720p is better but still swaps.

---

### Post by superm1 on 2008-03-18
> 
Oh and forget about trying a combined front/backend with a HDHomeRun. Myth 0.21 fixes is a real pig now and the system swaps like crazy trying to do 1080i, 720p is better but still swaps.
This boils down to the default deinterlacer being pretty CPU intensive.  There are a variety of others to try :)

---

### Post by davilla on 2008-03-18
That's not the reason. De-interlacing was turned off. MythTV is just a pig with cpu and memory.

Rant Mode On:

MythTV has fundamental issues in memory, io management and cpu usage. There's absolutly no reason for MythFrontEnd to suck down +100MB of ram doing 720p decode and display. Most of this is the static configuration screens and they should be compressed or tossed when not being displayed. Caching everything is just silly.

Codewise, the usage of QString for everything and QString comparisons for branching decisions is bad, bad, bad. Talk about wasting cpu. Also there are several functions (closed caption, wide screen detection, etc) that run all the time even though they are NOT enabled. Jump vectors anyone? TVPlay needs to be forked into TVPlay and DVDPlay. There's too many exceptions that need to be checked when playing DVDs. These checks and branches slow down non DVD decode/display. And what's with the fascination with building libraries that cannot be used outside of the frontend or backend.

The MythTV devs are not interested in any of this. It works for them and since they are running high performance cpus with lots of ram, they never see the issues. 

For comparison, there's about 25% cpu difference and 75% memory footprint difference between mplayer and mythfrontend decoding and display the same 1080i content. That's a big difference. Yes, myth has more functionality but it's not being used for basic display.

RANT Mode Off;

I will be issuing numerous patches for MythTV once atv-bootloader settles down. We will see it they get accepted. If not, I'll create a fork of the frontend code and create mythfrontend-light. MythTV is really good for what it does, there's lots of hard work inside and I have respect for what the devs have done.. But it's internal structure has out grown it's design and there's lots of novice coding mistakes inside. This is really evident by the amount of problems that the released 0.21 fixes has uncovered. This was pushed out the door way before it's time.

---

### Post by superm1 on 2008-03-18
> **davilla said:**
> 
I will be issuing numerous patches for MythTV once atv-bootloader settles down. We will see it they get accepted. If not, I'll create a fork of the frontend code and create mythfrontend-light. MythTV is really good for what it does, there's lots of hard work inside and I have respect for what the devs have done.. But it's internal structure has out grown it's design and there's lots of novice coding mistakes inside. This is really evident by the amount of problems that the released 0.21 fixes has uncovered. This was pushed out the door way before it's time.
This is great to hear.  I certainly hope these get accepted.

---

### Post by SredniV on 2008-03-18
This morning, I was able to get my ATV back to working condition.  I put the internal drive back in and was able to boot to the standard ATV config.  The other drive connected via USB seems to work better now.

I'm still having trouble with getting the grub files installed during a mythbuntu install (7.10).  I can't seem to get it to just install the files without trying to write the MBR.  (The last step in the installer has an "Advanced" button where you can specify if you want a boot loader installed and what disk to install it to.  If you leave the destination disk blank, it crashes taking a lot with it.  If you give it something incorrect, it crashes taking a lot with it.)  Is there an option you see in your use of the installer that allows to install grub files without installing to MBR?

After falling down with mythbuntu, I did try minimyth using a syslinux approach with the ramdisk option.  I had noticed that boot_linux.sh seems to be able to handle this situation.  After setting up that partition, it did seem to try to kexec the minimyth environment, but it didn't start any services.  It switched over, claimed it was in runlevel 5 and that there were no more services to start.

Now that I think about it, given that the ATV is so memory constrained to start with, taking up 96M of ram for a ramdisk is probably a bad idea.

I'll try again with mythbuntu tonight, and give writing the MBR a try since it shouldn't do anything wrong.

Another question I had was about suspend to RAM.  Have you done any investigation regarding whether this is possible?  Are the ACPI capabilities even there?

Jason

---

### Post by SredniV on 2008-03-18
I might be answering my own question regarding suspend.

From [http://wiki.awkwardtv.org/wiki/Dmesg_output]("http://wiki.awkwardtv.org/wiki/Dmesg_output"), it looks like the supported ACPI system states are S0 and S4, which would rule out suspend to RAM.  Suspend to disk (S4) looks like a possibility, though.

Given the ease of setup for suspend in Linux and the fact that my UPS was only registering a 20W draw with the ATV powered on, so maybe I don't care about suspend _that_ much!  :)

Jason

---

### Post by davilla on 2008-03-18
I would just let it install the MBR, it does not seem to cause any problems. I think the MythBuntu installer has a problem with that part. I've been running the installed it with installed MBR and do not see an issues so far.

I also tried MiniMyth with the same results. The basic MiniMyth assumes intel video and you have to configure it for nvidia. I lost patience with searching around their web site regarding configuring MiniMyth so I punted thinking I would come back to it later. I did post a request of mythtv-users mailing list but no one responded. Their loss.

96MB as a ram disk is pretty big with only 256MB but I've seen post of others in similar memory constraints using MiniMyth.

The AppleTV depend a lot of ACPI. That's the only way Linux can find and configure the hardware resources ( no BIOS ). Have not tired suspend to ram, screensaver works and cpu power c1,c2 c3 states are working last time I checked.

---

### Post by SredniV on 2008-03-18
I've met with some success!

I was able to get mythbuntu fully installed on partition 4 of the USB drive and booted completely into mythbuntu.  After a short wait updating everything to 0.21, I was able to watch some recordings.  YAY!

I've still got to setup the remote, which I don't anticipate too many problems with, and also try it out on both my 480p and 1080p TVs.  I've been testing on a regular monitor via HDMI->DVI.

I was happy to see that it didn't have any trouble converting 1080i content to 1024x768, which gives me confidence about my intended use of getting a frontend that will be able to playback 1080i on a 480p display.  My previous frontend for that purpose, an original PPC Mac mini, doesn't really cut it anymore.

I'm sure I'll have more questions along the way, but I can't begin to thank you enough for all your work on the atv-bootloader, Scott!  You've accomplished a lot and made a very easy process out of it.  NICE JOB!

Jason

---

### Post by davilla on 2008-03-18
Make sure you check back to  atv-bootloader wiki. I've been updating again. See [http://code.google.com/p/atv-bootloader/wiki/InstallMythBuntu](http://code.google.com/p/atv-bootloader/wiki/InstallMythBuntu) for solutions to nvidia issue.

Also I have a solution to the 40-60 second delay before seeing the linux/atv logo. This just bit me a few days ago, I've seen it reported but never saw a solution. It's a simple fix but I need to write it up.

---

### Post by davilla on 2008-03-19
The IR remote needs a lirc and kernel module patch. see [http://wiki.awkwardtv.org/wiki/Apple_TV_Linux_IR_Howto](http://wiki.awkwardtv.org/wiki/Apple_TV_Linux_IR_Howto) , I'm working on pre-built deb install but not there yet.

Also digital audio should work but you need to run alisamixer and unmute teh digital output. Analog auto need a kernel module patch.

---

### Post by SredniV on 2008-03-19
Hi Scott,

Is there a specific kernel version you recommend using?  It looks like there's some use of 2.6.23 right now, and the mythbuntu current version is 2.6.22.  2.6.24 is available, too.  I'd like to stick to the same (or nearly the same version) that others use so we can all work on issues with somewhat similar environments.

Also, do you have a kernel config you can post?  I was able to get the 2.6.20 config from [http://wiki.awkwardtv.org/wiki/Apple_TV_Linux_Kernel]("http://wiki.awkwardtv.org/wiki/Apple_TV_Linux_Kernel"), but the 2.6.22 hosted by wojci isn't available, so I'm not sure how far from a known config I got when I worked with 2.6.24 this morning.

**Update:**  Never mind on that config request, I found the one attached to the forum at AwkwardTV:  [http://forum.awkwardtv.org/viewtopic.php?f=23&t=167]("http://forum.awkwardtv.org/viewtopic.php?f=23&t=167")

Thanks!
Jason

---

### Post by davilla on 2008-03-19
I have many kernel configs ;), however for my present and future work, I'm sticking with standard kernel configs. For example, Ubuntu 7.10 Gutsy and MythBuntu (which is based on Gutsy) are using 2.6.22-14 with a similar kernel config. What I'm aiming for is easy install, usage and update.

Both of these distros boot fine on the AppleTV and support out of the box almost all AppleTV devices. IR and analog audio need kernel module patches but one can do these without having to rebuilt the actual kernel. I should be able to construct a deb that can update these two modules with very little fuss.

Yes, you could trim the kernel down or custom config it but there really not much point. Also 2.6.23 and 2.6.24 do not really add anything that helps/hurts with respect to the AppleTV hardware.

I am running 2.6.24.3 for the embedded kernel in the mach_kernel. That's mainly to pickup the efi framebuffer for bootloader development. This was all before I discovered that I could use vesafb as the framebuffer. So no real reason for 2.6.24.3, just historical development reasons. The kernel config is really stripped down to get a small kernel size that loads quickly. The whole make process for the initramfs is going to get committed to svn this weekend, still cleaning it up.

But if you want, somewhere in the linux section ([http://forum.awkwardtv.org/viewforum.php?f=23](http://forum.awkwardtv.org/viewforum.php?f=23)), I attached a 2.6.23.xx kernel config. Don't remember where off hand.

---

### Post by davilla on 2008-03-20
Question for superm1;

I took the update from a new 7.10 install on both the AppleTV frontend and my mainline backend and seem to be running the 0.21 fixes branch which is good. Previously I was running  MythBuntu weekly builds for an non-AppleTV frontend. The AppleTV and backend were running manual svn builds that matched MythBuntu svn trunk weekly builds.

Are there weekly builds from svn 0.21 fixes branch? The Mythbuntu web site just mentions 0.20-fixes branch. I'm not going to svn trunk until the QT4 mess is stable.

The 0.21 fixes branch seems to be two steps forward, 10 steps back regarding 1080i decode/display using XVMC. Seeing how the mythtv devs just committed selected patches applied to trunk to 0.21 fixes, I believe some patches got missed. The mythtv devs don't do much testing under XVMC anyway, they all run high performance boxes.  This is compared to a svn pull I was running a few weeks before the merges and release of 0.21 fixes. 1080i XVMC decode was running great then.

So I'd like to get to the svn 0.21 fixes branch, weekly builds would be great if not then I'll just have to do an manual svn installs. I need to get source builds working so I can identify the issues and get the solutions committed to into the 0.21 fixes branch (if the myth devs accept them of course).

What would be really nice to get a build working that creates the same install layout as the MythBuntu install. That way I don't tamper with how myth is installed under MythBuntu. My own private builds that I can mess with.

Thanks
Scott

---

### Post by SredniV on 2008-03-20
Hi Scott,

Do you have any tips on building the kernel modules for analog audio and the lirc kernel module?

I'm having a devil of a time getting the modules to compile and load with the stock kernel (2.6.22-14).  The modules I have been able to build either don't load because of version issues.  When I tried loading a sound module without version info, it froze the system.

Any tips that you could provide on the subject would be appreciated.

Thanks,
Jason

---

### Post by davilla on 2008-03-21
you have to build using the ubuntu kernel or module source 

sudo apt-get source linux-ubuntu-modules-2.6.22-14-generic

This talks about rebuilding the IR patch

[http://wiki.awkwardtv.org/wiki/Apple_TV_Linux_IR_Howto](http://wiki.awkwardtv.org/wiki/Apple_TV_Linux_IR_Howto)

you can not use it verbatim as it will have to be adapted to ubuntu kernel or module sources.

The analog audio is here

[http://forum.awkwardtv.org/download/file.php?id=44](http://forum.awkwardtv.org/download/file.php?id=44)

Again, it's a patch against the realtek kernel module

Always when pathing try --dry-run first in case things need to be fixed.

These patches might be for 2.6.22 or 2.6.23 kernels. They are close but you still might have to hand edit a bit.

Both patches are pretty short and simple so not much work to hand edit.

Either kernel or modules, you will have to build/install the debian/ubuntu way. Do some google searching for patching ubuntu kernel modules or something like that.. If you do it the correct way you will end up with a deb that gets installed and you will not have version problems.

I won't get to these two issues until the weekend, Just got done rebuilding my mainline mythbackend. Now that my source for 1080i content is back, I need to check some things. It looks like the gpu under-clock is not sticking with the 100.14.19 nvidia driver. crap might have to move up to a newer nvidia driver.

And just got a 32GB iPod touch -- very cool, so I'm a little distracted.

UPDATE:

do 
sudo apt-get source linux-image-2.6.22-14-generic

then google for patching ubuntu kernel source deb, that should get you started.  The lirc patch might have to made to the modules source, I see changes tehre to support muthbuntu already and you want to keep them.

---

### Post by SredniV on 2008-03-21
Thanks!

The linux-ubuntu-modules-2.6.22-14-generic was the trick for me.  I've now got working audio via RCA.

My process was roughly this:

```

apt-get source linux-ubuntu-modules-2.6.22-14-generic

cd /usr/src/linux-ubuntu-modules-2.6.22-2.6.22

cd ubuntu/media/snd-hda-intel

# patch patch_realtek.c
patch -p4 < appletv-rca-sound.patch

cd ../../..

fakeroot debian/rules binary-arch arch=i386 flavours="generic"

cd ..

dpkg --install linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37_i386.deb

```

Note that two of the patches didn't apply cleanly, but they were trivial to put in manually.

I'm still wrestling with IR, though.  I went through the patch process for hid-quirks, but I'm not seeing the expected devices show up in /dev when I load the module.

At the very least, I was able to build that module and load it without pulling down the system.  :)

I'm going to have to find more time to investigate that in the morning.

Jason

---

### Post by SredniV on 2008-03-21
OK.  

I figured out my IR problem.  Turns out that I applied those patches manually because they were so small.  Also turns out that I need to learn to type!

Things are working well now.

Next, I'll start playing with suspend stuff...

Jason

---

### Post by davilla on 2008-03-21
excellent, so you only had to patch "linux-ubuntu-modules-2.6.22-14-generic". That's very good. It will make the fixup processes easier.


Just an FYI,  nvidia-setting is not saving the gpu underclock setting. So eventually one will get a hang/video corruption if using xvmc. The installed driver is 100.14.19, there's a 100.24.23 then into the 169.xx versions. You must use "Envy" to install (follow their directions) or Ubuntu can get confused.

---

### Post by SredniV on 2008-03-21
"linux-ubuntu-modules-2.6.22-14-generic" was what I had to patch to fix the RCA output issue with the Intel HDA.  

For the IR issue, I had to patch against the usbhid code in the kernel tree itself and build from there.

I did look a bit at suspend this morning before I had to come to work.  I didn't get a chance to do anything very formal, but it doesn't seem to know about S3 (only S4).  I was able to tell it to suspend to disk by manually echoing "disk" to /sys/power/state.  It went through the proper motions (writing memory image to swap, etc.) and went into some kind of state.  It didn't look like the system was fully off, though, as the LED on the front was still blinking.

From there, I power cycled it because it didn't seem to want to wake via remote.  I probably didn't have the /proc/acpi/power/wakeup settings correct.  It did seem to try to resume after going through the atv-bootloader on power cycle, though.  Once it was back up, it was in a pretty catatonic state, so I assume I'll need to do a lot more investigation regarding what needs to be stopped prior to suspend.

Later tonight, I'm going to hook it up to my HD TV set to see how the full 1080i output looks/works.  So far, I've been doing 480p to a standard TV.

Jason

---

### Post by davilla on 2008-03-21
A full S4 suspend might get tricky. The normal AppleTV OS does not have this behavior so critical things might be missing in efi firmware and ACPI functions. Good luck.

The constant LED blink is normal. Unless the power goes all the way down, I don't think it will stop.

The LED blink (and color white/amber) is controlled by the internal USB IR controller. The internal UBS device does more than just IR, it's a catch all for IR, LED, Fan and other devices. It's a real USB device, a cypress chip but not a FX, FX2 varient.

There's a command line app (osputil) under the AppleTV OS that can get/set states for difference devices. It talks to the USB controller. This app works (more or less) using a patched OS X install so the information required is contained in the app itself. Disassembly has not been successuful so far. My intel disassembly skills suck. I'm a 68k man from way back.

So in theory, all one has to do is either fully disassemble and understand the app or snoop the USB bus transfers and capture the data transfers. Snooping the USB on the AppleTV OS (really OS X 10.4.7 variant) means creating a replacement IOUSBDevice kext that does the snooping. I know how to do this but have not had the time to undertake the project yet.

---

### Post by superm1 on 2008-03-21
> **davilla said:**
> Question for superm1;

I took the update from a new 7.10 install on both the AppleTV frontend and my mainline backend and seem to be running the 0.21 fixes branch which is good. Previously I was running  MythBuntu weekly builds for an non-AppleTV frontend. The AppleTV and backend were running manual svn builds that matched MythBuntu svn trunk weekly builds.

Are there weekly builds from svn 0.21 fixes branch? The Mythbuntu web site just mentions 0.20-fixes branch. I'm not going to svn trunk until the QT4 mess is stable.

The -fixes will start on hardy in a month.  Don't want to pollute the current 0.20-fixes for those that don't want to upgrade.  People on 7.10 wanting to upgrade can install the backport

> 
The 0.21 fixes branch seems to be two steps forward, 10 steps back regarding 1080i decode/display using XVMC. Seeing how the mythtv devs just committed selected patches applied to trunk to 0.21 fixes, I believe some patches got missed. The mythtv devs don't do much testing under XVMC anyway, they all run high performance boxes.  This is compared to a svn pull I was running a few weeks before the merges and release of 0.21 fixes. 1080i XVMC decode was running great then.

I don't know that i'd agree with this entirely.  There are devs that use XvMC as far as i'm aware.  I did run into similar behavior though that pre-empted my purchase of some hardware that didn't need XvMC...

> 
So I'd like to get to the svn 0.21 fixes branch, weekly builds would be great if not then I'll just have to do an manual svn installs. I need to get source builds working so I can identify the issues and get the solutions committed to into the 0.21 fixes branch (if the myth devs accept them of course).

If you catch some fixes that we should bring into hardy in the process, I'd be glad to import those in.  There has been a certain level of reluctance thus far because 0.21 is stable and all.

Your best bet is to "apt-get source mythtv".  You can then modify the debian/rules get-orig-source target to grab newer svn checkouts, and 'dch -i' to bump the changelog in your local builds.  Just type debuild or use a ppa/pbuilder/sbuild to do the builds.

> 
What would be really nice to get a build working that creates the same install layout as the MythBuntu install. That way I don't tamper with how myth is installed under MythBuntu. My own private builds that I can mess with.

Thanks
Scott
See above :)

---

### Post by davilla on 2008-03-21
Thanks for the response, 

I get to eat a large plate of crow about the xvmc comment. It seems to be working fine now that I got the backend stable again. I run several large drives for video storage and this time I did not want /var/lib/mythtv/video used for video storage. Thought the problem was related with this but it turned out to be a firmware update that slipped in for the HDHomeRun screwed up tuning channel 5 (CBS) which is my 1080i source. Downgrading the firmware fixed it.

I do get a large amount of repeating "audio stream changed" in the frontend log.

I'll take a stab at the Hardy beta this weekend, I wanted to get Gutsy working first as many other projects depend on this.

---

### Post by SredniV on 2008-03-23
Hi Scott,

I noticed two things tonight around the same time:  1)  The overclocking settings on my system weren't taking hold.  2)  Your changes to the wiki indicating a needed change there.

I have the 100.14.x drivers installed which came as part of a convenient package for ubuntu.  How did you install the 169.x driver you're using?  Was it part of an ubuntu package, or did you download from the nVidia site and install using their installer?

Other than that, things are working great.  I seem some decent stutter at the start of live-TV viewing in HD and during OSD usage, but it's bearable.  I decided to use my MS MCE remote for myth instead of the ATV IR since I had the MCE all setup on my previous front end already and could just copy config files.  I'm also successfully using a Logitech RumblePad for MAME control.  It's all stable enough, though, that I'm risking the WAF to put it in place as my primary frontend system in place of the PC that was there before.

After some testing I think I gave up on suspend, as I don't seem to be able to get the system to completely shutdown in S4 mode.  When it goes to sleep, it still draws a significant amount of power (well, for it, at least).  

Average runtime power consumption is 18-20W (peak 23W).  When it thinks it's asleep, it's using ~14W.  At that point, I'm not sure what the win is in regards to suspend.  4W over a month is ~3kWh, which would save me about $0.30.  It's not the most earth friendly point of view, but I'm not sure wrestling suspend into completely working is worth that much of my time.  :)

I will probably pick up another ATV for the bedroom, though, and will likely be going the 8.04 route there.

<rant>I also now know why I quickly decided not to use Debian when it first came on the scene so many years ago.  Is there some requirement that everything require the most convoluted and arcane process?  ;)</rant>

---

### Post by superm1 on 2008-03-24
> **SredniV said:**
> Hi Scott,
<rant>I also now know why I quickly decided not to use Debian when it first came on the scene so many years ago.  Is there some requirement that everything require the most convoluted and arcane process?  ;)</rant>
Well this is how "development" is anywhere.  Once it's fully "functional", all these patches get dropped into nice places and it gets easy :)

---

### Post by davilla on 2008-03-24
> **SredniV said:**
> Hi Scott,

I noticed two things tonight around the same time:  1)  The overclocking settings on my system weren't taking hold.  2)  Your changes to the wiki indicating a needed change there.

I have the 100.14.x drivers installed which came as part of a convenient package for ubuntu.  How did you install the 169.x driver you're using?  Was it part of an ubuntu package, or did you download from the nVidia site and install using their installer?

I first used "Envy", then the drive died when I was rebuilding the kernel, so I'm going to an manual install next. I've done that before and as long as you remove and purge the other it's fine. "Envy" seems really complicated for what it does. I was going to test again with 100.14.x after I figured out how to get the 169.xx driver to stick with the underclock settings. I've updated the wiki to reflect what I had to do so re-check it before trying to update the nvidia driver.

> **SredniV said:**
> Average runtime power consumption is 18-20W (peak 23W).  When it thinks it's asleep, it's using ~14W.  At that point, I'm not sure what the win is in regards to suspend.  4W over a month is ~3kWh, which would save me about $0.30.  It's not the most earth friendly point of view, but I'm not sure wrestling suspend into completely working is worth that much of my time.  :)


I would concentrate on spinning down the disk and sleeping the video. The cpu will drop to c3 when nothing is happening. That's about the best you can do

> **SredniV said:**
> <rant>I also now know why I quickly decided not to use Debian when it first came on the scene so many years ago.  Is there some requirement that everything require the most convoluted and arcane process?  ;)</rant>

I when from RedHat to Ubuntu because it was much easer to install stuff. The deb stuff is a little strange but I've gotten use to it.  

Most of what you have done is working around the fact that the AppleTV is pure EFI with no BIOS running x86 hardware. LInux make a very big assumption that x86 means BIOS and video bios. 

If you really want WAF, get a MacMini for the primary front end and move the ATV to the bedroom. You might want to wait, there's a rumor going around that the MacMini is about to get an update. Maybe a month or so.

---

### Post by davilla on 2008-03-25
UPDATE;

  New version of recovery.tar.gz posted. This fixes the boot load error that affects some AppleTVs.

---

### Post by jakep_82 on 2008-03-26
Has anyone tested wireless speeds while running Linux on the Apple TV?  I'm about to pull the trigger on buying one and installing Mythbuntu, but I'm concerned I'll have bandwidth issues while streaming HD recordings from the backend.  I do have an 802.11n router which I'm assuming should help in that regard.

---

### Post by davilla on 2008-03-26
I use a wired link so I can't tell you real world numbers but

if you don't have any non "n" devices forcing your "n" router to "g" or "b", and if you don't have other 2.4GHz devices (wireless phones, microwaves, etc) blasting garbage into your wireless spectrum and the linux "ndiswrapper" works as advertised and your wireless router is close enough, the you should have no problems streaming HD content. 

I can stream over a "g" network from mythweb (on myth backend) to a MacBook running VLC but that not the same as myth backend to myth frontend.

Can you stream HC content over wireless "n" using other computers? If so then I would guess possible, the above "ifs" then reduce down to ndiswrapper working as advertised and you can check that by searching google for others using ndiswrapper and linux on the Broadcom chipset. WEP and WAP add other switch points.

---

### Post by jakep_82 on 2008-03-26
That is a lot of ifs.  The router in question is not currently in use as I don't have any 802.11n devices.  I bought it specifically to connect a frontend to my backend.  Originally I was going to buy a wireless bridge and build a small frontend machine.  Then I saw your posts on mythtv-users and I figured I could save a bunch of money with an Apple TV.  The plan is to run the router in "n" only mode without encryption, but with MAC filtering that will only allow the frontend to connect.  I think I'll just buy the Apple TV and see what happens.  If nothing else I can always use it with the original firmware.  Off to the Apple store I go :)

---

### Post by davilla on 2008-03-30
UPDATE

Mythbuntu on the AppleTV seems pretty stable so far. There have been several updates to the atv-bootloader wki ([http://atv-bootloader.googlecode.com/](http://atv-bootloader.googlecode.com/)) that describe the installation process. Installation should be pretty straight forward. Video (Nvidia XvMC), audio (analog and digital), and IR (Apple IR remote) are all working.

You don't need to modify the original internal hard drive, this processes works fine from an external USB hard drive which can be a 2.5 or 3.5 hard drive depending on your external USB hard drive enclosure. I highly recommend starting with a external USB hard drive setup as this does not require altering the original internal hard drive.

As stated before, you do not need to open the AppleTV as everything required can be downloaded from network sources.

This project does require normal PC hardware booting the LiveCD for the initial setup and installation as installation directly from the AppleTV is not possible at the current time (still looking in to this). In addition, there are several patch/build steps which are detailed in the wiki. As such, this project is NOT a click-n-install and requires some familiarity with Ubuntu and Linux.

Enjoy

Scott

---

### Post by davilla on 2008-04-10
Well, no more sticky thread it seems.

Anyway, Mythbuntu on the AppleTV is working fine and is quite stable. I guess this thread will eventually get buried unless I keep tagging it.

ok, I see now, forum re-organization and the threads are being moved.

---

### Post by tgm4883 on 2008-04-10
Yea there were waaaaay to many stickies.  You are still linked to in the Testing sticky.

---

### Post by davilla on 2008-04-10
I understand, thanks for keeping it sticky.

---

### Post by chimpoko on 2008-04-10
Hi,

Great job on this, great install guide! just great! I'm happy that this is working for ppl. but I'm having issues....... :( 

I've tried installing using the atvbootloader follwoing the precise instructions on the google code page. unfortunately I have run into issues.

Issue #1 On boot the anything "black" on the screen turns "pink".
* I am connected via HDMI... I have not tried using any other cable...
* color is fine when booted into aTV

Issue #2 Ir does not respond at all.
* works in aTV

If someone could help with this I would be grateful.
Thanks

---

### Post by davilla on 2008-04-10
Need more info. 

This is the Mythbuntu install correct? 

nvidia driver updated to 169.12? I get a flash of all pink just before X11 comes up, this is 1080p HDMI output.

usbhid patch installed (needed for IR) ?

post your dmesg output to a pastebin site and give the URL here.

---

### Post by davilla on 2008-04-12
> **chimpoko said:**
> Issue #1 On boot the anything "black" on the screen turns "pink".
* I am connected via HDMI... I have not tried using any other cable...
* color is fine when booted into aTV

pink showing for black it a classic example of an DVI/HDMI RGB - YPrPb mismatch. The nvidia chipset  is driving one format, the HDTV expects the other. 

Once X11 and the nvidia binary driver takes control this should clear up. I'm not sure how to fix for command-line. I now have the same issue when doing 1080p via the command-line. Very strange.

---

### Post by markbirss on 2008-04-22
davilla

thank you for your ongoing work on this project!:)

I am running Ubuntu Gutsy on my appletv.

I have installed the 169 nvidia driver and sometimes when X/gdm (ubuntu 7.10) starts I have a green screen. I simply kill X to restart it and it starts normally.

I'm running 1080p and 720p. My console displays without the green/pink problem.

Could the ATV Bootloader be changed to display the grub menu ?

Regards

---

### Post by animatt on 2008-04-23
I orginally read this post a little while back when it was short, so maybe my answer is in the first few posts, but I can not remember and I am being lazy.

Basically the appletv seems to have the exact same hardware from machine to machine to machine.

I was wondering why there does not exist a generic mythbuntu image.  Like do a fresh install, apply patches and get things working.  After that just make a disk copy with dd command?  

Being that all the hardware is the same it just screams out to me, but maybe that is just me.

I have a apple tv and would enjoying messing around with it.  But again being a bit lazy here.  


So basically I am offering to host such a file if one is made.  I can probably support 250gb a month transfers right now, not sure about speeds though.

I can not see a reason why this would be illegal but anyway the offer this there.

Thanks for your time, everyone keep up the good work.

Cannot remember which email address I attached to this account but can be reach at my [email]USERNAME@gmail.com[/email]

---

### Post by davilla on 2008-04-23
> **markbirss said:**
> davilla

thank you for your ongoing work on this project!:)

I am running Ubuntu Gutsy on my appletv.

I have installed the 169 nvidia driver and sometimes when X/gdm (ubuntu 7.10) starts I have a green screen. I simply kill X to restart it and it starts normally.

I'm running 1080p and 720p. My console displays without the green/pink problem.

Could the ATV Bootloader be changed to display the grub menu ?

Regards

Green screen with X running, that's new one, never have seen it. I'd like to see the contents of

/etc/modules

/etc/X11/xorg.cong

/var/log/Xorg.0.log 

when you have a green screen


grub menu? An Apple TV IR remote controlled boot menu selector is planned but I've had no time to work on it.

---

### Post by davilla on 2008-04-23
> **animatt said:**
> I orginally read this post a little while back when it was short, so maybe my answer is in the first few posts, but I can not remember and I am being lazy.

Basically the appletv seems to have the exact same hardware from machine to machine to machine.

I was wondering why there does not exist a generic mythbuntu image.  Like do a fresh install, apply patches and get things working.  After that just make a disk copy with dd command?  

Being that all the hardware is the same it just screams out to me, but maybe that is just me.

I have a apple tv and would enjoying messing around with it.  But again being a bit lazy here.  


So basically I am offering to host such a file if one is made.  I can probably support 250gb a month transfers right now, not sure about speeds though.

I can not see a reason why this would be illegal but anyway the offer this there.

Thanks for your time, everyone keep up the good work.

Cannot remember which email address I attached to this account but can be reach at my [email]USERNAME@gmail.com[/email]

I don't think this will be required once I turn back to Mythbuntu and get cdrom boot working. I've figured out how to get analog audio and IR working without a kernel rebuilt and those two are the messiest of the patches. An initrd rebuild might be required but that's easy.

dd can't be used reliably with GPT formated disk. Has to do with the secondary partition table at the ending sectors of the disk. Also when you dd the disk, you replicate partition UUIDs and that's bad.

One thing that would help a lot with Mythbuntu install is a deb that contains the patched parted, hfs tools and gptsync. This would eliminate any source building from a LiveCD. I'm deb stupid and this seems pretty simple for someone with deb building experience. I can certainly host the deb and it's a simple wget from atv-bootloader downloads and dpkg -i.

---

### Post by laga on 2008-04-23
> **davilla said:**
> 
One thing that would help a lot with Mythbuntu install is a deb that contains the patched parted, hfs tools and gptsync

That should be possible. Is there any reason why these patches can't go into the regular packages? Or go upstream?

---

### Post by davilla on 2008-04-23
> **laga said:**
> That should be possible. Is there any reason why these patches can't go into the regular packages? Or go upstream?

gptsync is in the current refit 0.11. You really don't want refit (EFI bootloader), just gptsync

As far as I know hfs tools don't have a package, this build darwin versions of fsck.hfsplus and mkfs.hfsplus under Linux. There might be a license issue with this a the source is Apple Public Source License and the patches are GPL.

The parted patch was submitted to parted dev more than a year ago but they seem to have dropped with no explanation.

As far as other patches;

IR controller -> usbhid need a simple two line patch that been around for months an I need to push upstream. One does not need the patch as a usbhid module option can enable the device.

Analog audio -> snd-hda-intel in patch_realtek.c need a simple patch. forcing to macpro will also work. but easer to patch/rebuld ALSA than kernel. This also has been around for month and I need to push it upstream.

---

### Post by davilla on 2008-04-27
Update:

WooHoo, Gutsy cdrom boot direct on the AppleTV. See the atv-bootloader wiki for details.

---

### Post by haxor999 on 2008-04-29
Davilla,
thanks for the great work. I am about to get an Apple tv and will be installing some flavor of Ubuntu on it using your instructions.

One thing I'm wondering about is - the atv-bootloader wiki seems to contain the most up to date and comprehensive information for linux on the atv. Other sites such as [http://www.mactel-linux.org/wiki/AppleTV]("http://www.mactel-linux.org/wiki/AppleTV") and [http://wiki.awkwardtv.org/wiki/Linux_on_Apple_TV]("http://wiki.awkwardtv.org/wiki/Linux_on_Apple_TV") look to be quite dated by now. Would it be worth it to consolidate this information, or at least add pointers from those sites to yours? It took me quite some googling before I stumbled across your wiki.

---

### Post by shwtme on 2008-05-02
Ignore for now.  Just saw that the wiki has been updated with Hardy instructions (I did the initial install last week).  Will update after I go through them.  No point in anyone wasting there time trying to help me till I do.  Thanks.

First of all thanks for all the great work.

I went and picked up an AppleTV last week after finding this thread.

I have gotten everything installed (and running, woohoo) using 8.04 except for the audio.

First question: Does the audio support digital out or just RCA?  I know from your wiki that it doesn't support HDMI.

Second Question:  When trying to install the audio I get an error when trying to run:

```
sudo fakeroot debian/rules binary-arch arch=i386 flavours="generic"

```

The error is something about a missing version.h file and the path to the linux source.  Sorry I don't have the exact error right now, I will re run it later to get it for you when I am near the box again.

I have tried every way I can think of to get the linux source installed properly.

Any idea what I may be missing?

Thanks and again great job.

---

### Post by grytpype on 2008-05-02
I just bought an Apple TV on eBay to serve as a satellite frontend... so consider me a tester.

I've read this thread and I'm a little confused... is this working yet or not?

---

### Post by shwtme on 2008-05-02
> **grytpype said:**
> I just bought an Apple TV on eBay to serve as a satellite frontend... so consider me a tester.

I've read this thread and I'm a little confused... is this working yet or not?
I'm working on getting it setup now.  I have everything working but the sound.  Meaning I get the interface I can use the remote to navigate and play items, they play, I just don't get any sound yet.  Working on that issue now using the updated instructions.  I'm just hoping I didn't screw things up too bad by trying to hack through the instructions for an older version of mythbuntu.

FYI - I installed to an external USB harddrive so if I run into any show stoppers I can still return the apple tv.  Once I have everything working I will install to the internal HD.

The instructions where great on the wiki page listed from the first page of this thread.  And He seems to be constantly updating them.

If you have any questions I would suggest posting them here and/or on the target wiki page.

Good luck.

---

### Post by shwtme on 2008-05-02
An update on my sound issue:

I am connecting using a digital audio cable.

It appears to be a myth setup issue and not the Apple TV system setup.

Mythvideo - plays video but no sound, I have tried vids with dts, dd, others that I don't know the specific encoding

Mythmusic - no sound at all (doesn't even appear to play the files)

MythStream - I have tried apple movies trailers and shoutcast and both play fine with sound.

Anyone have an idea?

---

### Post by grytpype on 2008-05-02
Thanks for the info, after reading the wiki I still have a few questions:

> **davilla said:**
> One of the initial targets is a USB pen drive based MythBuntu. The idea here is to create a USB pen drive based distro that one can boot MythBuntu without have to alter the original internal hard drive. Stick the USB pen in, re-boot and boot into MythBuntu instead of the AppleTV OS. It will most likely require at least a 4GB pen drive.

Has that been accomplished?  Or do I have to do an install from the live disk to a USB hard drive?  Would a USB pen drive work?

I've seen the AppleTV remote, and no way does it have enough buttons to work a MythTV frontend!  Can we use other remotes like the MCE?

---

### Post by davilla on 2008-05-02
> **shwtme said:**
> An update on my sound issue:

I am connecting using a digital audio cable.

It appears to be a myth setup issue and not the Apple TV system setup.

Mythvideo - plays video but no sound, I have tried vids with dts, dd, others that I don't know the specific encoding

Mythmusic - no sound at all (doesn't even appear to play the files)

MythStream - I have tried apple movies trailers and shoutcast and both play fine with sound.

Anyone have an idea?

run "alsamixer" in a terminal windows and un-mute the digital. ALSA always comes up with digital out muted.

EDIT
 Just re-read your post. Sounds like digital audio out work for some MythTV plugins but not all. Not a clue but you might check the MythTV wiki ([http://www.mythtv.org/wiki](http://www.mythtv.org/wiki)).

---

### Post by davilla on 2008-05-02
> **grytpype said:**
> Thanks for the info, after reading the wiki I still have a few questions:



Has that been accomplished?  Or do I have to do an install from the live disk to a USB hard drive?  Would a USB pen drive work?

I've seen the AppleTV remote, and no way does it have enough buttons to work a MythTV frontend!  Can we use other remotes like the MCE?

There are lot's of new pages and the wiki has been re-organized.

[http://code.google.com/p/atv-bootloader/wiki/BootableUSBLinuxInstall](http://code.google.com/p/atv-bootloader/wiki/BootableUSBLinuxInstall)

shows how to do a usb disk boot, this can be flash or hard disk. I did a 8GB flash drive using Mythbuntu Hardy and it worked pretty well.

I'll be adding a page on using an MCE remote and IR receiver -- just got one to try out.

---

### Post by davilla on 2008-05-02
It's best if you post to the atv-bootloader discussion group. I get those emailed directly to me so I can respond pretty quickly.

Now that this thread is no longer a sticky, other threads can drive this thread off the main page and I sometimes don't see new posts.

---

### Post by grytpype on 2008-05-03
> **shwtme said:**
> I'm working on getting it setup now.  I have everything working but the sound.

Could you possibly make an ISO, or tar.gz, of your disk?

Reason I'm asking is that I've been re-reading the wiki, and although I'm willing to do all that stuff, if it's already been done then what's the point of doing it again?

---

### Post by davilla on 2008-05-03
> **grytpype said:**
> Could you possibly make an ISO, or tar.gz, of your disk?

Reason I'm asking is that I've been re-reading the wiki, and although I'm willing to do all that stuff, if it's already been done then what's the point of doing it again?

Sorry, I don't have hosting space for a disk image of any size. In addition, a disk image of GPT format disk can only be reliably "imaged" to a disk with exactly the same number of sectors. And using "dd" with USB flash disks can be problematic. I mention this on the wiki.

---

### Post by grytpype on 2008-05-03
> **davilla said:**
> Sorry, I don't have hosting space for a disk image of any size. In addition, a disk image of GPT format disk can only be reliably "imaged" to a disk with exactly the same number of sectors. And using "dd" with USB flash disks can be problematic. I mention this on the wiki.

I wonder if the Mythbuntu.org folks could host it for you, give you a directory and let you ftp disk images into it.

I think Apple TV could be THE solution for a Myth frontend, since it's so cheap and available and has HD capability, but if it's going to catch on there's going to have to be a way to package the software so it's reasonably easy to install.

---

### Post by shwtme on 2008-05-03
Fixed my sound issue.

Changed the myth sound settings to the following:

```
Audio Output Device: ALSA:default
Passthrough output device: ALSA:plughw:0,1
Checked Enable AC3 to spdif passthrough
Checked Enable DTS to spdif passthrough

```

I'm now completely setup and working.  I'm going to run for a while (a couple weeks) using the external usb hardrive and see if I run into any issues.  If I run into anything I will post the issues on the project page.

After I'm comfortable that everything is working I will do a clean install to the internal HD to test that out.

Thanks again for your fantastic work on this.

Also, if you think of a good way to setup an image(s) for this.  Maybe just an internal and/or external usb HD image (with specifically mentioning that people need to backup the internal HD first).  If you turn it into a torrent I'd be willing to allocate 5Mbs of my internet connection to seed the torrent.

I'll cross-post this on the main wiki so if anyone runs into the sound issue my settings will be there to.

---

### Post by grytpype on 2008-05-03
> **davilla said:**
> And using "dd" with USB flash disks can be problematic. I mention this on the wiki.

I'm actually thinking about pulling out the 40G hard drive and replacing it with a flash drive of some sort, using adapters.  I figure the atv will use less power and make less noise!

---

### Post by Unibrav on 2008-05-14
My Apple TV arrived late last week and I'm going to get started on it this weekend. What do you think the chances are that we could figure out how to [network boot]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless") these machines? Even if we had to bootstrap it with a USB key. To me, that would be the ultimate setup.

---

### Post by davilla on 2008-05-14
> **Unibrav said:**
> My Apple TV arrived late last week and I'm going to get started on it this weekend. What do you think the chances are that we could figure out how to [network boot]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless") these machines? Even if we had to bootstrap it with a USB key. To me, that would be the ultimate setup.

Should be quite possible, I know someone has already done a nfs mount using atv-bootloader without needing any mods. I've not tried it as my backend is a Gusty install and I need a working Hardy install to setup Hardy diskless.

A bootstrap with USB flash would be required as this is the only way to get control of the AppleTV in the first place.

---

### Post by JEDIDIAH on 2008-07-09
Hello,

   I am currently running a 40GB appletv unit with 7.10 and the latest available version of mythfrontend (and plugins) from the repositories. I am experiencing severe network performance issues and I was wondering if anyonne else had any ideas. I am seeing about 600KB/s whereas the other machines on my home network are able to push/pull 8MB/s or more.

   It's a wired home network and the central switch is a GigE switch.

   I've heard that the 8139 in the appletv is really lousy. So far it
seems like my network performance is my performance bottleneck. I have
been able to play transcoded OTA HD recordings but the raw stuff just
stutters way too much. SD stuff is fine. Although there are some startup
lags here and there.

---

### Post by lmclaren on 2008-08-15
I am considering buying a ATV and installing Mythbuntu on it, can someone please give some feedback in regard to performance in the areas of startup, browsing through the menus, which themes work best, time to start live tv after selecting etc.
Feel free to compare (unfairly?) to a reasonable pc based front end (C2D?)

Thanks

Lee

---

### Post by lmclaren on 2008-08-25
Hi, I will answer my own question in case it is of benefit to others:

I brought an ATV and installed Mythbuntu on the internal HDD.

Boot up is a little slow but once into Mythtv it is quite good, sometimes you get slight pauses on changing menu items (in the order of 1 sec).

Live Tv take a little time say 15 sec the first time but after that not too bad about 5 seconds. Most other functions like recorded tv and media library are quite good, say 3 sec to get into.

Nice and quite.

regards

LM

---

### Post by dardack on 2008-10-23
> **JEDIDIAH said:**
> Hello,

   I am currently running a 40GB appletv unit with 7.10 and the latest available version of mythfrontend (and plugins) from the repositories. I am experiencing severe network performance issues and I was wondering if anyonne else had any ideas. I am seeing about 600KB/s whereas the other machines on my home network are able to push/pull 8MB/s or more.

   It's a wired home network and the central switch is a GigE switch.

   I've heard that the 8139 in the appletv is really lousy. So far it
seems like my network performance is my performance bottleneck. I have
been able to play transcoded OTA HD recordings but the raw stuff just
stutters way too much. SD stuff is fine. Although there are some startup
lags here and there.

You have to put the AppleTV"s nic card in state C1 or C2, no I don't understand all of this, but from what i gather something along the lines of the nic card has different states of activity and when it drops to C3 it can't come back out of C3 in linux or something, so you have to set it to always be in C2, i think anyways.  It's what I did.

---

### Post by iitywygms on 2009-05-10
Reviving an old thread I know, but I am curious if this is now a pretty straight forward install.  I am thinking about getting the atv and want to be sure I can handle it before I do.  Is there a good how to I am not aware of?

---

### Post by iitywygms on 2009-06-01
Okay guys, I need some help
Been at this all weekend and still no joy.
I have followed this guide exactly

[http://code.google.com/p/atv-bootloader/wiki/PartitioningLinux](http://code.google.com/p/atv-bootloader/wiki/PartitioningLinux)
Everything goes well and no errors seen.

I then follow this guide.

[http://code.google.com/p/atv-bootloader/wiki/BootingLiveCD](http://code.google.com/p/atv-bootloader/wiki/BootingLiveCD)
I do the netboot install and all goes well.

This is what I do.

Boot the AppleTV using atv-bootloader and connect using telnet. Then

mkdir tmp

mount /dev/sdb1 tmp

kexec --load tmp/linux --initrd=tmp/initrd.gz --command-line="vga=normal vesa video=vesafb"

kexec -e

I install ubuntu, no errors noticed.  I install system to partition 4 and swap to 5.

Now here is where I am stuck.
When I reboot the atv, nothing happens and the atv logo with the question mark appears.
So I stick in the atv-bootloader usb stick and it boots to give me the login prompt.

I can login.  I just don't know where to go from here??????
How do I start linux?  Should it start automatically?

If I run boot_linux.sh  this is what I get.


boot_linux.sh
sda4/boot/brub menu.list found
/bin/bash/
kexec – load /mnt/rootfs/boot/vmlinux    (alot of numbers and stuff I am to tired to type)

kexec jump to new kernel


mount proc/mounts: No such file or directory
mount proc/mounts: No such file or directory

I have been at this all weekend and my eyes are shot.
Could someone please help.  I really want to make this work but I am bugging out and need a little help. Please

---

### Post by iitywygms on 2009-06-01
Help!!!

---

### Post by iitywygms on 2009-06-03
Okay, I quit. :( Time to sell it and buy a different box.
For anyone else that tries this, good luck.

---

### Post by iitywygms on 2009-06-08
I finally got it.
I had been installing from the usb stick, and or the netboot install.
I finally tried installing using and external cd drive.  That worked.
I still get the error message, but it does boot the linux kernel afterwords.
I think it may have been booting linux using the other methods, but x would not start???? maybe, I don't know.
Anyway, after some reading and messing around.  It works, remote and all.
:popcorn:

---

