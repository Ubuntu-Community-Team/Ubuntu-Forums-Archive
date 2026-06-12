---
title: "Ipod Touch v1 with Amarok 1.4 stopped working on upgrade to Lucid"
date: 2010-06-08
forum: Multimedia Software
---

### Post by cazabon on 2010-06-08
Hello all,

Thanks for reading - this one's got me stumped, and no one else seems to have posted about it.  My circumstances are a little unusual (v1 firmware on the Ipod touch), which probably explains that.

Summary: a long-working config involving a 1st-generation Ipod Touch with v1 firmware, Ubuntu, and Amarok 1.4 stopped working when I upgraded to Lucid.

A few years ago I was given a 1st-generation Ipod Touch, running the original v1 firmware (I never upgraded to the v2 firmware because v2 wasn't jailbroken at the time).  I took it to a friend's place to activate and jailbreak it with her Mac laptop (I didn't have a Mac or Windows machine to install Itunes on; have been Linux-only for many years).  Once jailbroken, I was happily able to use it with Hardy, Amarok 1.4, and ipod-convenience (which supply ipod-touch-mount/ipod-touch-umount).

This continued through upgrades to Intrepid and Jaunty.  I didn't care for Amarok 2 in Jaunty, so I installed Amarok 1.4 from the ppa someone else made available.  I continued to use it through Jaunty and Karmic, without any problems.

Last week I upgraded to Lucid.  Syncing Amarok 1.4 to the Ipod Touch no longer appears to work; the Ipod fails to recognize any music transferred onto it (standard "No Music - you can buy music at Itunes" error screen), so I presume this is a libgpod/hash error.  I have the FirewireGuid properly set in the .../Device/SysInfo file, as I always have.

Every time I use the Amarok Ipod "connect" function (which runs ipod-touch-mount) it tells me no valid Itunes db was found, and asks to initialize the db.  I can then transfer music to the Ipod, and successfully disconnect, but it's not recognized on the Ipod after a respring or reboot.

I've tried RhythmBox and gtkpod briefly with no luck either.

Relevant installed packages:

```

ii  amarok14                                     2:1.4.10-0ubuntu3~ppa5                       Amarok 1.4 series
ii  amarok14-common                              2:1.4.10-0ubuntu3~ppa5                       architecture independent files for Amarok
ii  amarok14-engine-xine                         2:1.4.10-0ubuntu3~ppa5                       xine engine for Amarok 1.4 series
ii  libgpod-common                               0.7.93-0ubuntu1                              common files for libgpod
ii  libgpod-doc                                  0.7.93-0ubuntu1                              documentation for libgpod
ii  libgpod4                                     0.7.93-0ubuntu1                              library to read and write songs and artwork to an iPod
ii  python-gpod                                  0.7.93-0ubuntu1                              Python bindings for libgpod
ii  ipod                                         0.5.3-3.2ubuntu2                             tool for retrieving informations from iPods
ii  ipod-convenience                             0.11-0ubuntu1                                iPod Touch & iPhone sync setup
ii  libipoddevice0                               0.5.3-3.2ubuntu2                             library for retrieving informations from iPods

```

I'd appreciate any help anyone can offer.  I'm guessing the v1 firmware on the Ipod is what makes my case more or less unique.

Edit: a little more info: after I let Amarok initialize the Ipod Touch and transfer a song to it, the iTunes.db that gets created on the Ipod is 0 bytes long.  I presume this is the source of the  problem, and indicates something is going wrong with libgpod's creation/editing of the db.

Any ideas on what I should do from here?  I've tried removing the DB by hand, but it makes no difference - the subsequent operation to initialize the db results in the same 0-byte file.

---

### Post by cazabon on 2010-06-11
Answering my own question, in case anyone else runs into this.

The problem turns out to be the SysInfoExtended file.  This was not previously used (or at least not required) with the libgpod library I'd been using, but apparently with the version shipped with Lucid, it's now mandatory, and what's worse, when it's not present it doesn't complain, but still manages to corrupt the db on the ipod.

I found various bad advice on how to generate the SysInfoExtended file as well.  A lot of seems to assume a non-touch Ipod that's syncing through USB, not through wifi.  Some of it specifies the wrong arguments.

Here's what to do.


[LIST=1]
[*]reinstall the ipod-convenience package if it isn't installed or was removed on upgrade to Lucid.  You can find it through the Ubuntu packages list at packages.ubuntu.com.
[*]configure normally through `/etc/default/ipod-convenience`, if your  configuration got blown away
[*]run: ```
ipod-touch-mount
``` to mount the Ipod Touch over wifi.  I mount mine at `/media/ipod/`
[*]run: ```
sudo lsusb -v | grep iSerial
``` and find the line containing the  serial / uuid for your Ipod Touch.  If more than one line has data, read  the full output of `lsusb -v` to find the right one
[*]run: ```
ipod-read-sysinfo-extended [uuid] [mountpoint]
```
[*]verify the file has correctly been written to `[mountpoint]/iTunes_Control/Device/SysInfoExtended`  (it contains some  XML)
[*]run: ```
ipod-touch-umount
``` to flush the changes to your Ipod
[*]now go ahead and connect with Amarok, gtkpod, or whatever, and resync.   It should work.
[/LIST]
Hope this helps someone else.

---

### Post by funfrank on 2010-06-26
Thanks for this post.  I have a similar situation that began when I reinstalled Karmic.  I had been using a very simple iTunnel-sshfs connection and gtkpod for transfers.  When I reinstalled Karmic, I thought I'd give ifuse a go and attempt to transfer files within my player of choice, rhythmbox.  This seems to have corrupted my FirewireGUID contained within my sysinfo file.  The problem now, is that I cannot edit that file -- even when logged as root:

```
frank@frank-laptop:/mnt/ipod/iTunes_Control/Device$ sudo gedit SysInfo
(gedit:1899): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory

** (gedit:1899): WARNING **: Could not get info for file:///mnt/ipod: Error stating file '/mnt/ipod': Permission denied

** (gedit:1899): WARNING **: Could not get info for file:///mnt/ipod/iTunes_Control: Error stating file '/mnt/ipod/iTunes_Control': Permission denied

** (gedit:1899): WARNING **: Could not get info for file:///mnt/ipod/iTunes_Control/Device: Error stating file '/mnt/ipod/iTunes_Control/Device': Permission denied


```

I tried rolling back changes and mounting again with iTunnel and sshfs, but I think the ifuse installation may have "corrupted" the functionality of my original setup.  The root mount was successful, but I still receive these permission denied messages.  I was thinking of restoring and re-jailbreaking the iPod Touch (1st gen, firmware 2.x), but I too, have been linux-only for several years now.  Any advice would be appreciated.

---

### Post by funfrank on 2010-06-26
Well, I was able to edit the FirewireGUID strangely through nautilus, but not through terminal.  Once I edited the FirewireGUID, gtkpod stopped giving me the hash error, but now it will not initialise the directory structure.  It seems to still be a problem with permissions.  Considering that I have sufficient permissions to edit the files in nautilus and not in terminal, I truly am stumped.

---

