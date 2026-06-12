---
title: "HOWTO: Automatically mount NFS shares without autofs"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by JeroenHoek on 2010-01-24
This howto has been moved to the  [Wiki]("https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto")

The thread is kept open in order to have a place for discussing the Wiki page.

---

### Post by X3lectric on 2010-07-28
Hi

I thank you for posting this, it would be helpfull if it worked for me but it doesnt, maybe you can help?

In addition of what I post below the /media/**whateverdirectory **exists.

My nfsmount.sh this exists and is executable in /usr/local/bin
```
#!/bin/bash

# The hostname or IP-address of the fileserver:
FILESERVER="192.168.1.7"
# Check every X seconds (60 is a good default):
INTERVAL=60
# The shares that need to be mounted:
MOUNTS=( "/media/TV_SERIES" "/media/MOVIES" "/media/MUSIC" "/media/SOURCES" )

while true; do
    ping -c 1 "$FILESERVER" &>/dev/null
    if [ $? -eq 0 ]; then
        # Fileserver is up.
        logger "Fileserver is up."
        for MOUNT in ${MOUNTS[@]}; do
            mount | grep -E "^${FILESERVER}:${MOUNT} on .*$" &>/dev/null
            if [ $? -ne 0 ]; then
                # NFS mount not mounted, attempt mount
                logger "NFS shares not mounted; attempting to mount ${MOUNT}:"
                mount -t nfs ${FILESERVER}:${MOUNT} ${MOUNT} ${MOUNT} ${MOUNT}
            fi
        done
    else
        # Fileserver is down.
        logger "Fileserver is down."
        for MOUNT in ${MOUNTS[@]}; do
            mount | grep -E "^${FILESERVER}:${MOUNT} on .*$" &>/dev/null
            if [ $? -eq 0 ]; then
                # NFS mount is still mounted; attempt umount
                logger "Cannot reach ${FILESERVER}, unmounting NFS share ${MOUNT}."
                umount -f ${MOUNT}
            fi
        done
    fi
    sleep $INTERVAL
done

```My nfsmount.conf exists and is 644 owned by root:root in /etc/init
```
# nfsmount
# mount NFS shares on fileserver, if present
# Created by JeroenHoek - http://bit.ly/c4Pwv6
# Modded by X3, Team iQuik 2010

description    "Mount NFS-shares"

start on (filesystem)
respawn

exec /usr/local/bin/nfsmount

```My nfsmount upstart created it exists in /etc/init.d
```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          nfsmount
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start nfsmount daemon at boot time
# Description:       Enable nfsmount service provided by daemon.
### END INIT INFO
# upstart-job
#
# Symlink target for initscripts that have been converted to Upstart.

set -e

INITSCRIPT="$(nfsmount "$0")"
JOB="${INITSCRIPT%.sh}"

if [ "$JOB" = "upstart-job" ]; then
    if [ -z "$1" ]; then
        echo "Usage: upstart-job JOB COMMAND" 1>&2
    exit 1
    fi

    JOB="$1"
    INITSCRIPT="$1"
    shift
else
    if [ -z "$1" ]; then
        echo "Usage: $0 COMMAND" 1>&2
    exit 1
    fi
fi

COMMAND="$1"
shift


if [ -z "$DPKG_MAINTSCRIPT_PACKAGE" ]; then
    ECHO=echo
else
    ECHO=:
fi

$ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"

case $COMMAND in
status)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    $COMMAND "$JOB"
    ;;
start|stop|restart)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    PID=$(status "$JOB" 2>/dev/null | awk '/[0-9]$/ { print $NF }')
    if [ -z "$PID" ] && [ "$COMMAND" = "stop" ]; then
        exit 0
    elif [ -n "$PID" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    elif [ -z "$PID" ] && [ "$COMMAND" = "restart" ]; then
        start "$JOB"
        exit 0
    fi
    $COMMAND "$JOB"
    ;;
reload|force-reload)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
    exit 1
esac

```this never works tried
```
root@iMedia:/usr/local/bin# nfsmount
No command 'nfsmount' found, did you mean:
 Command 'ntfsmount' from package 'ntfsprogs' (main)
nfsmount: command not found
root@iMedia:/usr/local/bin#

``````
root@iMedia:/usr/local/bin# ./nfsmount.sh
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
``````
root@iMedia:/usr/local/bin# nfsmount start
No command 'nfsmount' found, did you mean:
 Command 'ntfsmount' from package 'ntfsprogs' (main)
nfsmount: command not found

``````
root@iMedia:/usr/local/bin# /etc/init.d/nfsmount start
/etc/init.d/nfsmount: 17: nfsmount: not found
```I've ran out of ideas, what have I done wrong?
I cant see the mistake or error.

---

### Post by JeroenHoek on 2010-08-12
X3lectric:
Can you mount your NFS shares from the command-line? This should be explained in the [COLOR="Blue"]_[SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")_[/COLOR].

Also, you call the script as **nfsmount**, but the actual script appears to be named **nfsmount.sh**. Is the name correct? You should see the name of your script appear in the console if you type *nfs* and hit tab twice.

---

### Post by yp2 on 2010-09-10
Thanks!!!! It's working. Thanks!!! May I translate this how-to in polish with your credits of course?

---

### Post by JeroenHoek on 2010-09-10
yp2:
By all means. Just linking to this thread is more than sufficient really. As far as I am concerned, consider this mini-HOWTO in the public domain. I'm glad it can be of use to others. :)

I'm still using it for my home network; it works quite well.

---

### Post by yp2 on 2010-09-20
Thaks.

---

### Post by jatatar on 2010-10-29
This is a great little script.  Just needed a bit of tweaking to make it work with my system/setup.  ${Fileserver}:${Mount} language only works if the shares are located in the same place on both systems,I found it easy to modify the .sh file as follows to suit my need.

#!/bin/bash

# The hostname or IP-address of the fileserver:
FILESERVER="192.168.0.10"
# Check every X seconds (60 is a good default):
INTERVAL=360
# The shares that need to be mounted (server side)
SHAREA="/home/jatatar/storage"
SHAREB="/home/jatatar/Downloads"
SHAREC="/home/jatatar/Documents"
# Place where shares will be on local system (if different from server location)
MOUNTA=${SHAREA}
MOUNTB="/media/maverick-documents"
MOUNTC="/media/maverick-downloads"

while true; do
        ping -c 1 "$FILESERVER" &>/dev/null
        if [ $? -eq 0 ]; then
                # Fileserver is up.
                mount -t nfs ${FILESERVER}:${SHAREA} ${MOUNTA} 
                mount -t nfs ${FILESERVER}:${SHAREB} ${MOUNTB}
                mount -t nfs ${FILESERVER}:${SHAREC} ${MOUNTC}
        else
                # Fileserver is down.
                logger "Fileserver is down."
                umount ${MOUNTA}
                umount ${MOUNTB}
                umount ${MOUNTC}
        fi
        sleep $INTERVAL
done


###
I also eliminated the extra checking to see if the folders were already mounted...due to the interval re-running the script, if the server was unavailable, folders are unmounted. Seemed logically simpler this way.:)

Also could add more fileservers in a second do loop to expand, could check mulitple folders for you.   This is a good alternative to sudo mount -a as you can already see either in Places, or desktop if your server is available.


Only question is how much resource does this script use?

---

### Post by jatatar on 2010-11-01
Been experimenting with this script because I wanted to accomplish two things... 
1) Automount another share located on a seperate fileserver using the same script.

2) Only attempt mounts when internet connection is available

For #1, I changed my nfsmounts file as follows:
#!/bin/bash

# The hostname or IP-address of the fileserver:
FILESERVERA="192.168.0.12"
FILESERVERB="192.168.2.4"

# Check every X seconds (60 is a good default):
INTERVAL=60

# FILESERVERA -- The shares that need to be mounted (server side)
SHAREA="/home/jatatar/Music"
SHAREB="/home/jatatar/Downloads"
SHAREC="/home/jatatar/Documents"
SHARED="/home/jatatar/Videos"

# FILESERVERB -- The shares that need to be mounted (server side)
SHAREE="/mnt/HD_A2"

#  - Place where shares will be on local system (if different from server location)
MOUNTA="/media/mvaerick-music"
MOUNTB="/media/maverick-documents"
MOUNTC="/media/maverick-downloads"
MOUNTD="/media/maverick-video"
MOUNTE="/home/jatatar/dlink"

while true; do
	ping -c 1 "$FILESERVERA" &>/dev/null
	if [ $? -eq 0 ]; then
		# FileserverA is up.
		mount -t nfs ${FILESERVERA}:${SHAREA} ${MOUNTA} 
		mount -t nfs ${FILESERVERA}:${SHAREB} ${MOUNTB}
		mount -t nfs ${FILESERVERA}:${SHAREC} ${MOUNTC}
		mount -t nfs ${FILESERVERA}:${SHARED} ${MOUNTD}
	else
		# FileserverA is down.
		logger "FileserverA is down."
		umount ${MOUNTA}
		umount ${MOUNTB}
		umount ${MOUNTC}
		umount ${MOUNTD}
	fi

	ping -c 1 "$FILESERVERB" &>/dev/null
        if [ $? -eq 0 ]; then
                # FileserverB is up.
                mount -t nfs ${FILESERVERB}:${SHAREE} ${MOUNTE} 
	else
                # FileserverB is down.
                logger "FileserverB is down."
                umount ${MOUNTE}
	fi 

	sleep $INTERVAL
done

Changed verbage to add 2 fileservers and then added ping check and mounting of shares in a second if else statement.  This could be expanded infinitely as needed.  My server has two separate NICS and thus has two separate ips. 

For #2, linked nfsmounts-serv to the network/if-up.d directory 

using command:

sudo ln -s /usr/local/bin/nfsmounts-serv /etc/network/if-up.d

files in /etc/network/if-up.d directory are executed when nm-applet has a valid network connection this way on bootup program starts on network connection and loops every 60 seconds.

You could easily save or move your script to that directory, but I prefer the symlink.

---

### Post by buntunub on 2010-12-10
I noticed some autofs issues when I did that 200 line kernel hack a while back to optimize my Lucid desktop. This script came to the rescue, but it will not work with a typical nfsv4 setup. Followon posters pointed me in the right direction -

Typicsl /etc/fstab =


```
#nfs drive
192.168.11.5:/export/ /media/exportA  nfs4  proto=tcp,port=2049,rsize=8192,wsize=8192,timeo=60,retrans=6,rw,noatime,intr  0  0
```

This sets up a typical nfs setup with the server export(s). Because of this, the script would not work as written and required heavy modification. Here is the correct way -

```
#!/bin/bash

# The hostname or IP-address of the fileserver:
FILESERVER="192.168.11.5"
# Check every X seconds (60 is a good default):
INTERVAL=360
# The shares that need to be mounted:
SHAREA="/exportA/"
SHAREB="/exportB/"
SHAREC="/exportC/"
MOUNTA="/media/exportA"
MOUNTB="/media/exportB"
MOUNTC="/media/exportC"

while true; do
	ping -c 1 "$FILESERVER" &>/dev/null
	if [ $? -eq 0 ]; then
		# Fileserver is up.
		logger "Fileserver is up."
		mount ${FILESERVER}:${SHAREA} ${MOUNTA}
		mount ${FILESERVER}:${SHAREB} ${MOUNTB}
		mount ${FILESERVER}:${SHAREC} ${MOUNTC}
		else
		# Fileserver is down.
		logger "Fileserver is down."
		umount ${MOUNTA}
		umount ${MOUNTB}
		umount ${MOUNTC}
	fi
	sleep $INTERVAL
done
```


Thats an example of 3 shares mounted via /etc/fstab entries. You still have to setup your NFS shares the right way, autofs or no.

---

### Post by MountainX on 2011-01-09
I'm looking for a solution that will allow me to suspend to RAM. I have all my data on a mounted NFS share. [This prevents my computer from being able to suspend]("http://ubuntuforums.org/showthread.php?t=1641253").

Could this script be a solution for me? 

I suppose another script to auto-unmount upon suspending will be needed too. Maybe something like the script [here]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/506116/comments/1") would be a starting point.

Anyone want to help me with this?

---

### Post by airtonix on 2011-03-24
> **MountainX said:**
> 
Could this script be a solution for me? 
...
Anyone want to help me with this?

It might it might not be, but i have been having the same problem as you since moving to maverick from lucid.

I just tried commenting out the nfs mount from /etc/mtab , then issued a forced unmount : 

```

#!/bin/sh
SERVER_NAME=edge.home
SHARE_NAME=/share
sed s/"$SERVER_NAME:"/"#$SERVER_NAME:"/g -i /etc/mtab
umount $SHARE_NAME -f

```
source : [http://wikiri.upc.es/index.php/NFS_force_umount](http://wikiri.upc.es/index.php/NFS_force_umount)

After running code to that effect, i was able to click suspend from the gnome-panel session applet and actually have the computer suspend.

I suspect that according to the NFS docs we might need to have "hard,intr" in the options of the fstab.

**hard**
meaning the client will continue to attempt access to the server if the server is not there. and will refuse all requests to die.

**intr**
meaning that it will still attempt the behavior of hard, bu will instead honor any requests to die.


it's late and i'm about to fall over asleep, but i thought i'd document this here for you to find. maybe it's useful.

---

### Post by MountainX on 2011-03-26
thanks [airtonix]("http://ubuntuforums.org/member.php?u=44445"). That's interesting. I have been using hard,intr and I played with soft,intr and every option I could think of.

But I do like the idea of using a script to work around this problem. Here are some initial thoughts about it:

```
#!/bin/bash
#
# gnome-power-control
# Author: AgenT
# see http://ubuntuforums.org/showthread.php?p=8947629

#SETUP
#1) Save the above as: gnome-power-control
#2) Change file permissions to execute (right click on file -> properties -> permissions)
# or sudo chmod a+x /usr/bin/gnome-power-control
#3) optional: move this script into your ~/bin/ folder for easy access!
# or place it anywhere on the path. Check with $ echo $PATH
#USAGE
#To suspend: gnome-power-control suspend
#To hibernate: gnome-power-control hibernate

SERVER_NAME=edge.home

# write all unwritten data (just in case)
sync

# comment out NFS mounts (mine are all on one server, fortunately)
sed s/"$SERVER_NAME:"/"#$SERVER_NAME:"/g -i /etc/mtab

#need to do this for all NFS mounts! How?
umount -a -t NFS -f

case $1 in
suspend)
echo Suspending
    dbus-send --print-reply \
        --system \
        --dest=org.freedesktop.DeviceKit.Power \
        /org/freedesktop/DeviceKit/Power \
        org.freedesktop.DeviceKit.Power.Suspend
;;
hibernate)
echo Hibernating
    dbus-send --print-reply \
        --system \
        --dest=org.freedesktop.DeviceKit.Power \
        /org/freedesktop/DeviceKit/Power \
        org.freedesktop.DeviceKit.Power.Hibernate
;;
*)
echo Not supported command: '"'$1'"'
echo Usage: $0 '<suspend|hibernate>'
exit 1
;;
esac

# restore mount descriptors
sed s/"#$SERVER_NAME:"/"$SERVER_NAME:"/g -i /etc/mtab

# mount
sudo mount -a


```sources:
[http://www.linux.com/archive/feature/114220](http://www.linux.com/archive/feature/114220)
[http://ubuntuforums.org/showthread.php?p=8947629](http://ubuntuforums.org/showthread.php?p=8947629)

---

### Post by MountainX on 2011-03-26
There are a bunch of good suggestions here:
[http://ubuntuforums.org/showthread.php?p=8947629](http://ubuntuforums.org/showthread.php?p=8947629)

Combining those suspend scripts with airtonix's suggestions gave me a solution that appears to work. (I have only tested it once so far.)

```
#!/bin/bash
#
# gnome-power-control
# Original Author: AgenT
# see http://ubuntuforums.org/showthread.php?p=8947629

#SETUP
#1) Save the above as: suspend-unmount.sh
#2) Change file permissions to execute (right click on file -> properties -> permissions)
# or sudo chmod a+x /usr/bin/suspend-unmount.sh
#3) optional: move this script into your ~/bin/ folder for easy access!
# or place it anywhere on the path. Check with $ echo $PATH
#USAGE
#To suspend: suspend-unmount.sh

SERVER_NAME=192.168

# write all unwritten data (just in case)
sync

# comment out NFS mounts (mine are all on one server, fortunately)
sed s/"$SERVER_NAME"/"#$SERVER_NAME"/g -i /etc/mtab

#need to do this for all NFS mounts! This is experimental:
umount -a -t NFS -f

sudo pm-suspend

# restore mount descriptors
sed s/"#$SERVER_NAME"/"$SERVER_NAME"/g -i /etc/mtab

# mount
sudo mount -a
```When I ran it, it suspended beautifully and really quickly. Waking up was trouble-free too. But upon waking up, I saw this output:

```
~/bin$ sudo ./suspend-unmount.sh 
mount.nfs: /volume/one is busy or already mounted
mount.nfs: /volume/two is busy or already mounted
mount.nfs: /volume/three is busy or already mounted
mount.nfs: /volume/four is busy or already mounted
mount.nfs: /volume/five is busy or already mounted
```Not a big deal for me. Those are just messages, not errors. But I might experiment with variations on the mounting.

EDIT: even though everything is working, the NSF mounts on SERVER_NAME are missing from /etc/mtab after resuming. But I can access the NFS shares just fine. Not exactly sure what's going on...

---

### Post by MountainX on 2011-03-26
I tested a few more times with some modifications. This code works for me:

```
#!/bin/bash
sync
umount -a -t NFS -f
sudo pm-suspend
sudo mount -a -t NFS
```Changing the umount command to this:
```
umount -a -t NFS -l
```causes suspending to fail. So the force unmount is required in my case. I wonder if it is really safe, even with the sync? The man page says:

> Force  unmount  even  if busy.  This can cause data loss. 

---

### Post by tobcro on 2012-03-18
A truly excellent script! I use it for all my Linux clients at home that need to use the NFS shares on my NETGEAR ReadyNAS. Since the ReadyNAS uses its volume in the mount point (like /c/music) I decided to modify the script so its able to use separate mount points for server/client. Also, on my 11.10 it didnt seem to correctly detect if the mount was already up, so I used **proc/mounts** instead. Maybe my changes can help someone (as the original script helped me) :)

```
#!/bin/bash
# The hostname or IP-address of the fileserver:
FILESERVER="192.168.0.1"
# Check every X seconds (60 is a good default):
INTERVAL=60
# Delimeter used for separating fileserver/client shares below:
DELIMETER="|"
# The shares that need to be mounted:
MOUNTS=( "/c/music|/home/xxx/Homenet/Music" "/c/pictures|/home/xxx/Homenet/Pictures" "/c/homevideo|/home/xxx/Homenet/Homevideo" "/c/video|/home/xxx/Homenet/Video" )

declare -a MOUNTP
while true; do
	ping -c 1 "$FILESERVER" &>/dev/null
	if [ $? -eq 0 ]; then
		# Fileserver is up.
		logger "Fileserver is up."
		for MOUNT in ${MOUNTS[@]}; do
			MOUNTP=(`echo ${MOUNT//$DELIMETER/ }`) # do the split
			if grep -qs ${MOUNTP[1]} /proc/mounts; then
				logger "${MOUNTP[1]} is mounted"
			else
				# NFS mount not mounted, attempt mount
				logger "NFS shares not mounted; attempting to mount ${FILESERVER}:${MOUNTP[0]} to ${MOUNTP[1]}:"
				mount -t nfs ${FILESERVER}:${MOUNTP[0]} ${MOUNTP[1]}
			fi
		done
	else
		# Fileserver is down.
		logger "Fileserver is down."
		for MOUNT in ${MOUNTS[@]}; do
			MOUNTP=(`echo ${MOUNT//$DELIMETER/ }`) # do the split
			if grep -qs ${MOUNTP[1]} /proc/mounts; then
				# NFS mount is still mounted; attempt umount
				logger "Cannot reach ${FILESERVER}, unmounting NFS share ${MOUNTP[1]}."
				umount -f ${MOUNTP[1]}
			fi
		done
	fi
	sleep $INTERVAL
done
```

---

### Post by xlslx on 2012-07-23
Hi,

i just found this script which is pretty much useful in our data center environment. i tuned it to use "rpcinfo" instead of "ping". ping only guarantees that the server runs. rpcinfo guarantees that actually the nfs server daemon is listening for connections - which is pretty much more useful. furthermore i added some useful mountoptions and added it as a config option. i upped that script to my github account, so its freely useable by everyone. i hope this is okay for you? You`re mentioned everywhere as the original author of this cool script!

Github: [https://github.com/martinseener/yard-sale/blob/master/various-scripts/autonfs.sh]("https://github.com/martinseener/yard-sale/blob/master/various-scripts/autonfs.sh")

Thank you...

---

### Post by thinking on 2012-09-01
just wanted to mention another script which is able
to process fstab-like files and automatically mount/umount
if the corresponding host is up/down

[https://github.com/prometheus0/scripts/blob/master/sh/automounterd.sh]("https://github.com/prometheus0/scripts/blob/master/sh/automounterd.sh")

hth

---

### Post by JeroenHoek on 2012-09-02
Long overdue update: I have merged the excellent modifications made by Tobcro and xlslx, and made some minor modifications to the main script.

I've put it up on github:
[https://github.com/jdhoek/util/blob/master/autonfs.sh](https://github.com/jdhoek/util/blob/master/autonfs.sh)

Too bad I can't edit the first post. :(

---

### Post by JeroenHoek on 2012-09-03
Because older posts can no longer be edited, I have moved this howto to the Wiki: [https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto](https://help.ubuntu.com/community/AutomaticallyMountNFSSharesWithoutAutofsHowto)

I think I've got it right with the recent updates to the script. Let me know if something is wrong.

---

