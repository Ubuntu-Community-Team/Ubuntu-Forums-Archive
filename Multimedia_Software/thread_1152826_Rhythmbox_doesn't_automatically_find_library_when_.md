---
title: "Rhythmbox doesn't automatically find library when starting after reboot"
date: 2009-05-08
forum: Multimedia Software
---

### Post by halfmind on 2009-05-08
Every time I reboot (I use a laptop) and start Rhythmbox, my music list is empty. I have to Edit > Preferences > Music > Watch my library for new files. As soon as I click 'Watch..." the list populates.  
   Any help would be appreciated (I'm very new at this Linux thing), but I would be especially grateful if it involved using the command line instead of the GUI. Thanks.

---

### Post by xc3RnbFO8P on 2009-05-08
Do you have your music on a external hard drive?

---

### Post by jaithehulk on 2009-05-08
I think ur hard drive or partition is not mounted at boot time...pls tell us on which partition or external harddrive ur songs reside?
on the terminal run
> sudo fdisk -l

post its output here..

---

### Post by halfmind on 2009-05-08
The music is on an internal drive.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1926    15470563+  83  Linux
/dev/sda2            1927        9464    60548985   83  Linux
/dev/sda3            9465        9729     2128612+  82  Linux swap / Solaris
```

Edit: So, /sda2 is my /home, and my Music is there.  See next post...

Thanks.

---

### Post by halfmind on 2009-05-08
Furthermore:  I read the man page for "fdisk" (-l is about the only option in my league), and "mount".  I ran "mount -l". Here is the output:

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime) []
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
```

When I searched this forum before submitting my question, I saw several mentions of "mount"ing issues, so I wasn't surprised when it came up, again, but I don't know how to read the results of "mount -l".
The ```
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
``` part looks interesting, because my Music directory is in /home/matt. I have no idea what "gvfs-fuse-daemon" is, but it's the only thing that actually mentions the directory that contains Music, where my tunes are stored.  
If thinking out loud is rude, please inform me.  Otherwise, I hope that some of this stuff will help.

Thanks, again.

---

### Post by halfmind on 2009-05-08
And furthermore: This is not an issue if I close and then reopen Rhythmbox during the same session.  If I have not shut-down, Rhythmbox populates the list without prompting...

Edit: So, maybe it's not saving my settings...?

---

### Post by xc3RnbFO8P on 2009-05-08
Check:
> gconf-editor
App> Rhythmbox> Libary Location

---

### Post by halfmind on 2009-05-08
Wow.  Some interesting error messages, there.  I have to step away for about ten hours, but I will check out your tip, and get back.  Thank you, very much.  It looks very interesting.

---

### Post by halfmind on 2009-05-09
Whoops. I got a bit excited, there...  This is the output from gconf-editor, library_locations:
```
[file:///home/matt/Music]
```

Thanks.

---

### Post by halfmind on 2009-05-12
O.K.  So, I right-clicked the library_locations mentioned earlier, and clicked, "Set As Default".  I got the following message:

"No database available to save your configuration: Unable to store a value at key '/apps/rhythmbox/library_locations', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf"

I'm totally lost, here.  Database? As in, "music library"?  Or is it something else? Is it something that the system should have created, or is it something that I can install?

Where can I find the "user.* syslog" file?

---

