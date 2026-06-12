---
title: "AUFS root partition breaks networking"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by lastexyle on 2009-07-22
Hello,

I'm setting up a computer to use AUFS as the root partition with a read-only base installation, and a rewritable partition that is cleared each boot. I have this working, but for some reason when in this mode I can't connect to the network. The network manager gets to two green orbs and then fails.

Here is my script (placed in init-bottom):

```

#!/bin/sh

PREREQ=""
prereqs(){
  echo "$PREREQ"
}
 
case $1 in
 prereqs)
   prereqs
   exit 0
   ;;
esac

for p in `cat /proc/cmdline`; do 
    case "$p" in 
    *=*) eval $p;;
    *)   eval $p=1;;
    esac 2> /dev/null
done

test "$aufs" = "on" || exit 0


modprobe -q aufs

mkdir -p /rw /ro /union

mount --move $rootmnt /ro
mount /dev/sda2 /rw

rm -R /rw/*

mount -t aufs -o br:/rw:/ro none /union

# Change root to union fs
mkdir -p /union/.ufs /union/.ufs/ro /union/.ufs/rw
mount --move /ro /union/.ufs/ro
mount --move /rw /union/.ufs/rw
mount --move /union $rootmnt


# Generate new fstab

fstab=$rootmnt/etc/fstab

cat <<EOF > $fstab
none / tmpfs defaults 0 0
$root /.ufs/ro ext3 ro,noatime,nodiratime 0 0
EOF

cat $rootmnt/ro/etc/fstab | grep -v $root | grep -v tmpfs >> $fstab

cat <<EOF >> $fstab
/dev      /.ufs/ro/dev      none bind 0 0
/dev/pts  /.ufs/ro/dev/pts  none bind 0 0
/sys      /.ufs/ro/sys      none bind 0 0
/proc     /.ufs/ro/proc     none bind 0 0
#/mnt/sda1 /.ufs/ro/mnt/sda1 none bind 0 0
EOF

exit 0;

```

I'm guessing that the system is brining up the network interfaces before this script runs and that's messing things up, but I have no idea how to fix it.

---

### Post by EarlM on 2009-11-19
See this other thread for the same issue (no fix yet)
[http://ubuntuforums.org/showthread.php?t=1315160](http://ubuntuforums.org/showthread.php?t=1315160)

This affects me on Jaunty and Karmic - works fine if I boot with normal rw root, but not with AUFS root. So far I haven't managed to work through the init scripts to see where it's going wrong. In my karmic syslog I can see that /sbin/dhclient3 is denied_mask="r::" for /ro/etc/ld.so.cache and /ro/lib/libc-2.10.1.so - Is this AppArmour interfereing? But why is dhcpclient bothering with files on /ro?

---

### Post by nschembr on 2009-11-20
I'm sorry I missed the post about this issue. I will retest the [https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash) this weekend.

This post talks about NetworkManager and AppArmor not liking the /ro filesystem,
[http://www.languid.org/blog/index.php/2009-10/an-ubuntu-appliance/](http://www.languid.org/blog/index.php/2009-10/an-ubuntu-appliance/)

This may just be an issue with the way aufs works.

I will post the changes on the wiki.

Nicholas A. Schembri
Pittsburgh PA USA.

---

### Post by philipp2084 on 2009-11-25
Hi, 

I ran into exactly the same problem. Any news on this yet?

To temporarily get the dhcp client to function I disabled AppArmor and restarted networking.

```

$ sudo /etc/init.d/apparmor stop
$ sudo /etc/init.d/networking start

```

I have had a look a the release notes of Karmic ([http://www.ubuntu.com/getubuntu/releasenotes/910overview]("http://www.ubuntu.com/getubuntu/releasenotes/910overview")) and came across this: 

> AppArmor

  

AppArmor in Ubuntu 9.10 RC features an improved parser that uses cache files, greatly speeding up AppArmor initialisation on boot. AppArmor also now supports 'pux' which, when specified, means a process can transition to an existing profile if one exists or simply run unconfined if one does not.   

Please see the AppArmor documentation for information on using AppArmor in Ubuntu.


I have not had time to look into this further but am very keen to have a proper solution. 

I have modified grub2 in order to achieve the same as described for grub1 on the wiki. Let me know if you are interested and I I will write it up and post it on the wiki.

---

### Post by EarlM on 2009-12-01
As a temporary work around, I edited /boot/grub/menu.lst to disable apparmor when booting with the read-only system: I added  apparmor=0 to the kernel command line just after aufs=tmpfs.

Not ideal, as I'm sure there's a good reason why apparmor is provided, but hopefully the read-only file system makes this a little less of an issue.

---

### Post by muppis on 2012-02-06
I know this is an old threat, but I ended up here because I needed aufs as root with apparmor. Enter dhclient3 to complain mode with command
```
sudo aa-complain dhclient3
```
networking works again without disabling an apparmor.

Cheers.

---

### Post by bbkudk on 2012-03-02
> **muppis said:**
> I know this is an old threat, but I ended up here because I needed aufs as root with apparmor. Enter dhclient3 to complain mode with command
```
sudo aa-complain dhclient3
```networking works again without disabling an apparmor.

Cheers.
I added to the [wiki]("https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash#Apparmor") this info.

---

