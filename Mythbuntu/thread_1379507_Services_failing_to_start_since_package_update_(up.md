---
title: "Services failing to start since package update (upstart?)"
date: 2010-01-12
forum: Mythbuntu
---

### Post by s3ntinel76 on 2010-01-12
Hi,

My system was working fine, and the upgrade from Mythbuntu 9.04 to 9.10 last year went fine. But probably running 

```
sudo apt-get update/upgrade
```

and a reboot, seems to have borked the system. I'm guessing a kernel update slipped through, and has broken many things?

Remote Desktop Viewer now seems to be the only way to initialise access to the box, as I'm now having to run the following script after boot, as none of these start:

```

#!/bin/sh

/etc/init.d/mysql start
/etc/init.d/lirc start
/etc/init.d/mythtv-backend start
/etc/init.d/ssh start
/etc/init.d/apache2 start

```

Any ideas why these wouldn't be starting? I'm guessing this may be due to upstart configuration?
Many Thanks


**Update:**

Seems this is due to the karmic-updates upstart version 
[http://ubuntuforums.org/showthread.php?t=1305226&highlight=upstart]("http://ubuntuforums.org/showthread.php?t=1305226&highlight=upstart")
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520")

mythtv-backend still doesn't start automatically as it "has been converted to an Upstart job"

**Other resolved problems:**

As I'm using a Hauppauge DVB 500, I recompiled the v4l-dvb driver to get the dib0700 driver against the new kernel headers (2.6.31-14), and that seems to have fixed the 'All channels busy/sleeping' errors from the frontend.

I've also noticed apparmor messages in /var/log/messages, i.e. 
Jan 12 21:30:45 mythtv kernel: [...] type=1503 audit(...): operation="open" pid=... parent=... profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

but I'm assuming adding to /etc/apparmor.d/usr.sbin.mysqld should fix this
```
/sys/devices/system/cpu rw,
```

They should all be started, as /etc/rc3.d seems to have entries for each one except mythtv-backend:

```
$ ls -l /etc/rc3.d
total 4
-rw-r--r-- 1 root root 677 2009-11-10 09:44 README
...
lrwxrwxrwx 1 root root  13 2009-01-06 22:17 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  23 2009-01-06 22:12 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  19 2009-01-06 22:12 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  17 2009-01-06 22:15 S20apache2 -> ../init.d/apache2
...
lrwxrwxrwx 1 root root  15 2009-01-06 22:15 S20mysql -> ../init.d/mysql
...
lrwxrwxrwx 1 root root  14 2009-01-06 22:12 S51lirc -> ../init.d/lirc
...

```

However, /etc/init/mythtv-backend.conf does exist:
```
$ cat /etc/init/mythtv-backend.conf 
# MythTV Backend service

description	"MythTV Backend"
author		"Matt Mossholder <matt@mossholder.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on runlevel [016]

#expect fork
respawn

script	
	test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
	exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script
```

The end of /var/log/messages doesn't seem to show much else to help:
```
Jan 12 21:27:02 mythtv kernel: [   13.290034] i2c-adapter i2c-0: found SMSC47M192 or compatible, version 2, stepping A0
Jan 12 21:27:02 mythtv kernel: [   13.633575] dib0700: loaded with support for 14 different device-types
Jan 12 21:27:02 mythtv kernel: [   13.634113] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
Jan 12 21:27:02 mythtv kernel: [   13.634117] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
Jan 12 21:27:02 mythtv kernel: [   13.652300] smsc47m1: Found SMSC LPC47M15x/LPC47M192/LPC47M997
Jan 12 21:27:02 mythtv kernel: [   13.652344] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 12 21:27:02 mythtv kernel: [   14.063217] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
Jan 12 21:27:02 mythtv kernel: [   14.093361] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jan 12 21:27:02 mythtv kernel: [   14.277747] dib0700: firmware started successfully.
Jan 12 21:27:02 mythtv kernel: [   14.780243] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
Jan 12 21:27:02 mythtv kernel: [   14.780294] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jan 12 21:27:02 mythtv kernel: [   14.780812] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Jan 12 21:27:02 mythtv kernel: [   15.031924] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
Jan 12 21:27:02 mythtv kernel: [   15.208771] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan 12 21:27:02 mythtv kernel: [   15.267230] DiB0070: successfully identified
Jan 12 21:27:02 mythtv kernel: [   15.267235] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jan 12 21:27:02 mythtv kernel: [   15.267363] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Jan 12 21:27:03 mythtv kernel: [   15.425148] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
Jan 12 21:27:03 mythtv kernel: [   15.647327] DiB0070: successfully identified
Jan 12 21:27:03 mythtv kernel: [   15.647419] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:02:00.2/usb2/2-1/input/input3
Jan 12 21:27:03 mythtv kernel: [   15.647459] dvb-usb: schedule remote query interval to 50 msecs.
Jan 12 21:27:03 mythtv kernel: [   15.647462] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
Jan 12 21:27:03 mythtv kernel: [   15.653491] usbcore: registered new interface driver dvb_usb_dib0700
Jan 12 21:27:06 mythtv kernel: [   18.531017] usplash:326 freeing invalid memtype ffffffffcf000000-ffffffffcfe00000
Jan 12 21:30:43 mythtv kernel: [  236.074470] __ratelimit: 3 callbacks suppressed
Jan 12 21:30:43 mythtv kernel: [  236.074473] type=1503 audit(1263331843.792:13): operation="open" pid=1333 parent=1332 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
```

---

