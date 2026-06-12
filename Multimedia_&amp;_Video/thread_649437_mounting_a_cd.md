---
title: "mounting a cd"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by dsimpson on 2007-12-24
How do you mount a cd? I checked the cd-rom properties and under the Volume tab it says;
Mount Point , File Point , Mount Options. and behind each one it states Not Mounted

Under that it says Settings,
And under setting it gives boxes to enter Mount Point, File Point, Mount Options.

You can assign or fill the boxes there but I don't know what each means and how to do it.
Anyone out there that can help with this. This is for a blank cd for recording.

I can play audio cd's ok, view data cd's but want to open to write to a blank cd.

---

### Post by LateralusBWRY on 2007-12-24
Try going to Places>CD/DVD creator and it should open up in the finder. Then just drag the files you want to burn into that window. Hit Write to Disc button in upper right and your done. I don't think you need to worry about anything under the properties like filling out mount point and such

LateralusBWRY

---

### Post by dsimpson on 2007-12-25
I am trying to write an .iso image to a cd and by moving to cd/dvd creator, i did move the image but it still requests that I insert a disc in the cd player, and that will not mount a blank cd for me. Thanks for the idea tho. NEXT!

---

### Post by dsimpson on 2007-12-28
Can we try this again, seeking cdrom techno wizards, help me find an answer.

---

### Post by Yellow Pasque on 2007-12-28
Let's look at your /etc/fstab file to see if it's set to auto-mount. Post that plz.

For example, my cd burner entry looks like:
```
/dev/cdrom /mnt/cdrom   auto   user,auto,unhide   0      0
```

Yours may look a little different (probably mounts to /media/cdrom0) because I'm on Arch Linux at the moment.

---

### Post by dsimpson on 2007-12-28
here is what is on my etc/fstab;

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


The first one "hdc" is my cdrw while the second one "hdd" is my cdrom/dvd+-rw.
This is only the lines that pertain to the cd drives. The difference I see between your file and what I have is the portion after user, mine says noauto while yours says auto. What is the relevance of that?

---

### Post by dsimpson on 2007-12-30
bumping this back for **temujin**, here is the data from my files. Do I just make the changes to auto and save or is there more? I would like to resolve this, thanks!

---

### Post by Yellow Pasque on 2007-12-30
Sorry to leave you hanging. I've been busy/distracted this weekend. Yes, change the option to auto. If the CD still isn't mounting, go to a terminal and type sudo mount -a and that should mount it. We would then have to figure out why nautilus/gnome isn't auto-mounting. It may be a user/group permissions problem.

---

### Post by Yellow Pasque on 2007-12-30
Ok, just to make sure.. sudo gedit /etc/group and make sure your user is listed in the cdrom and floppy groups.

---

### Post by dsimpson on 2007-12-30
Temujin, here is what I got when I used terminal the mount the cd.

:~$ sudo mount -a
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: No medium found
mount: /dev/fd0 is not a valid block device

This is puzzling, when I put the cd in the drive, the disc icon shows on the desktop, but I am unable to mount and write to Disc. What is fs type, superblock, and the missing codepage. It seems to give a hint on useful info in syslog, but how to you access that?

---

### Post by dsimpson on 2007-12-30
Additionally here is what I received when I put dmesg | tail. Does this tell you anything more about what the problems might be?

---

### Post by mc4man on 2007-12-30
Just noticed your having issues with another drive - logs are in system>administration>system logs
ck debug and messages

---

### Post by Yellow Pasque on 2007-12-30
I'm sorry that I misread your problem. I assumed you couldn't get any CD's to mount, not just blank ones.

If the disk icon appears on the desktop, then the disk is recognized. You can't mount a blank CD because it doesn't have a filesystem on it (hence the error message). If you want to create a data CD on Linux, you can't just open the device and write files to it as you would a floppy without some sort of CD-burning software. You may be used to doing it this way on Windows, because Windows (at least XP and later) has software like that built into it. On Ubuntu, you do something similar by using the folder for CD/DVD creation, which can be found under the Places menu in the top bar. If you use that, can you write to the drive or is it still not letting you write to the device?

Now we have to figure out why the device itself is read-only and won't let you write to it.
Did you:
```
sudo gedit /etc/group
``` as I suggested to make sure your user is listed in the cdrom and floppy groups?

---

### Post by dsimpson on 2007-12-30
/etc/groups for cd and floppy

cdrom:x:24:haldaemon,eaglesoldier
floppy:x:25:haldaemon,eaglesoldier

What is haldaemon, is that necessary in my file.

:~$ dmesg | tail
[220617.024829] attempt to access beyond end of device
[220617.024851] hdc: rw=0, want=1252, limit=4
[220617.025181] attempt to access beyond end of device
[220617.025189] hdc: rw=0, want=1028, limit=4
[220617.025477] UDF-fs: No partition found (1)
[220617.071576] attempt to access beyond end of device
[220617.071592] hdc: rw=0, want=68, limit=4
[220617.071910] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[220617.119514] end_request: I/O error, dev fd0, sector 0
[220617.143483] end_request: I/O error, dev fd0, sector 0

here is what came up in my syslog...

Dec 30 07:35:47 eaglesoldier-desktop syslogd 1.4.1#21ubuntu3: restart.
Dec 30 07:35:47 eaglesoldier-desktop anacron[9081]: Job `cron.daily' terminated
Dec 30 07:40:02 eaglesoldier-desktop anacron[9081]: Job `cron.weekly' started
Dec 30 07:40:02 eaglesoldier-desktop anacron[9267]: Updated timestamp for job `cron.weekly' to 2007-12-30
Dec 30 07:40:03 eaglesoldier-desktop syslogd 1.4.1#21ubuntu3: restart.
Dec 30 07:40:03 eaglesoldier-desktop anacron[9081]: Job `cron.weekly' terminated
Dec 30 07:40:03 eaglesoldier-desktop anacron[9081]: Normal exit (2 jobs run)
Dec 30 07:55:38 eaglesoldier-desktop -- MARK --
Dec 30 08:15:38 eaglesoldier-desktop -- MARK --
Dec 30 08:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9459]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 08:35:38 eaglesoldier-desktop -- MARK --
Dec 30 08:55:39 eaglesoldier-desktop -- MARK --
Dec 30 09:15:39 eaglesoldier-desktop -- MARK --
Dec 30 09:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9482]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 09:35:39 eaglesoldier-desktop -- MARK --
Dec 30 09:55:39 eaglesoldier-desktop -- MARK --
Dec 30 10:15:39 eaglesoldier-desktop -- MARK --
Dec 30 10:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9519]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 10:35:39 eaglesoldier-desktop -- MARK --
Dec 30 10:55:40 eaglesoldier-desktop -- MARK --
Dec 30 11:15:40 eaglesoldier-desktop -- MARK --
Dec 30 11:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9542]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 11:35:40 eaglesoldier-desktop -- MARK --
Dec 30 11:55:40 eaglesoldier-desktop -- MARK --
Dec 30 12:15:40 eaglesoldier-desktop -- MARK --
Dec 30 12:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9565]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 12:35:40 eaglesoldier-desktop -- MARK --
Dec 30 12:55:40 eaglesoldier-desktop -- MARK --
Dec 30 13:12:42 eaglesoldier-desktop NetworkManager: <debug> [1199049162.390926] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_empty_unknown'). 
Dec 30 13:12:50 eaglesoldier-desktop kernel: [220597.905592] cdrom: This disc doesn't have any tracks I recognize!
Dec 30 13:12:50 eaglesoldier-desktop NetworkManager: <debug> [1199049170.469220] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_empty_unknown'). 
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.011888] attempt to access beyond end of device
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.011909] hdc: rw=0, want=68, limit=4
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.024829] attempt to access beyond end of device
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.024851] hdc: rw=0, want=1252, limit=4
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.025181] attempt to access beyond end of device
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.025189] hdc: rw=0, want=1028, limit=4
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.025477] UDF-fs: No partition found (1)
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.071576] attempt to access beyond end of device
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.071592] hdc: rw=0, want=68, limit=4
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.071910] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.119514] end_request: I/O error, dev fd0, sector 0
Dec 30 13:13:09 eaglesoldier-desktop kernel: [220617.143483] end_request: I/O error, dev fd0, sector 0
Dec 30 13:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9676]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 13:35:41 eaglesoldier-desktop -- MARK --
Dec 30 13:55:41 eaglesoldier-desktop -- MARK --
Dec 30 14:15:41 eaglesoldier-desktop -- MARK --
Dec 30 14:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9792]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 14:35:41 eaglesoldier-desktop -- MARK --
Dec 30 14:55:41 eaglesoldier-desktop -- MARK --
Dec 30 15:15:42 eaglesoldier-desktop -- MARK --
Dec 30 15:17:01 eaglesoldier-desktop /USR/SBIN/CRON[9815]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 15:35:42 eaglesoldier-desktop -- MARK --
Dec 30 15:55:42 eaglesoldier-desktop -- MARK --
Dec 30 16:15:43 eaglesoldier-desktop -- MARK --
Dec 30 16:17:02 eaglesoldier-desktop /USR/SBIN/CRON[9915]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 16:35:48 eaglesoldier-desktop -- MARK --

Any of this help, this is what I wanted to post earlier but failed to, sorry about that, but here it is now.

---

### Post by mc4man on 2007-12-30
Again out of curiosity try booting up to the live cd and see if your Samsung can mount a dvd (assuming cd-rw is your boot drive )
Did you post whether your using 7.04 or 7.10 (if 7.10 - upgrade or fresh)

sorry meant to post to your other thread

---

### Post by Yellow Pasque on 2007-12-30
Ok, so what happens when you put the blank CD in, go to Places -> CD/DVD Creator, and try pasting some files? Still giving you write-protected error messages or what?

---

### Post by dsimpson on 2007-12-30
mc4man - tried the livecd and the same happens, it says unable to mount.

temujin - tried to write using cd/dvd creator and here is what I got...

Insert a rewritable or blank disc
Please put a disc, with at least 2.0 MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW

The disc type is cdr so it should work, but isn't.

I am using 7.10. just upgraded from 6.06 and didn't have any problems with this then, so I am thinking that it is something unique to GUTSY, trying to fix the problem..

As far a loading and playing cd's, I can play audio cd's without problems but am unable to write to a blank disc. I am writing to disc using cd/dvd creator and still nothing..

---

### Post by Yellow Pasque on 2007-12-30
Ok, now we're getting somewhere :P This thread has some possible fixes: [http://ubuntuforums.org/showthread.php?t=12133](http://ubuntuforums.org/showthread.php?t=12133)
The gconf editor it refers to can be installed with
```
sudo apt-get install gconf2 gconf2-common gconf-editor
```
You should now have a 'Configuration Editor' program under the Application -> System Tools menu. When you open it up you should see an 'apps' sub-menu. Pull that down and click on nautilus-cd-burner. Over in the right pane, check "overburn", "debug", and "burnproof".

Close that, reboot and try burning a CD again.

---

### Post by dsimpson on 2007-12-31
Hi, tried to install the gconf2 editor but this is what I received. Also under Applications, I cannot find any reference to System tools - Configuration editor......... Is this supposed to be listed under Applications? or under System - Administration etc....I can't seem to find any reference to this phantom editor...It says that gconf-editor is already the newest version....is there some way to enter using Terminal to enter gconf-editor and make the changes??


sudo  apt-get install gconf2 gconf2-common gconf-editor
[sudo] password for eaglesoldier:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gconf2 is already the newest version.
gconf2-common is already the newest version.
gconf-editor is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 123 not upgraded.

---

### Post by mc4man on 2007-12-31
You Don't need to install it , right click applications, edit menu's, and then add it from the system tools tree

edit: if what you mean by 'upgrading'' was using the update manager to upgrade from 6.06 to 7.10 then that has to be suspect for any odd or unexpected behavior.If reconfiguring or anything  else doesn't works a 'fresh' install of 7.10 is well worth trying. I noticed you had a 2nd hard drive where I assume you could backup most anything you needed. As far as the dvd-rom , if nothing else works physically removing(basically just removing ide cable from back of _drive_), a reboot / off cycle, and reinstalling can't hurt, there won't be any issue booting up without it as it's cabled in the slave position. If you do this and are unsure of anything ask first.

---

### Post by dsimpson on 2007-12-31
Thank you for the information. I have it on there now, am going to try the suggested fix and see if that works. Glad you are here to help.


I tried the changes referred to in the bug report and still no cd access, This is only happening with blank cd's with which I need to write data to, and am unable to get to work. I can get the audio cd's to play, but now have another problem, when I go to Places, Computer, there is no icon for the cdrw anymore. Something that has been done up to here took it away. HELP!

---

### Post by mc4man on 2007-12-31
refer to my edit of previous post - got to get to sleep

---

### Post by dsimpson on 2007-12-31
Thank you mc4man, have a good nights rest. I will sign off for today and try all this tomorrow evening. I will try the disconnect and see what that gets me.

Oh by the way, I rebooted and got my cdrw to reappear on Places-Computer, so I am happy about that.

---

### Post by Yellow Pasque on 2007-12-31
I'm almost out of ideas: One more though (inspired by [http://bugs.gentoo.org/show_bug.cgi?id=100460#c7](http://bugs.gentoo.org/show_bug.cgi?id=100460#c7))

Someone reported that he couldn't write to his CD device even though his user was in the cdrom group. He solved it by giving read/write access for the device to all users.

```
sudo chmod 666 /dev/hdc
```

---

### Post by dsimpson on 2007-12-31
Ok, have read/write permissions for group, tried to write to disc, still nothing, this is really frustrating. It almost seems that it is recognizing the disc as an incompatible type, it keeps saying the following types are supported, cdrw & cdr, but that is what I am using.

---

### Post by dsimpson on 2008-01-02
bump - see my last post! I also disconnected the cdrw and reconnected it new boot both times and nothing changed, was hoping the system would re-recognize the drive and load it but nada! I am coming back around to seek more ideas, HELP! Please...:confused:

---

### Post by dsimpson on 2008-01-15
bump. Still looking for some help on this one.

---

