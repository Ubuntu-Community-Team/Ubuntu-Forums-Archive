---
title: "Init scripts stop working after upgrade from mythbuntu 9.10 to 10.04"
date: 2010-05-03
forum: Mythbuntu
---

### Post by ardnut on 2010-05-03
I've recently upgraded to mythbuntu 10.04 and I've noticed that apache no longer automatically starts at boot.  If after booting I manually run /etc/init.d/apache2 start then mythweb works.  I've tried removing and adding it again using update-rc.d but that doesn't resolve the issue.  I also have another init.d script I wrote for setting up wakeonlan to work but that no longer runs at boot/shutdown either.

I know the init.d scripts are slowly being replaced by upstart but I thought it was still backwards compatible?

I don't mind replacing the init.d script with a new apache upstart one (and my wakeonlan one just runs one command on shutdown) so how do I fix this?

Thanks,
Ash

---

### Post by picbits on 2010-05-03
Try the command :

runlevel

If you get "unknown" then try this:

telinit 2

or 

telinit 3 if the above 2 doesn't work

If everything runs fine then you have the same problem as me - fresh 10.04 Server install then Desktop installoed over the top.

It looks like its **might** be the latest version of Upstart messing about because of the Network Interfaces file but thats only what I've managed to glean over the past couple of hours worth of research.

Let me know if the above does anything for you,

---

### Post by db260179 on 2010-05-04
There does seem to be a lot of old balls things going wrong.

For example on my Dad's htpc, going from Ubuntu 8.04 to 10.04 these things are now a problem.

1. Will not automatically login - Removing gdm and clearing config, works once - then after a reboot the same problem reappears! - Still not fixed!

2. All the SAA7134 cards I have tested have issues with the linux-nonfree firmware, using the get_firmware.pl from linuxtv.org and using the lifeview firmware cures the problem for all the cards. (example. Firmware failed 0 when booting). This is particularly and issue with Amd x2 processors.

3. ACPI wakeup no longer works as the location of the RTC in the kernel has changed and obviously because of the use of upstart all the scripts are now located in /etc/init

It's been a learning curve. Hopefully get this fixed and pass the info onto you guys/girls.

Please reply if you have any info on this!

---

### Post by ardnut on 2010-05-04
I'll have to do more testing this evening, I checked it again quickly yesterday and apache seemed to have started ok without me manually running the init.d script.  Very odd indeed.

---

### Post by picbits on 2010-05-04
Mine has worked for the first time in ages today. Nothing has been changed although it may be the difference between a cold boot and a soft reboot.

---

### Post by ardnut on 2010-05-04
Hmmmm... very bizarre indeed, sometimes apache is started on boot and other times it isn't, I'm failing to see a pattern in when it works vs when it doesn't.

Being unfamiliar with init.d vs upstart could anyone help with where I should look to debug this further?  Should all my init.d scripts be replaced with equivalent upstart ones, and if so how?

Thanks,
Ash

---

### Post by vmpho on 2010-05-04
I have same issue, I fresh installed 10.04 32-bit then installed Mythbuntu 10.04 from web.

MythWeb failed and also my VMWare workstaion 7 also failed to start properly, I have to start those services manually:-

For apache[FONT=Arial]
sudo /etc/init.d/apache2 restart[/FONT]  

For VMware[FONT=Arial]
sudo service vmware start[/FONT] 

However it sometimes work fine after reboot .

Other than services not start properly, sometimes my another ext4 volume failed to mount automatically during bootup. "Error message somthing like S to Skip M to manaually..."

Did some google search, it pointing to Plymouth & Upstart new features in Ubuntu 10.04.

Anyone knows how to fix it ?

:frown::frown::frown::frown:

---

### Post by paoleary on 2010-05-04
> **ardnut said:**
> Should all my init.d scripts be replaced with equivalent upstart ones, and if so how?

One of the explicit requirements of upstart is that it is backwards compatible with sysvinit scripts, so this *shouldn't* be necessary.  Whether it is needed in practice I do not know.

---

### Post by picbits on 2010-05-05
Well mine was having another strange one today.

Booted it up and checked it was serving up pages - no problem there.

Went to the MythWeb on it and it was all there but hadn't recognised any tuners.

Restarted Mythbackend through /etc/init.d/mythtv-backend restart and everything was fine again.

Cold and warm booted it and its still behaving.

---

### Post by ardnut on 2010-05-05
Even more weirdness, I figured I'd completely uninstall apache (sudo aptitude purge apache2) then reinstall it, but now I have no way of starting it!

$ sudo service apache2 start
apache2: unrecognized service

$ sudo /etc/init.d/apache2 start
sudo: /etc/init.d/apache2: command not found

So now I have no upstart or init.d scripts.

---

### Post by ardnut on 2010-05-05
Posted too soon, figured apache2 is a meta package and I had to purge apache2.2-bin package then reinstall that.

I've now done an apt-get purge and reinstall for the services (apache, lcdproc, etc...) that were causing me issues and now after many reboots of testing it seems to have fixed the problems I was having.  Assuming this now continues working I can only guess that the previous init.d scripts from my upgrade were somehow not compatible with the newer upstart/init system of Ubuntu 10.04.

Ash

---

### Post by ardnut on 2010-05-14
I thought the above had fixed the problem but I'm still having issues with apache sometimes not starting at boot.

I did track down what was causing my runlevel not to be set... I ended up reseting my /etc/network/interfaces file back to basics and now use the network-manager gui to configure a static IP. So I now get a correct runlevel set at boot, which I thought would fix the issue but it hasn't :(

Any other ideas on how to debug this? I can't find anything in the logs.

---

### Post by picbits on 2010-05-14
When mine fails, I usually get a line in /var/log/syslog which reads 

```
May  9 08:42:26 pbhp init: Failed to spawn rc main process: unable to open console: Input/output error
```

---

### Post by ardnut on 2010-05-14
I'm seeing those as well, looks like this bug...
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

Ash

---

### Post by picbits on 2010-05-14
Mine has behaved itself for the past few days but this is a production server so I need to be 100% confident in it. 

Time will tell ......

---

### Post by picbits on 2010-05-21
Getting really cheesed off now. 

Just done a clean install onto a Revo R3600, installed Lirc and everything went well until a reboot and now I'm having exactly the same problems

Apache, Lirc and some other services in init.d will not start automatically on boot.

---

### Post by ian dobson on 2010-05-21
Hi,

Have a look in  /var/log/boot.log there is a list/status messages for the boot process. It could well be that upstart is trying to start demons before all dependancys are met (start apache before network is up).

Regards
Ian Dobson

---

### Post by picbits on 2010-05-21
Thanks for finding one of my other "moaning" threads Ian :)

boot.log gives me this:

```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 153997/2445984 files, 1067505/9764864 blocks
ripped: clean, 12/6963200 files, 949541/27840645 blocks
init: ureadahead-other main process (651) terminated with status 4

```

Any clues ?

---

### Post by picbits on 2010-05-21
I thought I'd just sussed it - found some info about ureadahead not liking multiple mounts or something. 

I turned off the external USB DVD drive and rebooted - everything worked :)

Result of boot.log:

```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 153995/2445984 files, 1067555/9764864 blocks
ripped: clean, 12/6963200 files, 949541/27840645 blocks
init: ureadahead-other main process (586) terminated with status 4

 * Starting AppArmor profiles       ^[[80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

^[[74G[ OK ]
Loading the saved-state of the serial devices...
 * Setting sensors limits       ^[[80G
^[[74G[ OK ]
 * Loading LIRC modules       ^[[80G
^[[74G[ OK ]
 * Starting remote control daemon(s) : LIRC        ^[[80G
^[[74G[ OK ]
 ^[[33m*^[[39;49m Speech-dispatcher configured for user sessions
 * Starting Common Unix Printing System: cupsd       ^[[80G
^[[74G[ OK ]
 ^[[33m*^[[39;49m PulseAudio configured for per-user sessions


```

Rebooted (still with DVD off) and had exactly the same problem :(

Boot.log (now not working again)

```

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 153996/2445984 files, 1067607/9764864 blocks
ripped: clean, 12/6963200 files, 949541/27840645 blocks
init: ureadahead-other main process (627) terminated with status 4

```

---

### Post by picbits on 2010-05-21
And rebooted again and everythings working (with the second longer boot.log message again)

So to sum it up ....

Had around 10 reboots - scripts in init.d wouldn't start
Turned off external USB DVD drive - scripts started
Rebooted - scripts not started
Rebooted - scripts started

Have rebooted 4 times now - scripts starting each time

Powered off Revo, powered back up - still working

Very strange.

---

### Post by picbits on 2010-05-21
And just rebooted again and none of the scripts have run.

I've done absolutely nothing whatsoever on the Revo other than SSH into it, SUDO SU and then reboot.

---

### Post by picbits on 2010-05-21
2 more reboots and its working again

Each time it fails, if I type "runlevel" I get "unknown"
When its working I get "N 2"

When its working I get the longer message above in boot.log. When its not, the boot.log ends at "init: ureadahead-other main process (719) terminated with status 4"

Its very random, follows no pattern and seems incredibly unreliable.

---

### Post by ian dobson on 2010-05-21
Hi,

Can you try just removing ureadahead. I'd like to see if your box has a problem with ustart/ureadahead (I don't think there can be a problem as my frontend has both active and it always works)

Regards
Ian Dobson

---

### Post by picbits on 2010-05-21
Any easy way of doing this ? Is it an apt-get remove ureadahead ?

---

### Post by picbits on 2010-05-21
P.s. spent 3 days getting this machine to this point so I dont want to bork it lmao

---

### Post by ian dobson on 2010-05-21
Hi 

Yep apt-get remove ureadahead.

Wow that was quick.

Regards
Ian Dobson

---

### Post by picbits on 2010-05-21
Back in 5 ......

---

### Post by picbits on 2010-05-21
Ok - so far so good - its booting as it should, the jobs are running.

I ran sudo apt-get remove ureadahead

Interestingly, I'm getting this in boot.log now

```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 153982/2445984 files, 1067992/9764864 blocks
ripped: clean, 12/6963200 files, 949541/27840645 blocks
init: ureadahead-other main process (739) terminated with status 2

mountall: Event failed
 * Starting AppArmor profiles       ^[[80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

^[[74G[ OK ]
Loading the saved-state of the serial devices...
 * Setting sensors limits       ^[[80G
^[[74G[ OK ]


```

Back in a few reboots to report back.

---

### Post by ian dobson on 2010-05-21
Hi,

Have you removed ureadahead? This doesn't look too nice :-mountall: Event failed

What do you have in your fstab?

Regards
Ian Dobson

---

### Post by picbits on 2010-05-21
Sorry - got sidetracked sorting out compound mortgage calculations for the wife - she was nearly missold a mortgage earlier lol.

Still working ok on the reboots - no failed scripts yet.

fstab reads:

```
 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=df8dfdda-960b-491e-86e5-53944849c679 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4e28dfa5-ade5-488c-a1ba-ef8a460b8e43 none            swap    sw              0       0
UUID=49be4ea7-5e57-4baa-8bbd-81dc22b78659 /media/ripped   ext4    errors=remount-ro 0   1

```

---

### Post by picbits on 2010-05-21
5 reboots and one power cycle and still working.

---

### Post by picbits on 2010-05-21
5 more reboots and still working.

Will report back tomorrow with more results :)

---

### Post by picbits on 2010-05-22
Still working this morning after numerous reboots. 

I've not had a single failure yet since removing the ureadahead.

---

### Post by ian dobson on 2010-05-22
Hi,

so it looks as if ureadahead is causing deamons to start too quickly (when upstart starts them) so that upstart doesn't realise the deamon is started.

Or maybe ureadahead is causing deamons to start before upstart is finished starting up, which is causing upstart to not see the inital events.

A silly question your you seeing a slowdown after disabling ureadahead? How fast is your boot drive/what are the specs for your boot drive.

Regards
Ian Dobson

---

### Post by picbits on 2010-05-22
Well the actual machine is an Acer Revo R3600 with 1Gb Ram and a 160gb 2.5" Hard drive so its never going to be that fast.

I've put on a standard Ubuntu 10.04 64 bit desktop, latest Nvidia graphics drivers, MythTv and Lirc so not a lot really.

Boot time feels about the same - from when it starts to boot to when the desktop appears is 38 seconds. It actually not that much slower to boot than my Bluray DVD player which is Linux based so quite happy with that.

I'm not a speed freak to be honest with you, I'd much rather something worked than was 10 seconds faster to boot.

Disk speed is pretty horrendous - here's the output of hdparm -tT /dev/sda 

```
/dev/sda:
 Timing cached reads:   1352 MB in  2.00 seconds = 675.51 MB/sec
 Timing buffered disk reads:  178 MB in  3.02 seconds =  58.94 MB/sec

```

---

### Post by ian dobson on 2010-05-22
Hi,

I've started to look into upstart and it looks as if ureadahead-other is started by upstart after mount-all is called, and ureadahead is started when / is mounted.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-05-23
Hi,

OK, I've now switched my brain on and started to try and decode the actual startup sequence from ustart/ureadahead (well actually I'm writing a depedancey script that looks at the start on/emits messages in the upstart configuration).

What I've found is that ureadahead-other starts when a file system is mounted and ureadahead starts when mountall is started (not when it's finished). This looks really racey to me.

Regards
Ian Dobson

---

### Post by picbits on 2010-05-23
> **ian dobson said:**
> Hi,

OK, I've now switched my brain on and started to try and decode the actual startup sequence from ustart/ureadahead (well actually I'm writing a depedancey script that looks at the start on/emits messages in the upstart configuration).

What I've found is that ureadahead-other starts when a file system is mounted and ureadahead starts when mountall is started (not when it's finished). This looks really racey to me.

Regards
Ian Dobson

I love you (in a non homosexual kind of way) :guitar:

P.s. I've not had one single init script boot failure since removing ureadahead.

---

### Post by ian dobson on 2010-05-24
Hi,

No worries, I'm man enough to understand what you mean.

OK, I can now reproduce your problem on my mythfrontend (C2D underclocked but boots from a very fast CF card). I've changed the kernel parameter to use ext4 (file system is still ext3 due to grub 0.97) and one in about 5-6 boots lirc doesn't start up if I have ureadahead enabled.

Looking in dmesg/boot.log it seems as if upstart doesn't see any events that should cause the remaining jobs to kick in.

The backend code to look at the dependancy/event tree for upstart processes is almost finished (I just need to work on multiline start on event and event) but I'm not sure how to display the results in a logical mannor. Some sort of spiders web of events/actions would be cool but I'm not sure how to programm it at the moment (backend uses perl).

Regards
Ian Dobson

---

### Post by ian dobson on 2010-05-24
Hi picbits,

Can you do me a small faviour. I think I've found something :P on my frontend the mount count for / was higher than the maximum count allowed before a fsck should be forced. But no fsck was forced on boot. After forcing a fsck, lirc started as expected (5 times in a row).

So can you do a :-
 tune2fs -l /dev/sda1 | grep -i "mount count"

Where sda1 is your boot drive. The dump the results here.

Regards
Ian Dobson

---

### Post by picbits on 2010-05-24
> **ian dobson said:**
> Hi picbits,

Can you do me a small faviour. I think I've found something :P on my frontend the mount count for / was higher than the maximum count allowed before a fsck should be forced. But no fsck was forced on boot. After forcing a fsck, lirc started as expected (5 times in a row).

So can you do a :-
 tune2fs -l /dev/sda1 | grep -i "mount count"

Where sda1 is your boot drive. The dump the results here.

Regards
Ian Dobson

Hi Ian

This is still with my ureadahead disabled:

```
root@revo:/home/dom# tune2fs -l /dev/sda1 | grep -i "mount count"
Mount count:              21
Maximum mount count:      37

```

Dom

---

### Post by ian dobson on 2010-05-24
> **picbits said:**
> Hi Ian

This is still with my ureadahead disabled:

```
root@revo:/home/dom# tune2fs -l /dev/sda1 | grep -i "mount count"
Mount count:              21
Maximum mount count:      37

```

Dom

OK then I'll look abit more. This ureadahead/ureadahead-other startup in upstart still looks very racey too me, and the more I look at it the more I think it's unsafe/relies too much on mounted/mount-all startup comming at exactly the right point.

Regards
Ian Dobson

---

### Post by picbits on 2010-05-24
No problem - just let me know if you need to try anything else. I might be a bit slow with replying today as I'll mostly be hitting my car with a large hammer to try and get that working.

---

### Post by ian dobson on 2010-05-25
Hi,

Why do you need a car to repair your hammer?

I'll be out of the country for the next few days, so I don't think I can work on the init scripts for awhile.

Regards
Ian Dobson

---

### Post by picbits on 2010-05-25
I'm not in any desperate hurry now that its all working.

Obviously it would be nice to find out exactly what was causing the problem but for the moment everything it working as it should (without ureadahead).

Thanks for your effort looking at this - its much appreciated.

Dom

---

### Post by ian dobson on 2010-05-29
Hi,

I've played about with upstart abit more, and I've got to the point where I can't really say what's wrong. Sometimes my system boots without any problems and everything works (90% of the time). Othertimes mybe lirc doesn't start up (old style init.d script), or networking doesn't startup (upstart script).

I've written a small upstart script (it just logs event and time to a file)that is called by most events and sometimes the log file is empty othertimes all events are logged correctly.

It looks as if upstart just doesn't fire the events in the correct order or just doesn't call some scripts, it looks alot like a race condition that could be worse/error more often when ureadahead is active due to the reduced loading time.

OK. Now that my MythTV frontend box is totally screwed up I'll reload the backup before my wife wants to watch TV.

Regards
Ian Dobson

---

### Post by ardnut on 2010-05-29
Not sure if you guys missed my post back on page 2 but this is the bug for the problem I'm having...
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

There's a solution which seems to be working for me posted there as well.

Ash

---

### Post by picbits on 2010-05-29
> **ian dobson said:**
> 
OK. Now that my MythTV frontend box is totally screwed up I'll reload the backup before my wife wants to watch TV.

Regards
Ian Dobson

Thanks for spending the time to have a look at this Ian - its appreciated. I've had no further problems on mine since removing ureadahead - I might try it on the server as well and see if that fixes things.

ardnut - I've had that link bookmarked for a while but forgot to check back over the past few days. Will have a read through it now :)

---

### Post by ian dobson on 2010-05-29
> **ardnut said:**
> Not sure if you guys missed my post back on page 2 but this is the bug for the problem I'm having...
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

There's a solution which seems to be working for me posted there as well.

Ash

Hi,

Thanks for the tip. I've disabled console output for all files and have been able to boot 6 times in a row before my wife wanted to watch TV (Mankells Wallander).

Regards
Ian Dobson

---

### Post by picbits on 2010-05-29
Hmmm will have to try that solution when I've got some spare :)

---

