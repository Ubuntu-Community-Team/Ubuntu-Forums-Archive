---
title: "4 gig ipod nano doesn't 'just work' in my Edgy"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by ions on 2007-01-07
When I first got the ipod I followed an [OLD HOWTO that had NOT been updated since April 19th 06](http://ubuntuforums.org/showthread.php?t=103071&highlight=ipod+install).  I didn't notice how out of date these instructions were until after I had followed them.  Perhaps following those [outdated instructions](http://ubuntuforums.org/showthread.php?t=103071&highlight=ipod+install) caused something to be installed which is boning me now?  Anyway, those instructions got it so I could get it to work by adding the line  '/dev/sdb2 /mnt/ipod vfat user,noauto,umask=000 0 0' in my fstab and gtkpod will see it.  Only gtkpod.  Neither Rhythmbox or Banshee see it.  Problem is I hear about these Edgy users that just plug in a Nano and away they go, automount and the good stuff.  Not me.  Plug it in and I get no visual response.  I asked around IRC and looked on the forums and there are quite a few Edgy users who it just works for.  

This may or may not be related but my Edgy install was via the Update-manager.  Those I talked to on IRC that had it automatically mount had fresh install Edgys.  I have tried 2 machines with the same results.  Both machines were updated with Update-manager.  I have reinstalled hal and gnome-volume-manager.  That should make no difference.  But of course it might. :\
 
What the computer is telling me:

Dmesg does list it.  Here is the last 20 lines of dmesg following a disconnect & reconnect of the nano:

```
$ dmesg | tail -20
[17181247.008000] usb 2-2: USB disconnect, address 5
[17181281.016000] usb 2-2: new high speed USB device using ehci_hcd and address 6
[17181281.148000] usb 2-2: configuration #1 chosen from 2 choices
[17181281.148000] scsi6 : SCSI emulation for USB Mass Storage devices
[17181281.148000] usb-storage: device found at 6
[17181281.148000] usb-storage: waiting for device to settle before scanning
[17181286.148000] usb-storage: device scan complete
[17181286.148000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17181286.148000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181286.152000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[17181286.152000] sdb: Write Protect is off
[17181286.152000] sdb: Mode Sense: 68 00 00 08
[17181286.152000] sdb: assuming drive cache: write through
[17181286.156000] SCSI device sdb: 1982464 2048-byte hdwr sectors (4060 MB)
[17181286.160000] sdb: Write Protect is off
[17181286.160000] sdb: Mode Sense: 68 00 00 08
[17181286.160000] sdb: assuming drive cache: write through
[17181286.160000]  sdb: sdb1 sdb2
[17181286.164000] sd 6:0:0:0: Attached scsi removable disk sdb
[17181286.164000] sd 6:0:0:0: Attached scsi generic sg1 type 0

```

lsusb lists:

```
$ lsusb
Bus 002 Device 006: ID 05ac:1260 Apple Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05ac:020b Apple Computer, Inc. 
Bus 001 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 002: ID 05ac:1003 Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

I also have an Apple keyboard.

```
$ ps aux | grep hald
108       4509  0.1  0.5   7240  5704 ?        Ss   16:26   0:03 /usr/sbin/hald
root      4510  0.0  0.1   2916  1060 ?        S    16:26   0:00 hald-runner
108       4516  0.0  0.0   2028   812 ?        S    16:26   0:00 /usr/lib/hal/hald-addon-acpi
108       4529  0.0  0.0   2028   804 ?        S    16:26   0:00 /usr/lib/hal/hald-addon-keyboard
108       4532  0.0  0.0   2024   812 ?        S    16:26   0:00 /usr/lib/hal/hald-addon-keyboard
108       4537  0.0  0.0   2024   804 ?        S    16:26   0:00 /usr/lib/hal/hald-addon-keyboard
108       4547  0.0  0.0   2028   836 ?        S    16:26   0:00 /usr/lib/hal/hald-addon-storage
108       7919  0.0  0.0   2032   840 ?        S    16:54   0:00 /usr/lib/hal/hald-addon-storage

```

```
$ ps aux | grep gnome-volume-manager
chris     6655  0.0  0.5  18448  5468 ?        Ss   16:27   0:00 gnome-volume-manager --sm-client-id default4
chris     8317  0.0  0.0   2796   748 pts/1    R+   17:09   0:00 grep gnome-volume-manager

```

I tried applying the patch in [this thread](http://ubuntuforums.org/showthread.php?p=1981407#post1981407) which led [here](https://launchpad.net/ubuntu/+source/hal/+bug/66068/comments/13) which  failed on step 6 with:

```
$ patch -p0 < via-raid-fix.debdiff
patching file hal-0.5.7.1/debian/changelog
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file hal-0.5.7.1/debian/changelog.rej
patching file hal-0.5.7.1/debian/patches/23-fix-via-raid-detection.patch
```

I am running Edgy, 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux.  It's up to date.  Why won't it work like it does for everybody else in Edgy?  :(

---

### Post by ions on 2007-01-07
Just tried plugging the Nano into my Edgy installed laptop.  It's had no ipod type apps installed on it previously.  It's listed in dmesg and lsusb but it's not automounted.

The three machines I have access too are all Update-manager Edgy machines updated from Dapper.  Really beginning to look like a fault in the dist-upgrade process.  Signs point in that direction anyway.

---

### Post by ions on 2007-01-07
Working now between the helpful poster [here](http://ubuntuforums.org/showthread.php?p=1982788#post1982788) and a very helpful IRCer.  

Still have to wonder why it doesn't just plug and play for some but does for others.

---

### Post by viciouslime on 2007-01-10
Do you have a 1g nano, or a 2g? The 2g nanos are the new ones that have an entirely aluminium case, the 1g have a white/black front with a mirrored rear.

If you have a 2g nano try this: [http://www.viciouslime.co.uk/index.php?option=com_content&task=view&id=14&Itemid=33]("http://www.viciouslime.co.uk/index.php?option=com_content&task=view&id=14&Itemid=33")

---

### Post by RaZoR-x11 on 2007-01-10
Hey there,

What application are you using for it, and is it in the /media/ipod dir? have you tried to mount the 
ipod manualy?

---

