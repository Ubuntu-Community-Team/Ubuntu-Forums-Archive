---
title: "HOWTO: Automatically mount remote filesystems (NFS, Samba, SSHFS, FTP, etc.)"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by oscarjd74 on 2011-04-02
**Summary**
Automatically mount remote filesystems (NFS, Samba, SSHFS, FTP, etc.) whenever their fileserver is up. A simple bash script is started as a custom upstart job, periodically checks the availability of servers and mounts/unmounts remote filesystems accordingly.

**Introduction**
The available remote filesystems for a laptop, notebook or tablet change when it is carried around to another location. The NFS shares in your home LAN are not available when you are at work. A FTP share might be available both at home and at work, but not while you are working offline in a plane. Wouldn't it be convenient if your system automatically checks which fileservers are up and mount/unmount these filesystems accordingly? That's exactly what this setup does.

**Prerequisites**
[LIST]
[*] The fileservers are set up and added to the client's /etc/fstab. A ton of places on the internet explain how to do that for various types of fileservers so I won't go into it here.
[*] The client can ping the fileservers to determine their availability.
[*] You have administrator access to the client.
[/LIST]

**Installation**
[LIST=1]
[*] Open a terminal, become root and fork into your favourite text editor (gedit for example). You will be asked for the administrator's password after the first command.```
sudo su
gedit &
```
[*] Copy the following bash script into a new file and save it as /usr/local/sbin/amntd. You may want to change the INTERVAL=60 line according to your needs. It is the delay in seconds between consecutive checks of server availability.```
#!/bin/bash
test -r /etc/amntd.conf || exit 1
INTERVAL=60

s=-1; m=-1
while read line; do
    if echo "$line" | egrep -q '^[[:space:]]*$'; then continue; fi
    if echo "$line" | egrep -q '^\[.*\]$'; then
        s=$(($s+1))
        SRV[$s]="${line:1:$((${#line}-2))}"
    else
        m=$(($m+1))
        MNT[$m]="$line"
    fi
    LMNT[$s]=$m
done < /etc/amntd.conf

while true; do
    s=0; m=0
    while [ $s -lt ${#SRV[@]} ]; do
        ping -c 1 "${SRV[$s]}" &>/dev/null && up=1 || up=0
        while [ $m -le ${LMNT[$s]} ]; do
            if [ $up -eq 1 ]; then
                if ! mount | grep -q " ${MNT[$m]} "; then mount "${MNT[$m]}"; fi
            else
                if mount | grep -q " ${MNT[$m]} "; then umount "${MNT[$m]}"; fi
            fi
            m=$(($m+1))
        done
        s=$(($s+1))
    done
    sleep $INTERVAL
done
```
[*] Copy the following upstart job configuration into another new file and save it as /etc/init/amntd.conf.```
description "Automount daemon (amntd)"
start on filesystem
respawn
exec /usr/local/sbin/amntd
```
[*]Put your personal amntd configuration into a third new file and save it as /etc/amntd.conf. There is one section for each fileserver. At the start of a section the hostname or IP-address of the fileserver is put on a single line enclosed in square brackets. This is followed by the mount points for this fileserver, each on a single line. The mount points correspond to the mount points in /etc/fstab (or more exactly: to the mount points in the output of the mount command).

The following is just an example. You'll have to adjust it according to your setup and needs.```
[myhomeserver.local]
/mnt/backup

[myhomeserver.com]
/home/grouch/myMusic
/home/grouch/myDocuments

[serveratwork.com]
/home/grouch/work
```
[*] Switch back to the terminal, make the bash script executable and start the daemon.```
chmod a+x /usr/local/sbin/amntd
start amntd
```
[/LIST]

That's it! From now on your remote filesystems are mounted and unmounted automatically!



Credits to JeroenHoek whose earlier post ([http://ubuntuforums.org/showthread.php?t=1389291](http://ubuntuforums.org/showthread.php?t=1389291)) inspired much of this.

---

### Post by dlane on 2012-08-07
oscarjd74, many thanks for taking the time to describe your solution - this problem has be plaguing me for ages, and I was sure there had to be a reasonably elegant way to make this work.

---

### Post by wildmanne39 on 2012-08-07
Old thread closed.

---

