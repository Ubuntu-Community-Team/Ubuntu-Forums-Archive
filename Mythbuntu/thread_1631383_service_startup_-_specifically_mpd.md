---
title: "service startup - specifically mpd"
date: 2010-11-26
forum: Mythbuntu
---

### Post by slaterson on 2010-11-26
i have a semi-complicated mythbuntu box.  it uses ldap for authentication, runs two instances of mpd, one instance of mythtv and mounts all data via nfs (the local disk is there to hold the os and local config & logging info).  hardware wise, its got three soundcards (two rme96 and one intel hda) and an nvidia geforce graphics card.  originally installed mythbuntu 10.04, upgraded it to 10.10 using the official instructions several days after 10.10 was available.  box has been kept up to date on a ~weekly basis.

ldap is working perfectly.  mythtv is working perfectly.  both mpd instances are working - however i must start them manually with 'sudo service mpd1 start' and 'sudo service mpd2 start' at the command line when the box reboots.

here is what i have done to try to get this working:
1) copied /etc/default/mpd to /etc/default/mpd1 and mpd2 & changed MPDCONF to /etc/mpd1.conf and /etc/mpd2.conf respectively.  Set /etc/default/mpd1 and /etc/default/mpd2 START_MPD value to 'true'.
2) created correct /etc/mpd1.conf and /etc/mpd2.conf files (verified working - everything works great when starting the services manually).
3) copied /etc/init.d/mpd to /etc/init.d/mpd1 and /etc/init.d/mpd2.  also copied /etc/init.d/mpd.dpkg-dist to mpd1.dpkg-dist and mpd2.dpkg-dist.
4) edited /etc/init.d/mpd1 and mpd2 as well as the .dpkg-dist files to point to the correct conf files, use the correct names/descriptions, pid file, etc...
5) added mpd1 and mpd2 to the run levels with a 98 for startup, 02 for shutdown (trying to ensure they start last and shutdown first due to ldap and nfs mounting of the data).

when i reboot, the two mpd service do not start.  if i ssh in and 'sudo service mpd1 start' and 'sudo service mpd2 start' they both start right up, no errors or warnings, and work perfectly.

what am i missing here?  i have been pulling my hair out trying to get thee services to start automatically, its the last piece of the puzzle for this box...

any help is greatly appreciated.  would love to get the mpd instances starting automatically.

---

### Post by ian dobson on 2010-11-26
Hi,

If mpd doesn't use upstart to start them you'll need to make sure that the symbolic links in /etc/rcX.d are set correctly. Note the X in the dir name is the runlevel in which the service should be started/stopped. The name of the symbolic link should be something like S20xxxx  where S means start and 20 is the position in the list (19 starts before 20) and a K means Kill.

Regards
Ian Dobson

---

### Post by slaterson on 2010-11-26
> **ian dobson said:**
> If mpd doesn't use upstart to start them you'll need to make sure that the symbolic links in /etc/rcX.d are set correctly. Note the X in the dir name is the runlevel in which the service should be started/stopped. The name of the symbolic link should be something like S20xxxx  where S means start and 20 is the position in the list (19 starts before 20) and a K means Kill.

the links are set correctly as far as i can tell...

```
/etc/rc2.d$ runlevel
N 2
/etc/rc2.d$ ls -l
total 4
lrwxrwxrwx 1 root root  22 2010-11-24 22:57 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  17 2010-11-24 22:56 K20postfix -> ../init.d/postfix
lrwxrwxrwx 1 root root  19 2010-11-24 22:57 K30dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2010-11-24 22:57 K30pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  19 2010-11-24 22:57 K74bluetooth -> ../init.d/bluetooth
-rw-r--r-- 1 root root 677 2010-11-01 09:36 README
lrwxrwxrwx 1 root root  14 2010-08-27 21:14 S19lirc -> ../init.d/lirc
lrwxrwxrwx 1 root root  20 2010-08-28 18:07 S20fancontrol -> ../init.d/fancontrol
lrwxrwxrwx 1 root root  14 2010-11-24 22:56 S20gssd -> ../init.d/gssd
lrwxrwxrwx 1 root root  17 2010-08-29 15:41 S20hddtemp -> ../init.d/hddtemp
lrwxrwxrwx 1 root root  16 2010-11-24 22:56 S20idmapd -> ../init.d/idmapd
lrwxrwxrwx 1 root root  21 2010-08-27 22:05 S20libnss-ldap -> ../init.d/libnss-ldap
lrwxrwxrwx 1 root root  25 2010-11-24 23:06 S20network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root  17 2010-11-24 22:56 S20portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root  20 2010-11-24 22:56 S20rpc_pipefs -> ../init.d/rpc_pipefs
lrwxrwxrwx 1 root root  23 2010-08-29 15:40 S20smartmontools -> ../init.d/smartmontools
lrwxrwxrwx 1 root root  15 2010-08-28 18:07 S20snmpd -> ../init.d/snmpd
lrwxrwxrwx 1 root root  15 2010-11-24 22:56 S20statd -> ../init.d/statd
lrwxrwxrwx 1 root root  15 2010-08-27 21:14 S21aumix -> ../init.d/aumix
lrwxrwxrwx 1 root root  13 2010-08-27 21:14 S23ntp -> ../init.d/ntp
lrwxrwxrwx 1 root root  15 2010-10-29 07:37 S50rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  14 2010-10-29 07:36 S75sudo -> ../init.d/sudo
lrwxrwxrwx 1 root root  17 2010-08-27 21:14 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  17 2010-09-10 09:35 S98mpd1 -> ../init.d/mpd1
lrwxrwxrwx 1 root root  18 2010-09-02 14:29 S98mpd2 -> ../init.d/mpd2
lrwxrwxrwx 1 root root  21 2010-08-27 21:14 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root  18 2010-08-27 21:14 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-08-27 21:14 S99rc.local -> ../init.d/rc.local
```

am i overlooking something?  the above is for runlevel 2, reported as the runlevel using the 'runlevel' command when i ssh in.  odd thing, when looking at the runlevel wiki, it states the system should be in runlevel 3 for a normal multi-user system start.

---

### Post by ian dobson on 2010-11-27
Hi,

so what happens when you try and start S98mpd1 from the /etc/rc2.d directory?

Regards
Ian Dobson

---

### Post by slaterson on 2010-11-27
```
/etc/rc2.d$ sudo /etc/rc2.d/S98mpd1 start
 * Starting Music Player Daemon - 1 mpd1      [ OK ]
```

and everything starts as expected.  the same happens when i run 'sudo service mpd1 start'.

the only think i can think of is that during system start up, mpd is being started before the nfs mounts are done.  both mpd instances store their playlist, database and state files remotely on the nfs mount, without these i'm not sure will start.

---

### Post by ian dobson on 2010-11-27
Hi,

If the worst comes to the worst just start the deamons through /etc/rc.local. Not a nice solution but it'll work.

Is the sql database on the same box and do you have a fixed IP address for the box (not using dhcp). The only thing I can think of is that your using dhcp and it's taking time for the network interface to get am ip.

Regards
Ian Dobson

---

### Post by slaterson on 2010-11-27
i am using dhcp (which is fixed, but still needs time to get the address).

there is no sql db for mpd, it uses a text file based database (however mysql is running on the machine for mythtv).  isn't there a way to add dependencies to services?  i.e., service 2 waits for service 1 to finish starting up before it starts.  starting mpd so late (#98 in the list!) should do the trick, i think, but its obviously not.  its as if its not even being called.

lastly, how do i go about seeing the startup sequence and responses on screen during boot up (or a log of all startup text after boot)?  not dmesg, rather the list of services that are starting and their response text.

thanks!

---

### Post by ian dobson on 2010-11-27
Hi,

Maybe you see something in /var/log/boot (I'm not sure).

A simple solution would be to add a sleep 10 to the startup scripts. Other than that maybe a loop checking the output of ifconfig that only exits the loop when the interface has a IP address.

Does mpd have a log that you can check, what happend it you end ntp then try starting mpd?

Regards
Ian Dobson

---

### Post by slaterson on 2010-11-27
finding /var/log/boot.log has helped a lot.  looks like there are a couple services there require the network starting before the network is up.  for instance, nfs.  it also can't connect to the ldap server when mpd is trying to start, so the user and group (and nfs mount!) aren't present.  no wonder it doesn't start.

next thing to figure out...  how do i make mount.nfs and mpd wait until the network is up and fully functional...

---

### Post by ian dobson on 2010-11-27
Hi,

Maybe something like:-

```
#!/bin/bash
status=""
while [ "$status" == "" ]
do
        status=`ifconfig eth3 | grep  "inet addr"`
        sleep 1
        echo $status
done
```

It just sits in a loop running ifconfig every second waiting for eth3 to have a valid ip4 address.

Regards
Ian Dobson

---

### Post by slaterson on 2010-11-27
i'll give that a try...

one other question that came to mind.  how do i determine if mpd is using upstart?

---

### Post by slaterson on 2010-11-27
some additional info from /var/log/boot.log:

```
mount.nfs: Failed to resolve server 192.168.110.2: Name or service not known
mountall: mount /mnt/media/1 [910] terminated with status 32
mount.nfs: Failed to resolve server 192.168.110.2: Name or service not known
mountall: mount /home [911] terminated with status 32
/dev/sda1: clean, 235/2003424 files, 85041/3999744 blocks
```

this is really odd to me, when i log in or ssh in after the box is booted, the nfs mounts are mounted.  seems like maybe some services are being started twice, once before the network is ready and once after the network is ready OR being started using two methods (i.e. upstart and traditional init scripts)?

---

### Post by ian dobson on 2010-11-27
> **slaterson said:**
> i'll give that a try...

one other question that came to mind.  how do i determine if mpd is using upstart?

Just have a look in /etc/init/  for a file mpd.conf.

ps What version of ubuntu are you running.

Regards
Ian Dobson

---

### Post by slaterson on 2010-11-27
nothing in /etc/init for mpd (no mpd.conf, mpd1.conf or mpd2.conf).  i have removed all rcX.d links to mpd now, searching for some info on creating my own (or copying someone else's).

really odd about the nfs mounting, i'd like to clean that up, i just realized this was happening today.

i started with mythbuntu 10.04 on a clean hard drive.  kept it up to date with apt-get update/upgrade and then followed the ubuntu docs to upgrade the system to 10.10 once mythbuntu 10.10 was available.  have been keeping it up to date since upgrading as well (some things started working better with the 10.10 upgrade so i know the upgrade went well and was beneficial).

---

### Post by slaterson on 2010-11-27
i've got mpd starting on reboot now, but its starting before the nfs mounts.  mpd reports 0 songs in the database.

based on some info i found i created a mpd1.conf like so:

```
# MPD CDs service

description     "MPD CDs"
author          "CSC"

start on (remote-filesystems and net-device-up IFACE=eth0)
stop on starting shutdown

expect fork

pre-start script
        /etc/init.d/mpd1 start
end script

pre-stop script
        /etc/init.d/mpd1 stop
end script
```

so this starts up mpd but before the nfs share is mounted.  mpd (expectedly) reports:

```
Nov 27 13:40 : state_file: failed to open /mnt/media/1/audio/mpd/state1: No such file or directory
Nov 27 13:40 : database: unable to write to db file "/mnt/media/1/audio/mpd/database1": No such file or directory
```

in fact the files are there and correct.  if i restart using 'sudo service mpd1 stop' and then 'sudo service mpd1 start' everything runs fine.  is i use 'restart' instead of stop then start, its not.

i think i know what the problem is here - mpd1 & 2 need to verify that the network is up, the nfs mounts are mounted and ldap is accessible and THEN start - just not sure how to make that happen.

---

### Post by ian dobson on 2010-11-28
Hi,

Not quite. the pre-start is usually used to run something before starting the deamon. I this case we could use it to wait until the network is up.

Something like:-

```

pre-start script
while [ ! -s /some/file/on/your/nfs/mount/file.xml ]
  do
  sleep 1 
done
end script

```

and you just start mpg with a single liner. So you conf file should look like this:-
# MPD CDs service

```

description     "MPD CDs"
author          "CSC"

start on (remote-filesystems and net-device-up IFACE=eth0)
stop on starting shutdown

expect fork

pre-start script
while [ ! -s /some/file/on/your/nfs/mount/file.xml ]
  do
  sleep 1 
done
end script

exec /etc/init.d/mpd1 start


```

Regards
Ian Dobson

---

### Post by slaterson on 2010-11-29
this works perfectly ian!  thanks!

it takes a surprising amount of time for the mpd instances to start up and become available.  to keep things relative, its only a few seconds after i hear the bios beep, literally maybe only 5, so not much to complain about. :)

---

