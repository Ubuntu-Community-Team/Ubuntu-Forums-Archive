---
title: "fstab samba mount not working"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by StretchyBill on 2010-10-04
Ubuntu 10.04.1 LTS 32 bit. My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f2403430-799d-429a-9a76-23054367d08b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=fd75d544-06bb-4b92-81a1-23dd8731827d /home           ext4    defaults        0       2
/dev/sda6       /srv            ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=b42b11bf-9636-4095-8c00-6a3f46c6e81a /var            ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=bebd068b-6316-4362-a73f-526097f393b2 none            swap    sw              0       0
#
//sqlnas.dev/cvsbackup /backups smbfs username=XXXX,password=YYYY 0 0

```On boot, the last mount (//sqlnas.dev/cvsbackup /backups smbfs) does not work. Here is /var/log/boot.log:
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 135214/1831424 files, 721048/7323904 blocks
mount error: could not resolve address for sqlnas.dev: Name or service not known
No ip address specified and hostname not found
mountall: mount /backups [690] terminated with status 1
/dev/sda5: recovering journal
/dev/sda5: clean, 324/3055616 files, 278278/12206848 blocks
/dev/sda7: recovering journal
/dev/sda6: recovering journal
init: ureadahead-other main process (736) terminated with status 4
mount error: could not resolve address for sqlnas.dev: Name or service not known
No ip address specified and hostname not found
mountall: mount /backups [738] terminated with status 1
/dev/sda6: clean, 326141/19841024 files, 19464232/79345408 blocks
init: ureadahead-other main process (752) terminated with status 4
mount error: could not resolve address for sqlnas.dev: Name or service not known
No ip address specified and hostname not found
mountall: mount /backups [753] terminated with status 1
/dev/sda7: clean, 40657/19767296 files, 44331974/79056128 blocks
init: ureadahead-other main process (771) terminated with status 4
mount error: could not resolve address for sqlnas.dev: Name or service not known
No ip address specified and hostname not found
mountall: mount /backups [785] terminated with status 1
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Setting sensors limits                                                [ OK ] 
Starting Fisheye: 

```I have a similar machine, also running Ubuntu 10.04.1 LTS 32 bit, with the exact same line in the fstab file, where the mount works. Oddly, the mount appears to fail in the boot.log (at least the way I read it). Here is /var/log/boot.log for the machine where the mount works on boot:
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 461576/2445984 files, 4068793/9764864 blocks
mount error: could not resolve address for sqlnas.dev: Name or service not known
No ip address specified and hostname not found
mountall: mount /backups [551] terminated with status 1
/dev/sda7: clean, 10694/2654208 files, 1128269/10609408 blocks
init: ureadahead-other main process (630) terminated with status 4
/dev/sda6: clean, 342897/3662848 files, 4451916/14648064 blocks
mount error: could not resolve address for sqlnas.dev: Name or service not known
No ip address specified and hostname not found
init: ureadahead-other main process (648) terminated with status 4
mountall: mount /backups [631] terminated with status 1
mount error: could not resolve address for sqlnas.dev: Name or service not known
No ip address specified and hostname not found
mountall: mount /backups [657] terminated with status 1
 * Starting AppArmor profiles                                                                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                         [ OK ]
 * Setting sensors limits                                                                                                [ OK ] 
 * Starting MTA
```On the machine where the mount does not work, I do ```
sudo mount -a
``` without the /backups mount working. At some point,  /backups is successfully mounted. :confused:

The two machines attempting the mount, and the machine beging mounted (sqlnas.dev) machine are all on the same internal network.

Questions:

[LIST=1]
[*]Why is the mount failing?
[*]If the answer to #1 is not obvious, how can I diagnose what is going on so I can get a better idea of what is going on?
[/LIST]
Thanks in advance for any help.

-Bill

---

### Post by Morbius1 on 2010-10-04
Consider the following more random thoughts and observations than an answer:
> mount error: could not resolve address for sqlnas.dev: Name or service not known No ip address specified and hostname not found Your naming service cannot convert sqlnas.dev to an ip address. I'd check your router first to see if it has the ability to do that or at least check your firewalls ( on both the server and the client ) to see if it's getting in the way.

Second, try to circumvent the naming problem by specifying the ip address in fstab:
Change this:
> //sqlnas.dev/cvsbackup /backups smbfs username=XXXX,password=YYYY 0 0To this:
> //**[COLOR=Blue]192.168.0.101[/COLOR]**/cvsbackup /backups **[COLOR=Blue]cifs[/COLOR]** username=XXXX,password=YYYY 0 0[COLOR=Blue]*Where 192.168.0.101 is the ip addres of the server.*[/COLOR]

You'll note that I also changed the filesystem from "smbfs" to "cifs". cifs has replaced smbfs so it's best to use the current version.

Third, and this is going to look like a contradiction, but make sure the following package is installed:
```
smbfs
```smbfs the filesystem has been deprecated but smbfs the package is actually a metapackage that contains the utilities that that make mounting a cifs filesystem possible. 

Forth, I noticed that you have AppArmor. I'm not going to tell you what I really think of AppArmor for fear of being banned from the forum but you might want to make sure it's not interfering with something.

---

### Post by StretchyBill on 2010-10-04
Thanks for the info, Morbius1. A few things I forgot to mention:

[LIST=1]
[*]I already tried to substitute the IP address for the DNS name. The results are the same. Oddly, the other machine (the one that works) shows the same error message (No ip address specified and hostname not found) but still succeeds with the mount. Furthermore, a later invocation of ```
sudo mount -a
``` will successfully mount the share. Either some earlier ones fail or the first one takes a long time (a minute or more) to succeed.
[*]This is on a production server, so just about the only time I can reboot is first thing in the morning.
[*]The smbfs package is installed.
[/LIST]
In preparation for tomorrow morning, I changed the smbfs phrase in fstab to cifs. If it doesn't work, I will also try to ```
sudo mount -a
```and then be patient, to see if one invocation works. I will write back with the results of timorrow morning's reboot.

Also, do you have any links to information about cautions and dangers of using AppArmor? Much of the machine with the problems was setup with default Ubuntu 10.04 and I would like to be a bit more informed (benefits vs. potential problems) before I pull the plug on AppArmor.

Thanks again.

-Bill

---

### Post by Morbius1 on 2010-10-04
There is a bug which doesn't really seem applicable to your situation in that fstab is executed before the network is up. If it's a production server it's likely never turned off. 

In a home network setting I have recommended a not very elegant solution:

Create a script with the "mount -a" command in it and place it in if-up.d:
```
 gksu gedit /etc/network/if-up.d/fstabmount
```Add the following lines:
```
#!/bin/sh
mount -a 
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstabmount
```Anything placed in if-up.d will be executed only after the network is up.

---

### Post by StretchyBill on 2010-10-05
I rebooted this morning and same result. This time I tried ```
mount -a
``` but it never took. I run ```
mount -a -v
``` and this is the last message I get: ```
mount: //sqlnas.dev/cvsbackup already mounted on /backups
```, however, the mount never takes and there is nothing in the directory /backups. Weird!?!

I think I like your latest idea. I was thinking that maybe the network had not yet started when fstab was run. I didn't know about the /etc/network/if-up.d/ directory. Cool! My other thought was even uglier: call mount -a regularly in cron.

I understand what you are saying about it not being applicable to my situation. While this machine may be rebooted once every 18 to 24 months, I want that mount to be bulletproof since in 2 years whoever is doing admin on the server (including me ) may not realize the mount has not been done and the backups are not being done.

Thanks again for your help.

---

### Post by StretchyBill on 2010-10-11
I have rebooted a few times for testing and the fstabmount stuff works like a charm.

Thanks again!

-Bill

---

### Post by rkillcrazy on 2011-01-12
Is there a fix for this yet?  I'd rather not do a work-around if I can avoid it.

My issue is basically the same.  The line in FSTAB looks good and works once the server is up.  However, it doesn't work on startup which points to a timing issue.  We have some work-arounds that we've been using but, again, I'd rather not have to make this a permanent part of my new-server setup process.

2010-01-12
1534 EST

---

### Post by rkillcrazy on 2011-01-18
Here's a work-around we're using in our shop.  Ideally, there needs to be some *redesigning* done to how **FSTAB** entries are handled.  It would be nice to have the ability to add a **delay** (A **retry** wouldn't be bad either.) to anything in FSTAB - especially entries that deal with SMB/CIFS shares.

**_Basic description:_**
Basically, the following script has a loop that tries to mount my share on FS1.  If it fails, it waits for 5 seconds and then retries - up to 10 times.  The script is added to the startup process so it can be started or stopped as needed.



**_Script:_**
```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          mount-shares
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:       0 1 6
# Short-Description: Mount & Unmount network shares
### END INIT INFO

# Dump this into the /etc/init.d directory
# Make root and the root group owners of this file.
# Make the file executable for all.
# Run the following command to add it to the startup process: 
# update-rc.d mountshares.sh defaults

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin

do_start()
{
        for i in $(seq 0 1 10)
        do
                [COLOR="Red"]mount -t cifs //fs1/mysql-bu /mnt/fs1 -o credentials=/home/homenet/.smbcredentials[/COLOR]
                if [ $? -ne 0 ];
                then
                        sleep 5
                else
                        break
                fi
        done

        return 0
}

do_stop()
{
        umount /mnt/fs1
        return 0
}

case "$1" in
  start)
        do_start
        ;;
  stop)
        do_stop
        ;;
  *)
        echo "Usage: mount-shares.sh {start|stop}" >&2
        exit 3
        ;;
esac

```

**_Work-around:_**
[LIST]
[*]Tweak the script as needed.  The code in [COLOR="Red"]red[/COLOR] is where you'll do your tweaking.
[*]If you're using your own **.smbcredentials** file, be sure to follow the recommended way of using it.  (Search the forums or Google for it.)  If not, follow the process of replacing that bit of code with your username and password.
[*]Place it in **/etc/init.d**.
[*]Make root the owner and give the root group ownership as well.  (I did this because the other scripts in the init.d directory were showing the same.)
```
sudo chown root mount-shares.sh
```
```
sudo chgroup root mount-shares.sh
```
[*]Make the script executable. (I did this for ALL because the other scripts in the init.d directory were showing the same.)
```
sudo chmod a+x mount-shares.sh
```
[/LIST]

Once all that is done, you need to add it to startup.  The stuff at the top of the script, that looks like it's been commented out, is actually used to place the script in the proper spot of the startup.

Add the script to the startup process: ```
sudo update-rc.d mount-shares.sh defaults
```

**_Possible issues:_**
The only issue I see here is that, if the loop retries and fails 10 times, it'll still return a zero code.  Perhaps we can tweak the script to better trap errors in the loop (See lines 19-27.)  Frankly, I've not had it fail.

---

