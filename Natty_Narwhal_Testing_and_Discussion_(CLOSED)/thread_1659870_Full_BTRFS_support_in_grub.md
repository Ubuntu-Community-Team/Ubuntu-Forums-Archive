---
title: "Full BTRFS support in grub"
date: 2010-11-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by l3iggs on 2010-11-20
The natty installer crashes on me if I choose a fresh install with btrfs as the root file system type.

If I do a fresh maverick install with a btrfs root (and ext3 /boot) everything works fine until I upgrade to natty. When I attempt to boot into natty for the first time after the upgrade I get Kernel bug report with a stack trace saying there's a "kernel BUG at /build/buildd/linux-2.6.37/fs/btrfs/extent-tree.c:1400!" Things work fine again if I reboot and select the old linux kernel from maverick (2.6.35-22) in grub.

Can anyone else confirm this issue? Any suggestions on how to get btrfs working in natty?

---

### Post by l3iggs on 2010-11-22
Am I getting no responses here because nobody is able to recreate my issue or because nobody is trying?

It's a super easy test to run:
1) boot from the latest natty alternate .iso image: [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
2) when the partition manager comes up, choose manual
3)format your HD into 2 primary partitions
3a) 500 MB ext4 mounted at /boot
3b) the rest as btrfs mounted at /

right after the partitions get created my kernel crashes

Anyone else?

---

### Post by cariboo on 2010-11-22
I'm not sure if any one has been able to use the Live or alternate CDs to do an install. I tried both last Friday, and they both failed.

I did a Maverick install and updated to Natty earlier last week, using BTRFS. It took 4-5 hours to do the update, and most other operations where any disk writing was involved the system was abysmally slow.

---

### Post by arpanaut on 2010-11-22
I was finally able to install from the Sat. 11/20 alternate. No luck getting past the migration asst. in the live yet.
Tried BTRFS with a Maverick a while back and I too found the performance poor...
Sorry, I don't feel like messing with that filesystem again until I hear positive feedback. Support in Grub2 wouldn't hurt either.

Good Luck in your experimentation.

---

### Post by pferraro on 2011-01-04
... is finally here (apparently).  Has anyone tried using a btrfs boot partition yet?  Let us know if you've had any success.

[https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20110104-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20110104-1ubuntu1)

---

### Post by ratcheer on 2011-01-04
I saw that this afternoon, too. I haven't had time to try it, though. I guess it would require a fresh install.

Tim

---

### Post by brookie on 2011-01-04
Linux Mint 10 is using btrfs. Does that mean that they are already using btrfs for grub as well?

---

### Post by donniezazen on 2011-01-04
Do we still need a ext3/4 /boot partition or root,swap and home all can be btrfs?

---

### Post by dext on 2011-01-04
> **soham_1207 said:**
> Do we still need a ext3/4 /boot partition or root,swap and home all can be btrfs?

something i'd like to know also

---

### Post by Harry33 on 2011-01-05
> **pferraro said:**
> ... is finally here (apparently).  Has anyone tried using a btrfs boot partition yet?  Let us know if you've had any success.

[https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20110104-1ubuntu1](https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20110104-1ubuntu1)

That one failed to build on 64-bit architecture.

---

### Post by kahping on 2011-01-05
> **soham_1207 said:**
> Do we still need a ext3/4 /boot partition or root,swap and home all can be btrfs?

Just tried with today's ISO in VBox. The answer is "No". 

Even if grub supports it, the installer still tells you to create a separate /boot partition using a different FS. I was testing with the i386 ISO

---

### Post by pferraro on 2011-01-05
> **kahping said:**
> Just tried with today's ISO in VBox. The answer is "No". 

Even if grub supports it, the installer still tells you to create a separate /boot partition using a different FS. I was testing with the i386 ISO

Looks like the safe-guards have not yet been removed in the installer...  I wonder if the console installer has this problem.

That said, have any 32-bit users tried formatting their boot partition as btrfs and performing a manual grub-install?

---

### Post by Harry33 on 2011-01-05
> **Harry33 said:**
> That one failed to build on 64-bit architecture.

The new build was successfull:
[https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20110104-2ubuntu1](https://launchpad.net/ubuntu/natty/+source/grub2/1.99~20110104-2ubuntu1)

---

### Post by donniezazen on 2011-01-05
> **pferraro said:**
> Looks like the safe-guards have not yet been removed in the installer...  I wonder if the console installer has this problem.

That said, have any 32-bit users tried formatting their boot partition as btrfs and performing a manual grub-install?

Do we have to create boot partition or ideally we just need a root partition (with swap and /home)?

---

### Post by dnewkirk on 2011-01-05
Does anyone know if a fully functional fsck is immanent? I've seen some great performance improvements over ext3/4 when it comes to handling large sequence files, and I'd like to start using it on one of my workstations. I won't attempt that until I can fix errors though...

---

### Post by Slug71 on 2011-01-05
> **soham_1207 said:**
> Do we have to create boot partition or ideally we just need a root partition (with swap and /home)?

The point of this is to boot a root partition with BTRFS. So no, you shouldnt need a boot partition.

---

### Post by H3g3m0n on 2011-01-06
You can just install onto ext4 then run the conversion tool. You will have to update your fstab entries and grub though.

Otherwise if a conversion feels 'unclean' to you, you can install onto another partition/system/virtualmachine, manually create a partition then rsync -Xav the entire OS onto it while in the livecd (or other install). Once again update grub/fstab. (This option might be more problematic as you will need the updated grub already and need to know enough about grub to boot the install manually before the boot menu entries are crated. Then again your testing an experimental filesystem so you should be happy enough with a little command line...

---

### Post by ratcheer on 2011-01-07
It looks like the latest grub2 will detect and install with btrfs. From the change log:

 grub2 (1.99~20110106-1) experimental; urgency=low
...
- Fix grub-probe when btrfs is on / without a separate /boot.

Tim

---

### Post by ratcheer on 2011-01-07
I apologize for the triple posts, above. The site would not respond to my submissions, so I was hitting the X button on my browser and trying again. The site finally accepted all of my submissions.

Tim

---

### Post by cariboo on 2011-01-07
Removed extra posts.

---

### Post by pferraro on 2011-01-07
> **ratcheer said:**
> It looks like the latest grub2 will detect and install with btrfs. From the change log:

 grub2 (1.99~20110106-1) experimental; urgency=low
...
- Fix grub-probe when btrfs is on / without a separate /boot.

Tim

Also, the new partman-btrfs upload should enable the installer to accept btrfs boot partitions.

[http://launchpad.net/distros/ubuntu/natty/+source/partman-btrfs/5ubuntu1](http://launchpad.net/distros/ubuntu/natty/+source/partman-btrfs/5ubuntu1)

---

### Post by donniezazen on 2011-01-07
No luck so far.

---

### Post by t1497f35 on 2011-01-08
> **soham_1207 said:**
> No luck so far.
I wish the window on your screenshot could be maximized/resized since the area showing the list of partitions is (vertically) too small and there's plenty of vertical space on the screen. That's perhaps the only issue I have with the graphical Ubuntu installer but won't report it cause I'm too lazy... :(

---

### Post by dext on 2011-01-08
> **soham_1207 said:**
> No luck so far.

going by that i would of thought /boot partition would of Automatically been setup using ext4 ?

---

### Post by inportb on 2011-01-08
> **dnewkirk said:**
> Does anyone know if a fully functional fsck is immanent? I've seen some great performance improvements over ext3/4 when it comes to handling large sequence files, and I'd like to start using it on one of my workstations. I won't attempt that until I can fix errors though...

Same here. I've actually been using this on my MongoDB server for a while because snapshots are cool, but it doesn't die on me the way my Natty netbook does :P

---

### Post by pferraro on 2011-01-08
> **soham_1207 said:**
> No luck so far.

Which daily ISO did you use?  This fix would not have been available until today's iso.

---

### Post by ratcheer on 2011-01-08
Ok, I ran a fresh Natty install from the Jan 8 alternate iso. It allowed me to install to btrfs with no separate boot partition. The install ran from start to finish with no problems, everything appeared to be entirely normal and good.

When I tried to boot to Natty, here is what I got:

```

error: sparse file not allowed
error: couldn't find the chunk descriptor
error: you need to load the kernel first.

```I will also look on launchpad to see what I can find.

Luckily, my Maverick installation still boots just fine.

Tim

---

### Post by Blue Beard on 2011-01-09
> **dnewkirk said:**
> Does anyone know if a fully functional fsck is immanent? I've seen some great performance improvements over ext3/4 when it comes to handling large sequence files, and I'd like to start using it on one of my workstations. I won't attempt that until I can fix errors though...

Chris Mason has given a couple of people external to Oracle a version of fsck to fix their corrupted disks.

I would expect that we will see something in the next two months.

The power corruption issue appears to be hardware that reports it has completed tasks when it hasn't (i.e. a hardware issue).

---

### Post by amano on 2011-01-09
According to the btrfs wiki Chris Mason himself is working on the offline btrfs fsck: [https://btrfs.wiki.kernel.org/index.php/Project_ideas#Offline_fsck](https://btrfs.wiki.kernel.org/index.php/Project_ideas#Offline_fsck)

If it doesn't arrive in time for the Ubuntu feature freeze, btrfs support will most probably be delayed to autumn. Since they will not introduce it without the proper fsck tool around by default.

---

### Post by dext on 2011-01-09
> **amano said:**
> According to the btrfs wiki Chris Mason himself is working on the offline btrfs fsck: [https://btrfs.wiki.kernel.org/index.php/Project_ideas#Offline_fsck](https://btrfs.wiki.kernel.org/index.php/Project_ideas#Offline_fsck)

If it doesn't arrive in time for the Ubuntu feature freeze, btrfs support will most probably be delayed to autumn. Since they will not introduce it without the proper fsck tool around by default.

why would they delay it? F15 will have BTRFS support, Mint im sure has btrfs support. just because they dont have that tool yet doesnt mean it wont be supported, just a lil guess here, thats probably why /boot will still remain ext4 so users can still use fsck for errors untill btrfs gets that tool

---

### Post by amano on 2011-01-09
Let me clarify it: 

Without a fsck, they will have to delay btrfs as the standard filesystem and stay with ext4. But the midterm goal is to switch to btrfs completely (even for the boot partition) which cannot be considered without that tool. If something breaks it cannot be fixed. Which might be OK for Fedora (which is rather a testbed for RHEL) but certainly not for Ubuntu.

---

### Post by dext on 2011-01-09
> **amano said:**
> Let me clarify it: 

They will delay btrfs as the standard filesystem. But the midterm goal is to switch to btrfs completely (even for the boot partition) which cannot be considered without that tool.

ok that makes sense now, same with Fedora, hopefully target will be F17

---

### Post by amano on 2011-01-09
It seems that nobody knows the state of that tool. Perhaps it will come soon as a surprise. At least it is good to know that it is in the works.

---

### Post by dext on 2011-01-09
> **amano said:**
> It seems that nobody knows the state of that tool. Perhaps it will come soon as a surprise. At least it is good to know that it is in the works.

1 of 2 ways to findout, read the Grub mailing lists or searxh over on Oracles pages/wiki's

---

### Post by idontkn0w123 on 2011-01-18
> **ratcheer said:**
> Ok, I ran a fresh Natty install from the Jan 8  alternate iso. It allowed me to install to btrfs with no separate boot  partition. The install ran from start to finish with no problems,  everything appeared to be entirely normal and good.

When I tried to boot to Natty, here is what I got:

```

error: sparse file not allowed
**error: couldn't find the chunk descriptor**
error: you need to load the kernel first.

```I will also look on launchpad to see what I can find.

Luckily, my Maverick installation still boots just fine.

Tim

Hi, if I understand your posting right, your natty with btrfs does not  start? you just get this error then it starts? or doesnt it work at all?
I have installed natty with btrfs and its working for about 1 week now. I  have an 500MB patition in ext2 with /boot, and everything else is on my  / btrfs partition. 
I also get errors (about 4-5), but my natty starts after these  errors. Under 10sec (ssd) after i entered my bios password,  I can work  in natty. But i want to get rid of those errors. If someone knows what  to do, pls tell me :smile:

---

### Post by donniezazen on 2011-01-18
> **idontkn0w123 said:**
> Hi, if I understand your posting right, your natty with btrfs does not  start? you just get this error then it starts? or doesnt it work at all?
I have installed natty with btrfs and its working for about 1 week now. I  have an 500MB patition in ext2 with /boot, and everything else is on my  / btrfs partition. 
I also get errors (about 4-5), but my natty starts after these  errors. Under 10sec (ssd) after i entered my bios password,  I can work  in natty. But i want to get rid of those errors. If someone knows what  to do, pls tell me :smile:

I tried the Jan 17th alternate ISO and choose to install /root as brtfs but installation did not go through. I had to abort it. This sounds more like ISO error. The last time i tried to install i did not boot at all.

---

### Post by ratcheer on 2011-01-18
> **idontkn0w123 said:**
> Hi, if I understand your posting right, your natty with btrfs does not  start? you just get this error then it starts? or doesnt it work at all?
I have installed natty with btrfs and its working for about 1 week now. I  have an 500MB patition in ext2 with /boot, and everything else is on my  / btrfs partition. 
I also get errors (about 4-5), but my natty starts after these  errors. Under 10sec (ssd) after i entered my bios password,  I can work  in natty. But i want to get rid of those errors. If someone knows what  to do, pls tell me :smile:

No, it does not continue after those errors.

The way I understand the grub2 fixes referenced in the early posts of this thread is that the latest grub2 is supposed to be able to boot to a btrfs filesystem without a separate /boot partition. All I can say for sure is that that is not working for me. I gave up trying a couple of weeks ago and went back to ext4.

Tim

---

### Post by idontkn0w123 on 2011-01-18
As far as I can remember, when I installed it without /boot on a different filesystem, it did not work for me either. But with /boot on another format it worked. I have added compress in fstab and it really runs good. 
Elevator is set to noop. 
As I said before under 10sec to boot is okay for me. Only problem is that there are 4 or 5 error messages (like error:could not find the chunk descriptor) before system starts.
I'm having no problems so far with stability, even if its an alpha version running on btrfs format. Average daily use is about 8 hours and I had no data loss problems and my system did not crash yet. Im running ubuntu 11.04 as main (and only) system on my notebook. :)

@ratcheer you dont want to make 2 partitions on your (solid state) drive?

@soham_1207
my fstab with working system:
```
proc                                       /proc     proc   nodev,noexec,nosuid            0  0  
# / was on /dev/sda2 during installation
UUID=f737c5d5-b819-4c7e-878c-e56cad11b665  /         btrfs  defaults,noatime,compress,ssd  0  1  
# /boot was on /dev/sda1 during installation
UUID=c17a631a-a8c7-400f-9af0-f15dfa42cd84  /boot     ext2   defaults                       0  2  
tmpfs                                      /tmp      tmpfs  defaults,noatime,mode=1777     0  0  
tmpfs                                      /var/tmp  tmpfs  defaults,noatime               0  0  
tmpfs                                      /var/log  tmpfs  defaults,noatime               0  0  
tmpfs                                      /var/run  tmpfs  defaults,noatime               0  0  
```

I dont know if noatime is unecessary, so I simply added it.

---

### Post by ratcheer on 2011-01-18
> **idontkn0w123 said:**
> 

@ratcheer you dont want to make 2 partitions on your (solid state) drive?



No thanks, I will wait until btrfs is fully supported just like ext3, ext4, etc.

Tim

---

### Post by donniezazen on 2011-01-19
I just tried the latest ISO. It seems to work except ubiquity and grub installation is buggy which causes installer to crash. Hopefully we will see btrfs in a day or two.

---

### Post by kahping on 2011-01-20
> **soham_1207 said:**
> I just tried the latest ISO. It seems to work except ubiquity and grub installation is buggy which causes installer to crash. Hopefully we will see btrfs in a day or two.

I tried 20 Jan ISO in VM. Installs (though apport said Ubiquity crashed) and even boots though it gives an "error: sparse file no allowed" on boot. press any key and it continues on to desktop. looks like it works (mostly) :D

---

### Post by idontkn0w123 on 2011-01-24
Error's during bootup disappeared with some of the lastest patches from grub. Seems that btrfs is now better supported. /boot on ext3 partition and everything else on btrfs works now without any error messages or problems.
Now we have only to try if it also works with if there's only 1 btrfs with no separate boot. If I can find some free time to format and reinstall, I'll report if there are still any problems.

greets

---

### Post by ratcheer on 2011-01-24
> **idontkn0w123 said:**
> 
Now we have only to try if it also works with if there's only 1 btrfs with no separate boot. If I can find some free time to format and reinstall, I'll report if there are still any problems.

greets

I have to reinstall tomorrow. I will try it, too.

Tim

---

### Post by MountainX on 2011-01-24
FYI
btrfs is now available on Natty
[http://onubuntu.blogspot.com/2011/01/btrfs-is-now-available-on-natty.html](http://onubuntu.blogspot.com/2011/01/btrfs-is-now-available-on-natty.html)

> Recent daily ISOs for Natty are now able to install onto, and boot from btrfs partitions. It's still very much a work in progress so ext4 is still the default filesystem. You'll have to use advanced partitioning to manually configure the partitions yourself.

Ubiquity installing to btrfs partition in VirtualBox 4.0
With this, we can expect Alpha 2 to support btrfs for testing by the community.


Error when you boot from a btrfs partition
Booting from a btrfs partition currently still gives a "Error: sparse files not allowed" but pressing any key will resume booting and Natty indeed does boot all the way to desktop.


Natty running on btrfs
It's as simple as that. No fiddling with terminal. No installing to ext4 then converting to btrfs. No need for a separate /boot partition that uses another filesystem. The only requirement is to use Ubiquity's advanced partitioning feature.

---

### Post by ratcheer on 2011-01-25
> **ratcheer said:**
> I have to reinstall tomorrow. I will try it, too.

Tim

Still no workee. It installed Natty to btrfs root and installed grub2 to boot to the btrfs root partition. However, when I attempted to boot to it, I got the message "error: sparse file not allowed." When I pressed a key to continue, it gave me the grub menu with the option to boot to Natty. However, when I tried to do that, it gave me the sparse file error, again. And around and around.

I reinstalled Natty to ext4, again.

Tim

---

### Post by ratcheer on 2011-01-25
> 
Error when you boot from a btrfs partition
Booting from a btrfs partition currently still gives a "Error: sparse  files not allowed" but pressing any key will resume booting and Natty  indeed does boot all the way to desktop.

I tried this using Jan 25 alternate ISO. Pressed a key, got to grub2 menu. Attempting to boot just gave me the sparse file error, again. I tried multiple times, could never successfully boot.

Tim

---

### Post by donniezazen on 2011-01-25
Jan 25th ISO did not work. It failed to install grub.

---

### Post by idontkn0w123 on 2011-01-26
:( Installed lastest updates 10 minutes ago, now service nmbd does not start at all -.-
tried to reinstall, but it's still not working...

---

### Post by kahping on 2011-01-26
Well it _is_ a daily testing ISO. 

Were you installing in VBox or on a real machine? I was using Jan 23rd ISO I think. Trying Jan 26th ISO now in VBox :)

*Update:*

Jan 26th ISO works for me in VBox. What's with the new Ubuntu menu?

[IMG]http://picasaweb.google.com/lh/photo/ak9Z-aMkZBbRBxv-Z1iiUJ-RCF1dlIqVP8QFZQBld7s?feat=directlink[/IMG]

---

### Post by ratcheer on 2011-01-26
> **kahping said:**
> Well it _is_ a daily testing ISO. 

Were you installing in VBox or on a real machine? I was using Jan 23rd ISO I think. Trying Jan 26th ISO now in VBox :)

[IMG]http://picasaweb.google.com/lh/photo/ak9Z-aMkZBbRBxv-Z1iiUJ-RCF1dlIqVP8QFZQBld7s?feat=directlink[/IMG]

On a real machine.

Tim

---

### Post by donniezazen on 2011-01-26
> **idontkn0w123 said:**
> :( Installed lastest updates 10 minutes ago, now service nmbd does not start at all -.-
tried to reinstall, but it's still not working...

Were you able to install with only / btrfs and no ext3/4 /boot partition? How did the bootloader installation go?

---

### Post by cariboo on 2011-01-26
merged two btrfs threads that were the same.

---

### Post by idontkn0w123 on 2011-01-27
> **soham_1207 said:**
> Were you able to install with only / btrfs and no ext3/4 /boot partition? How did the bootloader installation go?

I did not try installing it with a new iso, my installation is now about 3 weeks old (NOT VM!), I chose manual partiton in the installation menu, put
"/boot" on ext2, 500MB
"/"  on btrfs, with entire remaining disk space
After that the system installed :)

Atm I get no errors with the brtfs format. I had no data loss at all, and no system crash with system running on a real machine with natty 11.04

The nmdb start failture has now gone when i installed todays new updates. But therefore now synaptics touchpad is nearly unusable with its new update from today. So I simply installed an old driver and it works again. hope they fix the new one soon.. 

greets

---

### Post by kahping on 2011-01-29
> **ratcheer said:**
> On a real machine.

Tim

I'm guessing it doesn't work outside a VM yet. Maybe things'll work once Alpha 2 is out.

---

### Post by rtalcott on 2011-01-29
/boot = ext4
everything else btrfs....feels quite fast and works well!
rt

---

### Post by Nerd_bloke on 2011-01-29
To everyone posting about a separate ext* "/boot" partition, you are referring to the old expected behaviour.

Grub reads/writes to either the "/boot" directory on the "/" partition, or (if it exists) a separate "/boot" partition.

The issue of grub supporting btrfs is whether grub can read/write to the single "/" partition formatted as btrfs (this will contain the "/boot" directory). 
Or to a separate "/boot" partition which is formatted btrfs.

Please stop posting about old supported cases.

---

### Post by H3g3m0n on 2011-01-29
Has anyone tried putting / on a subvolume? Could be handy for having multiple installs. You could also snapshot before a distupgrade.

I should also throw out a warning too. BTRFS does get corrupt even though it mostly seems fairly rock solid. It is an experiential filesystem still. I had problems with about 3 separate systems, nothing of value lost since they weren't important partitions.

Once it would randomly lock up the filesystem when reading files and instantly if I tried to do anything like erase a file (I manged to copy off most of that partition with rsync and it wasn't anything vitally important).

Another time I would get a kernel oops if I tried to mount it (It was just my partition for installed games for Linux (Wine) such as Dead Space, Mirrors Edge, The Witcher and a bunch of Wii isos which work great with dolphin-emu, all stuff I had backed up on my server). From what I could gather the free space reported by 'df' doesn't include the stuff used for btrfs's metadata so it can fill up even if there is space free, not sure why the results in not being able to mount it though...

btrfsck doesn't actually fix anything currently it just detects the errors, supposedly there is a lot of work going into a real fsck. But today if your file system gets corrupt there is no way to fix it.

I also wonder if it's safer to use sub volumes in the hopes that if they do get corrupt it's just that subvolume and you can still mount the whole fs to copy stuff off.

---

### Post by ratcheer on 2011-01-29
> **H3g3m0n said:**
> Has anyone tried putting / on a subvolume? Could be handy for having multiple installs. You could also snapshot before a distupgrade.



I have been wondering the same thing.

Tim

---

### Post by gnomeuser on 2011-01-29
> **ratcheer said:**
> I have been wondering the same thing.

Tim

[https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-btrfs-support](https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-btrfs-support)

It seems the plan is to exclude user data from the snapshot but otherwise do update snapshots (I assume this will work similarly to what Fedora does using yum and btrfs)

[csurbhi] change the installer so that it creates a system and a home subvolume by default (required for the apt snapshots): INPROGRESS

---

### Post by jacobzimmermann on 2011-01-30
> **H3g3m0n said:**
> Has anyone tried putting / on a subvolume? Could be handy for having multiple installs. You could also snapshot before a distupgrade.

I have been running maverick with / on a subvolume for a while. No problems at all, it works great, I can do snapshots etc. There were a few issues with setting it up though. I didn't find a way to tell the Ubuntu installer to install the root system into a subvolume, so I had to create a subvolume and then move the root filesystem's directories into it manually. Maybe this will change in natty, I didn't check that out yet. Once you have a subvolume with a root fs in it, there are a few more steps required to make it work:

Assuming that your root fs subvolume is /blah:

1) add the option "subvol=blah" to the root mount in /blah/etc/fstab;

2) restart your system, select recovery mode and enter command line edit mode. Add "rootflags=subvol=blah" to the kernel command line, then boot;

3) type mount | grep blah to ensure that your / is indeed mounted on the subvolume;

4) edit /etc/default/grub and add the following line:

GRUB_CMDLINE_LINUX="subvol=blah"

5) edit /usr/sbin/grub-mkconfig, search for GRUB_DEVICE and replace the following line:

GRUB_DEVICE="`${grub_probe} --target=device /`"

with:

GRUB_DEVICE="/dev/sda1" (assuming that the physical partition that contains /blah is /dev/sda1)

This is necessary because at least in maverick, grub-mkconfig doesn't properly detect partitions if a subvolume is used for /. Again, I don't know if that will change in natty.

6) run update-grub, reboot and enjoy ;)

---

### Post by Starks on 2011-01-31
Bottom line: Can GRUB use a BTRFS /boot or / partition?

---

### Post by gnomeuser on 2011-01-31
> **Starks said:**
> Bottom line: Can GRUB use a BTRFS /boot or / partition?

Yes

---

### Post by Starks on 2011-01-31
Are hacks required or will the GUI installer do all the work?

---

### Post by gnomeuser on 2011-02-01
> **Starks said:**
> Are hacks required or will the GUI installer do all the work?

All the information is available in this thread, I suggest you stop doing things the hard way and inform yourself.

---

### Post by Starks on 2011-02-01
Well, the information seems to changing daily with each new ISO, so a simple Yes or No would've been nice.

---

### Post by webme on 2011-02-01
> **gnomeuser said:**
> Yes

I've just tried to install Natty with btrfs as / (+boot) just like ext4 is now and doesn't work (at the end it gave me an error saying ti choose a different place for grub).

---

### Post by gnomeuser on 2011-02-01
> **Starks said:**
> Well, the information seems to changing daily with each new ISO, so a simple Yes or No would've been nice.

Okay, the blueprint I linked earlier is always the best way to track the btrfs feature.

Today it got updated to mark the required changes to the installer to separate /home out as a subvolume as DONE. This is needed for the apt-get snapshot features (similar to Fedora yum Btrfs snapshot assisted upgrades to allow rollback recovery), these though are not available presently.

Alpha 2 just froze for release, and I didn't note any change in the build queue to indicate that this work has been build. So if this will work in Alpha 2 is unknown, but you are at least likely to be able to do a full working BtrFS install using the daily isos shortly after Alpha 2 at least. One which has all the changes to the foundations applied to make future BtrFS feature upgrades painless (doing the subvolume transition would likely be practically impossible for upgrade). When the apt-get changes arrive they should hence just work.

So as things stand I would keep an eye on natty-changes and the daily builds. We are very close. I would though not recommend doing it till a daily or release is out which is confirmed to have the subvolume change.

---

### Post by gnomeuser on 2011-02-02
Okay the required feature is in. A daily iso or Alpha 2 when it arrives should give you the BtrFS you desire.

[https://lists.ubuntu.com/archives/natty-changes/2011-January/006578.html](https://lists.ubuntu.com/archives/natty-changes/2011-January/006578.html)

---

### Post by t1497f35 on 2011-02-02
Seems like supporting a new file system in grub is comparable to the effort of creating it. Why it's so difficult... do we have an architecture problem or what?

---

### Post by vishalrao on 2011-02-02
Anyone care to comment if BTRFS with Natty Alpha 2 will have **compression** and SSD+TRIM/discard support?

I usually jump on the development release bandwagon around alpha2 time, natty readiness is also coming along nicely apparently. Would love to see how my old 128 GB SSD performs especially if I get more space and hopefully more transfer speeds thanks to on-the-fly compression.

---

### Post by gnomeuser on 2011-02-02
> **t1497f35 said:**
> Seems like supporting a new file system in grub is comparable to the effort of creating it. Why it's so difficult... do we have an architecture problem or what?

You do have to implement some reading capabilities, and in btrfs's case the concept of volumes make this code more complicated than for most filesystems.

The biggest problem though seems to have been that grub2 is GPLv3+ licensed and the code for reading BtrFS was derived from the kernel and thus GPLv2, making the licensing incompatible. The code was ready in the Maverick development cycle but has only recently found it way into Grub2, to think of all the freedom which was protected by this. 

You may want to read up on coreboot for the "proper" solution, merely making Linux the BIOS and the bootloader.

---

### Post by gnomeuser on 2011-02-02
> **vishalrao said:**
> Anyone care to comment if BTRFS with Natty Alpha 2 will have **compression** and SSD+TRIM/discard support?

I usually jump on the development release bandwagon around alpha2 time, natty readiness is also coming along nicely apparently. Would love to see how my old 128 GB SSD performs especially if I get more space and hopefully more transfer speeds thanks to on-the-fly compression.

I believe those are optional mount parameters so you likely need to edit fstab to ensure that they are used but the code I believe should be in the daily isos now.

---

### Post by Funnnny on 2011-02-02
Can we convert / and /home to btrfs yet ?

---

### Post by vishalrao on 2011-02-02
> **gnomeuser said:**
> I believe those are optional mount parameters so you likely need to edit fstab to ensure that they are used but the code I believe should be in the daily isos now.

Ah, I guess there should be a way (it should be possible/nondestructive) to enable compression post install assuming there isn't a checkbox in the installer GUI somewhere :) Fingers crossed.

---

### Post by gnomeuser on 2011-02-02
> **Funnnny said:**
> Can we convert / and /home to btrfs yet ?

there is a conversion tool but using it will result in a slower performing filesystem compared to a clean install and it will not apply the needed subvolume changes.

---

### Post by Funnnny on 2011-02-03
> **gnomeuser said:**
> there is a conversion tool but using it will result in a slower performing filesystem compared to a clean install and it will not apply the needed subvolume changes.

I have /home mounted in a partition, and / in another, I can reinstall base system so it'll replace root partition by btrfs, but I wanna to convert /home, so is there any risk ? Why it's slower, with ext3->4 I know that older file will run on ext3, and newer file will perform on ext4, so is there any different with ext4 and btrfs

---

### Post by dext on 2011-02-03
> **Funnnny said:**
> I have /home mounted in a partition, and / in another, I can reinstall base system so it'll replace root partition by btrfs, but I wanna to convert /home, so is there any risk ? Why it's slower, with ext3->4 I know that older file will run on ext3, and newer file will perform on ext4, so is there any different with ext4 and btrfs

i would think ext4 is currently faster than BTRFS since it doesnt hold everything as of yet. BTRFS is still an experimental filesystem and probably wont be somewhat more useable till 11.10 / F16 - Fedora16

---

### Post by gnomeuser on 2011-02-03
> **Funnnny said:**
> I have /home mounted in a partition, and / in another, I can reinstall base system so it'll replace root partition by btrfs, but I wanna to convert /home, so is there any risk ? Why it's slower, with ext3->4 I know that older file will run on ext3, and newer file will perform on ext4, so is there any different with ext4 and btrfs

I know Hyperair tried to figure this out but without much luck (and then btrfs ate his data so testing kinda.. stopped). I suspect it has something to do with the layout that the conversion forces since that is backward compatible with ext3/4 (meaning you can mount the fs as ext3 still).

Regardless it won't enforce the subvolume changes which I suspect apt-get is likely to rely upon.

I would do a clean install, but I could wait some time, I just tried this with the daily from the 2nd of Feb, and it installs beautifully but grub is busted right now which leads to an unbootable system.

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/712366](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/712366)

---

### Post by ratcheer on 2011-02-03
> **gnomeuser said:**
> I know Hyperair tried to figure this out but without much luck (and then btrfs ate his data so testing kinda.. stopped). []("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/712366")

LOL! :p

Tim

---

### Post by blueadept on 2011-02-22
I did actually manage to get a system running Natty Alpha2 on UEFI working... all was running happily, except when the machine started I got this error:-

error: Couldn't find the chunk descriptor.
error: no suitable mode found.
error: no video mode activated.
error: Lua: cannot open (hd0,gpt3)/grub/hwmatch.lua: file not found.

There is no text console, but then X starts and all is well.

Any thoughts on why this might be?

Last night I updated, and now I have fewer errors from Grub... but the system does not boot into X... so with no console I have little hope of finding out why.

/boot is on ext3, / and /home on BTRFS.

Suggestions would be welcome.

---

