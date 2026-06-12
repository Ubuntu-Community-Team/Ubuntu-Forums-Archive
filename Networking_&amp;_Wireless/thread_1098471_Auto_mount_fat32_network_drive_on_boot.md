---
title: "Auto mount fat32 network drive on boot"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by lolouk on 2009-03-17
Hi there.
First post, hope I've posted it in the right place.

I have an issue with automounting a fat32 network drive for some time now. I have seen quite a few posts on that issue, but none coud resolve my problem.

I have installed samba on my PC and below is the line from my fstab relating to the mount:

//192.168.0.2/Downloads	/media/LAN_HDD	cifs auto,username=***,password=***	0	0

For some reason that doesn't mount the drive automatically.
If I try to mount the drive manually, I get an error message:
mount error 5 = Input/output error
Refer to the mount.cifs( 8 ) manual page (e.g.man mount.cifs)

For the mount to be successful, I have to run
echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled

I can then either manually mount the drive or run
mount -a
which does work (telling me my fstab should be correct).

I have seen that having modprobe cifs in my run level could help. but that doesn't seem to work either.

So I'm kind of lost. Can anyone give me a hand with this?

---

### Post by nixscripter on 2009-03-17
You can do the zero writing trick at boot if it helps.

Create a new file as root called **/etc/modprobe.d/cifs** and put this in it:

```

# Created to fix cifs, thanks to the ubuntu forums
install cifs /sbin/modprobe cifs && echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
remove cifs /sbin/modprobe -r cifs

```

This should cause what you suggested to occur at boot.

Hope this helps.

---

### Post by lolouk on 2009-03-18
Hi nixscripter,

Thanks for your quickreply.
It did't seem to work. I was wondering, do I have to install that in runlevel once the file is created?

On a different note, I tried to mount -a after boot and my pc froze while running that command.

Did I miss something?

Thanks

---

### Post by nixscripter on 2009-03-18
The script should run at boot when all of the modules (for things like device drivers) are loading. It basically tells the modprobe commnand to do what you're trying to do whenever the module is loaded.

Try running: ```
modprobe -v cifs
``` with the script still there, and see if it prints any messages.

---

### Post by lolouk on 2009-03-19
Hi nixscripter

No luck still.

Since echo 0 > /proc/fs/cifs/LinuxExtensionsEnableddoes resolve the issue, is there a way I could automatically run that command?


Of course this command only works once a mount has been attempted, so I'd have to basically get the below to run automatically at boot, if possible:
mount network drive
echo 
mount network drive

---

### Post by lolouk on 2009-03-19
Hi nixscripter,

I got tired of trying work arounds so today I decided to take the bull by the horns, I went to /etc/init.d to see what was there.
I had a look at mountall.sh and edited it in that way:
After
```
mount_all_local() {
	    mount -a -t nonfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs,gfs2 \
		-O no_netdev
```
I inserted this:
```
echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
mount -t cifs //192.168.0.2/Downloads /media/LAN_HDD -ocredentials=/home/laurent/Documents/mycreds.creds
```

I've also added an umount command in the stop area as when I shutdown/reboot my pc with my LAN drive still connected, it takes longer and throws warnings. I haven't checked it but just in case, this is what I've done:
From:
```
case "$1" in
  start|"")
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountall.sh [start|stop]" >&2
	exit 3
	;;
esac
```
to:
```
case "$1" in
  start|"")
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	umount /media/LAN_HDD
	;;
  *)
	echo "Usage: mountall.sh [start|stop]" >&2
	exit 3
	;;
esac
```

Anyway for the first time since I'n on this issue (~1 month now) I got my LAN drive to auto mount , so I though I'd share my resolution in case it helps anyone else ;)

---

### Post by Dominique Gallot on 2010-03-30
> **nixscripter said:**
> You can do the zero writing trick at boot if it helps.

Create a new file as root called **/etc/modprobe.d/cifs** and put this in it:

```

# Created to fix cifs, thanks to the ubuntu forums
install cifs /sbin/modprobe cifs && echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
remove cifs /sbin/modprobe -r cifs

```This should cause what you suggested to occur at boot.

Hope this helps.

This solution need some changes with 9.10 <Karmic Koala >

Create a new file as root called **/etc/modprobe.d/cifs[COLOR=Red].conf[/COLOR]** and put  this in it:
```

# Created to fix cifs, thanks to the ubuntu forums
install cifs /sbin/modprobe[COLOR=Red] --ignore-install [/COLOR]cifs && echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
remove cifs /sbin/modprobe -r cifs

```Not adding the --ignore-install will make the script calling it self

To test
```

rmmod cifs
modprobe cifs
cat /proc/fs/cifs/LinuxExtensionsEnabled

```

---

