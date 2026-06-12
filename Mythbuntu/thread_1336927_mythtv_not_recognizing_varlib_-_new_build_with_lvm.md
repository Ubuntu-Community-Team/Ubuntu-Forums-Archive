---
title: "mythtv not recognizing /var/lib/ - new build with lvm"
date: 2009-11-25
forum: Mythbuntu
---

### Post by tkleen on 2009-11-25
Hi all, 

I recently rebuilt my system to mythbuntu 9.10 with the intent of setting up my /var/lib/ folder on an lvm partition. I followed this tutorial to do so:

[http://ubuntuforums.org/showthread.php?t=584473](http://ubuntuforums.org/showthread.php?t=584473)

The only thing that I did differently is that I formatted it as ext4 instead of xfs. 

On the command line I see the files for /var/lib/ and when I run the command df -h /var/lib/ I get the following output:

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg-lib    887G   28G  815G   4% /var/lib

I'm able to see the files that I have dropped into /var/lib/mythtv/videos/ on my windows box via samba. However, when I run the video manager in mythtv frontend to populate the video list, no files are found. I also tried creating a symbolic link pointing to /var/lib/mythtv/videos/ and setting the default location for the videos folder to point to that link, and I am still unable to get mythvideo to populate.

Any ideas?

Thanks in advance.

---

### Post by superm1 on 2009-11-25
Manually created your directory structure with LVM?  I say permissions.  Go make sure everything is rw- for "mythtv:mythtv"

---

### Post by tkleen on 2009-11-25
Thank you for the reply superm1. 

All files in /var/lib/mythtv/ are set to mythtv:mythtv at write level 775. Tried changing /var/lib/mythtv to mythtv:mythtv with no effect. Have since changed /var/lib/mythtv back to root:root.

Here is the output of ls -l on /var/lib/mythtv/

> drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 banners
drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 coverart
drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 db_backups
drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 fanart
drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 livetv
drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 02:10 music
drwxrwxr-x 2 mythtv mythtv 4096 2009-11-24 23:04 other
drwxrwxr-x 2 mythtv mythtv 4096 2009-10-26 02:10 pictures
drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 recordings
drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 screenshots
drwxrwsr-x 2 mythtv mythtv 4096 2009-11-24 23:33 trailers
drwxrwxr-x 3 mythtv mythtv 4096 2009-11-24 23:18 unsorted
drwxrwsr-x 4 mythtv mythtv 4096 2009-11-24 23:33 videos

And here is the same for /var/lib/

> 
total 208
drwxr-xr-x  2 root          root          4096 2009-10-13 01:50 acpi-support
drwxr-xr-x  2 root          root          4096 2009-11-22 20:44 alsa
drwxr-xr-x  2 root          root          4096 2009-10-16 21:40 apparmor
drwxr-xr-x  6 root          root          4096 2009-11-22 21:02 apt
drwxr-xr-x  2 root          root          4096 2009-09-28 06:01 aptitude
drwxr-xr-x  2 avahi-autoipd avahi-autoipd 4096 2009-10-28 13:29 avahi-autoipd
drwxr-xr-x  2 root          root          4096 2009-11-22 19:35 belocs
drwxr-xr-x  2 root          root          4096 2009-11-22 19:41 dbus
drwxr-xr-x  9 root          root          4096 2009-10-28 13:30 defoma
drwxr-xr-x  2 root          root          4096 2009-10-23 05:11 DeviceKit-disks
drwxr-xr-x  2 root          root          4096 2009-10-15 09:26 DeviceKit-power
drwxr-xr-x  2 root          root          4096 2009-11-22 20:42 dhcp3
drwxr-xr-x  5 root          root          4096 2009-11-22 21:02 doc-base
drwxr-xr-x  7 root          root          4096 2009-11-22 21:02 dpkg
drwxr-xr-x  5 root          root          4096 2009-10-28 13:26 gconf
drwxr-x---  4 gdm           gdm           4096 2009-10-28 13:27 gdm
drwxr-xr-x  2 root          root          4096 2009-10-05 05:37 hal
drwxr-xr-x  2 root          root          4096 2009-10-28 13:28 initramfs-tools
drwxr-xr-x  2 root          root          4096 2009-10-19 08:18 initscripts
drwxr-xr-x  2 root          root          4096 2009-10-19 08:18 insserv
drwxrwsr-x  2 libuuid       libuuid       4096 2009-10-28 13:24 libuuid
drwxr-xr-x  3 root          root          4096 2009-10-28 13:27 libxml-sax-perl
drwxr-xr-x  3 root          root          4096 2009-10-28 13:24 locales
drwxr-xr-x  2 root          root          4096 2009-08-19 21:51 logrotate
drwxr-xr-x  2 root          root          4096 2009-10-28 13:26 misc
drwxr-xr-x  2 root          root          4096 2009-10-28 13:32 mlocate
drwxr-xr-x  4 mysql         mysql         4096 2009-11-24 23:33 mysql
drwxr-xr-x  3 root          root          4096 2009-10-28 13:27 mytharchive
drwxrwsr-x  3 mythtv        mythtv        4096 2009-10-28 13:28 mythdvd
drwxr-xr-x 15 root          root          4096 2009-11-24 23:03 mythtv
drwxr-xr-x  2 root          root          4096 2009-10-14 16:38 NetworkManager
drwxr-xr-x  6 statd         root          4096 2009-11-24 23:33 nfs
drwxr-xr-x  2 ntp           ntp           4096 2009-11-24 23:33 ntp
drwxr-xr-x  3 root          root          4096 2009-11-22 19:37 os-prober
drwxr-xr-x  2 root          root          4096 2009-11-22 19:39 pam
drwx-wx-wt  2 root          root          4096 2009-10-23 09:37 php5
drwxr-xr-x  2 root          root          4096 2009-10-06 14:41 pm-utils
drwx------  3 root          root          4096 2009-10-28 13:27 polkit-1
drwxr-xr-x  2 root          root          4096 2009-10-28 13:31 pycentral
lrwxrwxrwx  1 root          root            18 2009-11-24 22:46 python-support -> /usr/lib/pymodules
drwxr-xr-x  5 root          root          4096 2009-11-24 23:14 samba
drwxr-xr-x  2 root          root          4096 2009-10-28 13:30 setserial
drwxr-xr-x  2 root          root          4096 2009-10-28 13:24 sgml-base
drwxr-xr-x  2 root          root          4096 2009-10-15 10:15 synaptic
drwxr-xr-x  3 root          root          4096 2009-11-22 19:38 ucf
drwxr-xr-x  2 root          root          4096 2009-10-23 09:21 update-manager
drwxr-xr-x  3 root          root          4096 2009-11-22 20:17 update-notifier
drwxr-xr-x  2 root          root          4096 2009-11-22 19:39 update-rc.d
drwxr-xr-x  2 root          root          4096 2009-11-24 23:33 urandom
drwxr-xr-x  3 root          root          4096 2009-10-28 13:24 vim
drwxr-xr-x  2 root          root          4096 2009-10-28 13:25 x11
drwxr-xr-x  2 root          root          4096 2009-11-24 23:33 xkb
drwxr-xr-x  2 root          root          4096 2009-10-28 13:29 xml-core

I hope that helps. I'm stumped. The next thing I plan to try is unmounting the lvm partition and replacing the original /var/lib on the boot partition and test if it works that way. But that will have to wait until tomorrow. Have to work in the morning.

Thanks again to everyone for taking a look and offering help!

---

### Post by pootle1 on 2009-11-25
maybe a silly point, but if this is your first build with myth0.22, then have you taken account of the new way storage works?  

see [http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)

Caught me out when I first did it, but now I have converted, it makes life so much easier not having to do all the pratting about with exports.

All my videos are sitting on a nice little mdadm raid 10 array with LVM running on top of that.

---

### Post by nickrout on 2009-11-25
also have you scanned for videos in mythvideo (M button, scan for changes)

---

### Post by tkleen on 2009-11-26
Thank you for the replies, Nickrout and pootle1. It turns out you were both right. After looking at the article you recommended I realized that the video manager is now deprecated. When I tried populating the videos list via the menu button on the remote everything worked fine.

Never even thought that the problem could be that Video Manager doesn't do anything anymore. It's always something simple. isn't it?

Thanks again.

---

