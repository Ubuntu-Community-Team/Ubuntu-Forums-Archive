---
title: "Mythbuntu 8.04 Instability"
date: 2008-04-28
forum: Mythbuntu
---

### Post by adamwolf on 2008-04-28
I reinstalled my mythbox with Mythbuntu 8.04 on Friday via the CD (not an upgrade).  Since then, I've had 4 or 5 instances of the machine freezing completely, not even being accessible via SSH.  MythTV wasn't even running when the machine froze.

The machine was running the previous stable release of Mythbuntu previous, and had at least month+ uptimes before the upgrade.  I didn't open the case or move the hardware during the install, so I don't think there's an issue with RAM or power disconnecting.

Has anyone else had issues like this?

---

### Post by p$y on 2008-04-28
I had this too, I got a segmentation fault.
It was a defect RAM, so I would really suggest to check this.

---

### Post by bml137 on 2008-04-28
There is definitely an issue with the latest binaries.  Mine started locking up too.  Mine is related to the user jobs though.  When mythcommflag or mythtranscode run, even though they are of lower (high number) priority, X becomes unusable and I cannot even SSH into the box.

I am waiting for a fix, but the 8.04 freeze seems to have delayed those fixes for a while.

---

### Post by laga on 2008-04-28
Does your box lock up completely? Do you get a flashing 'caps lock' LED on your keyboard?

Do you have a sufficient amount of swap space?

---

### Post by bml137 on 2008-04-29
Mine?

I don't have a keyboard hooked up to that system.  There is no way for me to find out if it is a swap space issue, as I cannot do anything.  I can't even get a "user:" prompt when I ssh.  I can tell you that after running for a day, 0 swap space is being used right now.

However, if I am watching a recording after another recording finishes, the system will start to get hammered.  I immediately stop watching, ssh, and run htop.  I see that mythcommflag is taking 99% of one processor (dual core) at low priority.  When I start watching the recording again, it is better, but choppy.  X takes a good chunk of the second processor, but nothing out of the ordinary.

Basically, it appears that something seems really wrong with the kernel process scheduler.

I want to add that I could encode a DVD, record 2 shows, and watch 1 recording show all at the same time without a problem.  This was the case with the initial 0.21 upgrade.  When I upgraded from the gutsy to hardy sources, the cx88-alsa module was flawed.  That was finally fixed in ubuntu-modules-2.6.24-16.23.  Now the scheduling issue has popped up...seemingly in 2.6.24-16.23.

---

### Post by mrand on 2008-04-29
> **bml137 said:**
> Mine?

I don't have a keyboard hooked up to that system.  There is no way for me to find out if it is a swap space issue, as I cannot do anything.  I can't even get a "user:" prompt when I ssh.  I can tell you that after running for a day, 0 swap space is being used right now.
I think laga's question was how much do you have reserved for swap space?  While you're at it, how much RAM do you have?

   Marc

---

### Post by bml137 on 2008-04-29
not much: 512 MB for each RAM and swap.  it rarely never dips into swap though.  could a new process require that much more RAM?

---

### Post by gazer22 on 2008-04-29
I had a similiar experience to p$y.

7.10 had been pretty stable, 8.04 started out well, then random lockups started occurring - ssh freezing, etc.

Running memtest86+ from the Mythbuntu install CD confirmed a bad stick of RAM.  It's a pretty good first test to troubleshoot seemingly random system hangs:
[LIST=1]
[*]Put Mythbuntu (or Ubuntu) installer CD into the drive
[*]Shut down the system
[*]Remove all but one stick of RAM
[*]Turn the system back on, and choose "Test Memory" from the Mythbuntu/Ubuntu menu
[*]Repeat with each stick of RAM
[*]If one of them fails, separate it and replace if needed
[/LIST]

I have (had) 2 sticks of 1GB each, so my system is now running fine with the good 1GB while I try to get a replacement for the other under warranty.

System has been up for about 48 hours since.

Have no idea why RAM would apparently suddenly fail, but there you go.

As for swap, using 1GB of swap space...

---

### Post by gazer22 on 2008-04-29
> **bml137 said:**
> not much: 512 MB for each RAM and swap.  it rarely never dips into swap though.  could a new process require that much more RAM?

Good reference page here:  [COLOR="Blue"][Linux Server Performance Monitoring- When Do I Need A Memory Upgrade]("http://itmission.org/Main/LinuxServerPerformanceMonitoringCheckAndDetermineWhenDoINeedAMemoryUpgrade")[/COLOR]

---

### Post by bml137 on 2008-04-29
Mine may have to do with swap, now that I think of it.  When my system becomes unusable, you can hear the hard drive going wild.  Just a moment ago it became unusable when two recordings finished at the same time and 2 mythcommflag processes kicked off.  I had to reset the system.

Here is the interesting thing: after it booted, I ran htop and the mythcommflag processes started again and the hard drive was thrashing.  It was nearly unusable again, but ssh did work.  It seemed like the I/O was going nuts.  About 3 minutes later, the I/O stopped and the mythcommflag processes continued fine.  They don't seem to be the problem.  Maybe there is a hard drive problem...

---

### Post by bml137 on 2008-04-29
> **gazer22 said:**
> Good reference page here:  [COLOR="Blue"][Linux Server Performance Monitoring- When Do I Need A Memory Upgrade]("http://itmission.org/Main/LinuxServerPerformanceMonitoringCheckAndDetermineWhenDoINeedAMemoryUpgrade")[/COLOR]

```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 5  1      0   5032    180 127612    0    0  3846   218  255  974 67 14  6 13
 3  1      0   4984    180 127632    0    0  4922   581  602 3226 56 43  0  1
 3  3      0   5264    152 127500    0    0  7346   707  643 3582 58 38  0  5
 4  1      0   5300    132 127072    0    0  5804   543  599 3420 57 42  0  1
 3  1      0   4948    120 127380    0    0  6528   761  630 3485 58 42  0  0
 3  5      0   6040    108 126252    0    0  5788   593  693 3474 59 41  0  1
```

---

### Post by gazer22 on 2008-04-29
According to that page, you look good to go in terms of memory space.

I highly recommend the memory test on the Mythbuntu/Ubuntu installer CD.  

I was driving myself nuts checking logs, installing and uninstalling things, when it turns out to have been a RAM issue.

---

### Post by bml137 on 2008-04-30
Thanks you everyone for the suggestions, especially the swap space suggestion.

You won't believe what the issue is...  I've been using Linux on my personal computer for 8/9 years and am quite familiar with the architecture.  The issue was the last thing I would look for...

The upgrade from 2.6.24-16.22 to 2.6.24-16.23 caused my IDE hard drive to go from /dev/hda to /dev/sda.  My /etc/fstab file was still mounting /dev/hda1 to / and /dev/hda5 to swap.  Neither hda existed, but I guess grub is linking to hd0,0, so I didn't notice the /dev/hda1 issue.

Long story short, I didn't have swap drive.  I added udev rules to make sda1 and sda5 alias to hda1 and hda5 and everything is fine.

Is this a bug or should I expect IDE drives to appear on sd* now?  I have one IDE and one SATA on this system (OS on IDE and media on SATA).

Thanks,
Brian

---

### Post by gazer22 on 2008-04-30
Same thing here!  

I have no idea why that happens.

I changed my fstab file to use each drive's UUID instead of /dev/hdb1, etc., so I didn't have the issues you did.   (Well, not the same cause at least!)

---

### Post by jbman on 2008-04-30
Can you guys post the fix in terms of what you changed in fstab for future reference.

---

### Post by bml137 on 2008-05-01
I didn't change my /etc/fstab.  I just created a udev rule to point /dev/hda1 and /dev/hda5 to my IDE hard drive.

I could have changed /dev/hda1 to /dev/sda1 and /dev/hda5 to /dev/sda5 in /etc/fstab.  However, I don't know why my IDE became a SCSI drive.  I am assuming this will be fixed in the future and will become IDE again...

Aliasing the drive is rather complicated and is done using the serial number of your HD.

---

### Post by bla2000 on 2008-05-01
I think that I may have this problem too because my hard drive is thrashing a lot and the mythtv backend has failed 3 times in the past 3 days.  Before upgrading my system from Feisty to Hardy, I wrote down my results from: 

```
sudo fdisk -l
```

During the Hardy install I formatted all the drives except for the one containing my mythtv recordings.  In the old listing it refers to my drives as /dev/hda1, /dev/hda2, .. but now in Hardy my drives are listed as /dev/sda1, /dev/sda2, .. . Here is my current setup:

```

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a42d72d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            1276        9733    67938885    5  Extended
/dev/sda5            1276        1466     1534176   82  Linux swap / Solaris
/dev/sda6            1467        1593     1020096   83  Linux
/dev/sda7            1594        8280    53713296   83  Linux
/dev/sda8            8281        9733    11671191   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

```

My /etc/fstab looks like

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3155e3b1-84a2-4969-b9dc-b534ccefd0bc /               ext3    relatime,erro$
# /dev/sda7
UUID=2d0495ea-86f9-4e95-8aa5-71e9d4d88c69 /home           xfs     relatime     $
# /dev/sdb1
UUID=fa3988cc-f4cd-4d1a-83c6-c27564a035a1 /mythtv         xfs     relatime     $
# /dev/sda8
UUID=6ceb8070-5245-4767-8d9d-3cf0ad55f2ee /mythtv2        xfs     relatime     $
# /dev/sda6
UUID=3a5ba0cb-d086-40bb-9378-3624fd19fa5f /var/log        ext3    relatime     $
# /dev/sda5
UUID=48432008-d673-4b24-8d63-d5f3ca243bca none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by gazer22 on 2008-05-01
^^^ 

That's what my fstab looks like.  Works fine.

---

### Post by superm1 on 2008-05-01
Guys, I know it's probably easier to put in /dev/hdXY or /dev/sdVZ, but please try to use UUID's in your /etc/fstab.  They won't change around upgrades, and are created specifically for this purpose.

If you don't know your drives UUID, the easiest way to check is

```
ls -l /dev/disk/by-uuid
```
You will see your drive explicitly listed in one of the symlinks, and the appropriate partition's UUID there too.

---

### Post by bla2000 on 2008-05-01
Here's mine:

```

total 0
lrwxrwxrwx 1 root root 10 2008-04-30 23:11 2d0495ea-86f9-4e95-8aa5-71e9d4d88c69 -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-04-30 23:11 3155e3b1-84a2-4969-b9dc-b534ccefd0bc -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-30 23:11 3a5ba0cb-d086-40bb-9378-3624fd19fa5f -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-04-30 23:11 48432008-d673-4b24-8d63-d5f3ca243bca -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-30 23:11 6ceb8070-5245-4767-8d9d-3cf0ad55f2ee -> ../../sda8
lrwxrwxrwx 1 root root 10 2008-04-30 23:11 fa3988cc-f4cd-4d1a-83c6-c27564a035a1 -> ../../sdb1

```

Is hard drive my setup correct? Are my mythtv-backend instability issues related to something else?

---

### Post by ubnewbie2 on 2008-05-02
Guys, this has been catching lot's of people.  I experienced it on my desktop machine.  Apparently the new kernel does change the /dev/hd to /dev/sd type naming for most, but apparently not all, IDE drives. Seems like a crazy decision, but there it is!

I edited my fstab, as I don't expect it will change back, apparently this is the 'new' way of naming the hard drives from now on.

---

### Post by Nikas on 2008-05-02
I have the same problem. The computer locks up and i need to press reset. My drives did change from hd* to sd* but I'm using UUID's in fstab so... i dont know what to do!

My fstab:
```
# /dev/sda1
UUID=98bb856d-5c12-4a7a-bfe4-561ba3e125bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=f3518bb2-ca66-4099-8527-3dc6e8d26265 none            swap    sw              0       0
```

dmesg gives me: Adding 2008116k swap on /dev/sda2.  Priority:-1 extents:1 across:2008116k


My box do lock up completely.

memtest86 shows no errors. :( What now?
Going back to 7.10 soon.

---

### Post by Nikas on 2008-05-03
Changed grub to use kernel .22 from 7.10 again.
Now everything works fine!

My disks are back as hd* and the old driver is loaded.

What chipset do you guys have in your coputers?
I have Via. I'm quite sure it has something to do with libata..

What problems can this cause? Running Hardy with kernel .22.

---

### Post by bml137 on 2008-05-04
```
# lspci | grep IDE
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
```

I don't understand the use of UUID.  What happens when I switch hard drives?  I have to manually figure out the UUIDs and put them in fstab?  hda was the primary master IDE.  No matter what was plugged into that position, it showed up as hda.  Now it is bouncing around from sda to sdb.

---

### Post by Nikas on 2008-05-04
> **bml137 said:**
> ```
# lspci | grep IDE
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
```

I don't understand the use of UUID.  What happens when I switch hard drives?  I have to manually figure out the UUIDs and put them in fstab?  hda was the primary master IDE.  No matter what was plugged into that position, it showed up as hda.  Now it is bouncing around from sda to sdb.

Same hardware as mine. So.. this feels like a bug.
UUID's does not change. The names like hd*/sd* can change and yes, you have to change the uuid in fstab (if sys disk; menu.lst too) when switching hard drives.

I'm using 8.04 with the kernel from 7.10 now. Other "drivers" for the hard drives. Works great now.

---

### Post by bla2000 on 2008-05-07
Here my output:

```

lspci | grep IDE
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

```

---

### Post by bla2000 on 2008-05-07
Do you know what these errors mean? They were the last things written before my backend crashed.

```

2008-05-06 21:00:40.566 MythSocket(acfc7498:19): writeStringList: No data writte
n on writeBlock
2008-05-06 21:00:45.824 MythSocket(acfc7498:19): writeStringList: No data writte
n on writeBlock
2008-05-06 21:00:45.839 GetRecordBasename found no entry

```

---

### Post by Nikas on 2008-05-07
So, VIA + the new libATA = problem.

---

### Post by electrofreak on 2008-05-10
Seems nForce4 has the problem, too.

---

### Post by bla2000 on 2008-05-11
I rebuilt my system and the backend still crashes. It still writes the following in the logs before crashing.

```

2008-05-11 17:17:17.941 MythSocket(8301590:19): writeStringList: No data written
 on writeBlock
2008-05-11 17:17:24.035 MythSocket(8301590:19): writeStringList: No data written
 on writeBlock
2008-05-11 17:17:29.412 MythSocket(8301590:19): writeStringList: No data written
 on writeBlock
2008-05-11 17:17:34.842 MythSocket(8301590:19): writeStringList: No data written on writeBlock

```

Does anyone know what this indicates and is there a solution?  I'm using the same hardware as when I was running mythtv on Feisty, Edgy, and Hoary. My system seemed more stable in the older versions.

---

### Post by pauldoo on 2008-05-22
I'm using normal Ubuntu (8.04) and I experienced random freezes until I uninstalled "powernowd".

[http://ubuntuforums.org/showpost.php?p=4674219&postcount=15](http://ubuntuforums.org/showpost.php?p=4674219&postcount=15)

---

### Post by tcpankon on 2008-05-23
I will be trying this once I get out of work.  You will be my hero if this works as I have been banging my head against the desk about this one for about a month now...Nothing worse than having the backend lock up in the middle of a recording...or even worse, lock up while the wife is trying to watch something.

I will post the results in a couple days to see if it fixes stability issues.

---

### Post by wootah on 2008-05-23
> **gazer22 said:**
> Good reference page here:  [COLOR="Blue"][Linux Server Performance Monitoring- When Do I Need A Memory Upgrade]("http://itmission.org/Main/LinuxServerPerformanceMonitoringCheckAndDetermineWhenDoINeedAMemoryUpgrade")[/COLOR]

I'm not really apart of this thread, but I was reading through and noticed this post! Excellent reference you have there! :)

---

### Post by difosfor on 2008-05-24
I was also experiencing freezes and segfaults all over the place (mythfrontend, mythfilldatabase, apache2, ..) with the mysql tables corrupting regularly. 
What seems to be working for me now is the same kernel boot option I used to solve my installation problems (also see [thread 795533]("http://ubuntuforums.org/showthread.php?t=795533")): 

generic.all_generic_ide=1

Add that to the end of your "# kopt=root=.." line in /boot/grub/menu.lst, run update-grub and reboot.

Update: It seems I was cheering too soon as I found a bunch of apps segfaulting again this night :(

---

### Post by Nikas on 2008-05-26
> **difosfor said:**
> I was also experiencing freezes and segfaults all over the place (mythfrontend, mythfilldatabase, apache2, ..) with the mysql tables corrupting regularly. 
What seems to be working for me now is the same kernel boot option I used to solve my installation problems (also see [thread 795533]("http://ubuntuforums.org/showthread.php?t=795533")): 

generic.all_generic_ide=1

Add that to the end of your "# kopt=root=.." line in /boot/grub/menu.lst, run update-grub and reboot.

Update: It seems I was cheering too soon as I found a bunch of apps segfaulting again this night :(

Too bad. :(

I get this from "dmesg | grep ide":

```
[    0.000000] Kernel command line: root=UUID=98bb856d-5c12-4a7a-bfe4-561ba3e125bf ro generic.all_generic_ide=1 quiet splash
[    0.000000] Unknown boot option `generic.all_generic_ide=1': ignoring
```

---

### Post by difosfor on 2008-05-27
Well spotted Nikas! That proves it's of no use outside of the installation kernel.

The search for a solution continues..

---

### Post by TonyGould on 2008-06-24
> **pauldoo said:**
> I'm using normal Ubuntu (8.04) and I experienced random freezes until I uninstalled "powernowd".

[http://ubuntuforums.org/showpost.php?p=4674219&postcount=15](http://ubuntuforums.org/showpost.php?p=4674219&postcount=15)

I'm using Mythbuntu 8.04 on Asus Pundit P1-AH2. I'm v hopeful that this has fixed my problem -- thanks. I was getting random crashes every few hours as reported here. Also reboot hung, transcoding recorded video files was about half as fast as it should have been, and the system felt generally sluggish (so much so I was considering reverting to 7.10). With powernowd removed, reboot now works, and transcoding very fast, and the system feels responsive again. Hopefully the random hangs have gone too!

Tony.

---

### Post by TonyGould on 2008-06-26
> **TonyGould said:**
> Hopefully the random hangs have gone too!

unfortunately the hangs persist :(, even tho the m/c is much faster. Any ideas would be welcome. I guess I should memory check the machine, and then perhaps try reverting back to previous kernel and maybe graphics card drivers.

---

### Post by nfoti on 2008-07-08
I'm experiencing the backend hangs as well. The backend locks up, continues to run - according to top, but is unresponsive.

The backend log fills with:

2008-07-07 21:28:57.026 MythSocket(ab915f70:23): writeStringList: No data written on writeBlock
2008-07-07 21:29:02.401 MythSocket(ab915f70:23): writeStringList: No data written on writeBlock

over and over.

[URL="http://50dollarsoap.blogsite.org/mythbackend.log"]
mythbackend.log[/URL]
[mythfrontend.log]("http://50dollarsoap.blogsite.org/mythfrontend.log")

I'm running a fresh install of mythbuntu 8.04 with all updates installed. I did not experience these problems with Gutsy or earlier.

It seems to me that this problem is not mythbuntu specific as I've read several posts elsewhere.

Any help appreciated - Thanks.

---

### Post by buntunub on 2008-07-08
Not sure if its related or not, but I got these random lockups when using Mythtv as well and narrowed the cause down to NFS. Far as I can tell, MythBuntu uses NFS for its remote backend setup, and I was having a ton of issues with that so I switched over to using NFSv4 and all is now working well. Also, messing around with the fstab and export settings seemed to help out a great deal as well (soft vs. hard, etc). When NFS is set to hard mount it causes the system to thrash if it somehow loses connection to the backend.

---

### Post by nfoti on 2008-07-08
Thanks for the suggestion. I run my backend and frontend on the same machine - so I don't think it's an issue related to NFS network shares.

One thing to note though, although the frontend is unable to connect to the running backend, the backend still records programs just fine. Very bizarre.

Restarting the backend allows the frontend to connect and view the new recordings.

I do notice the Mythsocket errors in both the frontend and backend logs and am beginning to think that is the culprit. 

I also get a another worrisome comment in my frontend log:
2008-07-07 21:06:30.397 Connecting to backend server: 192.168.1.16:6543 (try 1 of 5)
2008-07-07 21:06:37.441 MythSocket(b30b7b60:25): readStringList: Error, timeout (quick).
2008-07-07 21:06:37.441 Unexpected response to MYTH_PROTO_VERSION: 

I've read that the MYTH_PROTO_VERSION error occurs when you are using differing version of mythfrontend and mythbackend. I'm running a fresh install with current updates so why the VERSION error?

Thanks

---

### Post by thespirit3 on 2008-07-09
Very interesting!

I've been having random complete lockups when hammering the box.  The machine seems stable running just the back and front ends, but start several rsyncs and the box will lock solid within minutes.

I'm using a Nova-T-500 dual tuner PCI card which has known issues with some riser cards and/or VIA chipsets.  I have an Nvidia chipset and don't use a riser card - but thought due to reported Nova-T-500 issues it was possibly related.   

However, judging by the comments in this thread - it may not be anything to do with the Nova-T-500.

I don't seem to log anything before a crash, and the box dies without warning (no disk thrashing).   This was a clean install of 8.04, fully patched, 1Gb RAM and 2gb SWAP.

Incidentally I do get the strobing IDE/SATA light issue - where the case LED indicates constant activity (on for a second, off for a second, repeat) - but with no audible head movement.   I've mentioned this before but no-one ever got to the bottom of it.

Anyone else have a strobing activity light?

Anyone else using a NOVA-T-500?


Steve

---

### Post by nfoti on 2008-07-11
I'm happy to report that after two days my system is still running, with no mythbackend lock ups!

I ran mythtv-setup, deleted all capture cards (more on this in a second), and re-added all of my capture cards. Since then I have not had a lock up!

I failed to mention in previous posts that I am running a fresh install with my old mythtv .21 mythconverg db uploaded. When I re-installed 8.04 I renamed the server on accident. When I ran mythtv-setup I found it odd that my capture cards were not listed, then proceeded to add them again. I think - this may have created a problem with the frontend or backend trying to access non-existent capture cards causing a crash. Live and learn.

Thanks for the suggestions.

---

### Post by Balachmar on 2008-10-09
So were these issues resolved?
Because I updated my system last week (Haven't done that for a long while) And now I also get a lockup and a flashing caps lock indicator.

So what is the solution?
Removing powernowd? --> I just checked it is not installed on my htpc
Making sure the hds are being used with their uid's? --> this is also done...

NFS is no problem in my case, since it is a combined back/frontend.
And also the tunercards shouldn't be a problem, since they behaved fine before and only one person resolved his problems by fiddling with those...

What magic solution did I miss?

---

### Post by chrisblue on 2008-10-09
I am also have random lockups. A new box with all new hardware and a clean install of Mythbuntu 8.04, only have SATA drives, 2 GB RAM (though I will MEMTEST that tonight)

Now having problems even getting the box to boot so will have to sort that out first.

---

### Post by Balachmar on 2008-10-11
I really don't know what it is now, because I now am using the older kernel. But I still have the lockup!
If anyone knows how to fix it, feel free to respond! :)

---

### Post by Nikas on 2008-10-11
I am using the kernel from 7.10 with 8.04. Works but i cant use the new kernel that came with 8.04. The computer locks up when it is much disk activity with the newer kernel.

I dont know if i dare to try 8.10.

---

### Post by Balachmar on 2008-10-11
> **Nikas said:**
> I am using the kernel from 7.10 with 8.04. Works but i cant use the new kernel that came with 8.04. The computer locks up when it is much disk activity with the newer kernel.

I dont know if i dare to try 8.10.

How did you make it use the kernel from 7.10?

---

### Post by Nikas on 2008-10-11
> **Balachmar said:**
> How did you make it use the kernel from 7.10?

You can choose older kernels from grub at boot (press esc before grub starts to load the kernel) if you have upgraded from 7.10 to 8.04. Edited my /boot/grub/menu.lst to always use the older kernel too.

---

### Post by Balachmar on 2008-10-12
> **Nikas said:**
> You can choose older kernels from grub at boot (press esc before grub starts to load the kernel) if you have upgraded from 7.10 to 8.04. Edited my /boot/grub/menu.lst to always use the older kernel too.
Could you specify which kernel you are using at the moment?

---

### Post by Nikas on 2008-10-12
> **Balachmar said:**
> Could you specify which kernel you are using at the moment?

niklas@mythtv:~$ uname -r
2.6.22-14-generic

:)

---

### Post by Balachmar on 2008-10-12
ok, sorry to bother you again, but I am unable to install that kernel through the repos. Any hint on how to get it installed?

---

### Post by rukie on 2008-10-12
About 7:30pm last night my machine locked up.
Since then, I can't get it to boot into the xfce desktop. It loads in recovery just fine, but if I go through a normal boot up, it hangs at the "Loading Desktop", and if I press alt f1, and look at syslog its sitting at loading /etc/rc.local or something..

The harddrive light just sits at 100% activity, so I'm not sure whats going on. Any ideas? I haven't really changed anything recently, other than an hd 2400 ati video card.. It runs both the front and backend but it basically just sits there and holds files.

anyways, thanks for any help.

---

### Post by Balachmar on 2008-10-13
I took the plunge of upgrading to 8.10
So far everything seems fine. Will keep you posted!

Seems to work better although I needed to add a udev thingy to get /dev/rtc working again. (This was needed for nvram-wakeup)
And I need network manager to automatically connect to wireless... But I did that before... somehow...

---

### Post by niceguy167 on 2008-10-15
Not sure if this helps any, but I am running fedora core 8 with kernel 2.6.26.5-28 I have the same problems.... I was running a master and a slave but took the slave offline thinking it would fix the master.. It of course has not... So I get the same symptoms box runs perfect for a couple of hours or more. Looking at my logs they seam to come in randomly but on this particular day I found these errors in the log when it was running mythfilldatabase. Maybe that might have something to do with it. I don't think so but maybe. It’s also totally random when it happens so far. (box running and recording fine then all of a sudden write error|) I know I’m not on Mythbuntu but it might help that it’s happening on another distro :) if I get time I was going to compile an older kernel and try that :) I am leaning more towards something in kernel??? Because I had FC7 installed with mythtv version 0.21-192.FC7 running an older 2.5 kernel then I updated the box to FC8 running mythtv version 0.21-192.FC8 and this problem started. I have also tried grabbing a new copy of FC8 and installed fresh and still get these problems. Hopefully this can help someone out figure out this problem. 

My logs are below thanks  

P.S. When this is going on the mythbackend service is running 90-100% cpu and browsing and watching is impossible as its that slow also if you get tv its all mangled and garbaged....

```

2008-10-15 03:47:34.061 DataDirect: Your subscription expires on 06/27/2009 10:07:10 AM
2008-10-15 03:47:37.121 New DB connection, total: 3
2008-10-15 03:47:37.175 Connected to database 'mythconverg' at host: localhost
2008-10-15 03:47:37.201 sourceid 1 has lineup type: Satellite
2008-10-15 03:49:41.839 Grab complete.  Actual data from Thu Oct 16 06:00:00 2008 to Fri Oct 17 06:00:00 2008 (UTC)
2008-10-15 03:49:41.886 Main temp tables populated.
2008-10-15 03:49:41.926 Updating myth channels.
2008-10-15 03:49:44.453 Updating icons for sourceid: 1
2008-10-15 03:49:44.548 Channels updated.
2008-10-15 03:49:49.598 Clearing data for source.
2008-10-15 03:49:49.627 Clearing from Thu Oct 16 00:00:00 2008 to Fri Oct 17 00:00:00 2008 (localtime)
2008-10-15 03:49:49.689 New DB connection, total: 4
2008-10-15 03:49:49.713 Connected to database 'mythconverg' at host: localhost
2008-10-15 03:50:05.720 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-10-15 03:50:17.825 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-10-15 03:50:26.702 TFW, Error: Write() -- IOBOUND end
2008-10-15 03:51:03.572 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-10-15 03:51:08.586 TFW, Error: Write() -- IOBOUND end
2008-10-15 03:51:30.997 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-10-15 03:51:38.244 TFW, Error: Write() -- IOBOUND end
2008-10-15 03:51:39.099 mythfilldatabase still running, skipping checks.
2008-10-15 03:51:59.922 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-10-15 03:52:08.113 TFW, Error: Write() -- IOBOUND end
2008-10-15 03:52:16.476 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-10-15 03:52:20.678 TFW, Error: Write() -- IOBOUND end
2008-10-15 03:52:47.472 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)
2008-10-15 03:52:55.134 TFW, Error: Write() -- IOBOUND end
2008-10-15 03:53:13.005 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(2047)

SOON AFTER THE ABOVE CODE I GET TONS OF THESE 2008-10-15 04:03:30.424 MythSocket(a5c12d0:19): writeStringList: No data written on writeBlock
2008-10-15 04:03:39.879 MythSocket(a5c12d0:19): writeStringList: No data written on writeBlock
2008-10-15 04:03:50.497 MythSocket(a5c12d0:19): writeStringList: No data written on writeBlock
2008-10-15 04:04:00.611 MythSocket(a5c12d0:19): writeStringList: No data written on writeBlock
2008-10-15 04:04:11.695 MythSocket(a5c12d0:19): writeStringList: No data written on writeBlock

They Happen All Night Long

```

---

### Post by niceguy167 on 2008-10-23
so far my issue is resolved. discovered defective ram in computer. also hard drive setup was not getting enough i/o and thus write error :)

---

### Post by Nikas on 2008-10-31
Anyone got better luck with 8.10?

---

### Post by Balachmar on 2008-11-09
I did, it is better now, however I am still having random lockups although less often. I will investigate the RAM module.

---

### Post by jacksonz123z on 2008-12-04
Yes no freezes so far, pleased I upgraded to 8.1.

---

### Post by jacksonz123z on 2008-12-15
No I was wrong 8.1 freezes just like 8.04!

---

### Post by jacksonz123z on 2008-12-22
Well for the record I fixed the freezing by replacing the video card. I was using a Radeon 9200, it seemed to work OK in the computer using the default ati driver.  I replaced it with a Radeon 9000 that has completely resolved the problem. At least in my case the video card was the issue. I hope this helps somebody else.

---

