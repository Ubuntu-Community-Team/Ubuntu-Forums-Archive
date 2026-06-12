---
title: "Remote dead after 9.04 upgrade?"
date: 2009-04-25
forum: Mythbuntu
---

### Post by xfred on 2009-04-25
I just upgraded from 8.10 to 9.04 in an attempt to fix another bug and was having some difficulty getting my remote working again.  I'm running a leadtek winfast dtv2000H tuner card with Y04G0044 remote.  I did manage to get it working under 8.10 - I wrote up the process [here]("http://ubuntuforums.org/showthread.php?t=1102033") - but this no longer works under 9.04 and I have no idea why.

So my questions are:

EDIT: what happened to the options file in modprobe.d?
1. Has anyone managed to get this remote working in 9.04?
2. Has something perhaps changed in LIRC that would mess this up?

Any suggestions would be greatly appreciated!

FWIW the setup is:

Motherboard: Asus P5KPL
CPU: intel dual core E2200
RAM: 1gb
HDD: 320GB primary drive + others 3TB
Video: Asus 7200GS HTD PE
TV tuner: LeadTek winfast DTV2000H

(probably marginal, but it works ok except for the remote)

---

### Post by superm1 on 2009-04-25
In 9.04 you need to rename anything in /etc/modprobe.d to have a ".conf" on the end.

So if you old file was called /etc/modprobe.d/blah, the new one should be /etc/modprobe.d/blah.conf

---

### Post by xfred on 2009-04-26
Update: I gave up and reloaded the old 8.10 version.
Pluses: remote now working again.
Minuses: old problem the led me to upgrade in the first place has returned.

Specifically: I want to display clone on both monitor and TV using the NVIDIA setup utility.  This is so I can watch on the TV most of the time but lug in and plug in a monitor when debugging is required.  Anyhow: this works OK *provided* the monitor is plugged in - unplug the monitor and the TV display becomes jerky and very annoying!  I've been fighting this problem for weeks now with no luck - when I go to debug (ie plug in the monitor) the problem vanishes... when I go back to TV only mode the problem is back in force.  Debugging in TV only mode isn't an option on our old TV (too fuzzy).  So I'm stuck.

I'm utterly lost here... why the fsck should it matter change anything to unplug/plug a monitor???  How can I find a cause if the symptom vanishes whenever I'm able to look for it?

Is there an option somewhere to say "pretend the monitor is there even if it isn't"???

Any help very very gratefully appreciated!

---

### Post by wittewim on 2009-04-26
I have a similar problem. This morning i had a perfect working installation (Mythbuntu 8.10). I did a network upgrade to Mythbuntu 9.04. Everything seems to be working fine except the remote.

I remember some problems configuring my remote on Mythbuntu 8.10 because i use an Antec Fusion case with an onboard volume knob that is recognized as an lirc device.

I would appreciate some help to solve the problem. At the moment i'm controlling everything with my laptop over a vnc connection

**lsusb**
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**ls -lh /dev/lirc***
```
crw-rw---- 1 root root 61, 0 2009-04-26 21:27 /dev/lirc0
crw-rw---- 1 root root 61, 1 2009-04-27 00:39 /dev/lirc1
srw-rw-rw- 1 root root     0 2009-04-27 00:45 /dev/lircd
lrwxrwxrwx 1 root root     5 2009-04-26 21:27 /dev/lirc_imon -> lirc0
lrwxrwxrwx 1 root root     5 2009-04-27 00:39 /dev/lirc_mce -> lirc1
```

**dmesg | grep irc**
```
[    8.770453] lirc_dev: IR Remote Control driver registered, major 61
[    8.979955] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[    8.979958] lirc_imon: Venky Raju <dev@venky.ws>
[    8.979979] lirc_imon: imon_probe: found IMON device
[    8.979983] lirc_dev: lirc_register_plugin: sample_rate: 0
[    8.980053] lirc_imon: imon_probe: Registered iMON plugin(minor:0)
[    8.980137] lirc_imon: imon_probe: iMON device on usb<4:2> initialized
[    8.980237] usbcore: registered new interface driver lirc_imon
[    8.981899] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[    8.981902] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[    9.244614] lirc_dev: lirc_register_plugin: sample_rate: 0
[    9.248606] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb5:2
[    9.248649] usbcore: registered new interface driver lirc_mceusb2
[   32.894555] lirc_imon: VFD port opened
[ 9757.649566] usbcore: deregistering interface driver lirc_mceusb2
[ 9757.650855] lirc_mceusb2[2]: usb remote disconnected
[ 9767.568566] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[ 9767.568570] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[ 9767.832616] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 9767.836614] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb5:2
[ 9767.836657] usbcore: registered new interface driver lirc_mceusb2
[10971.110974] usbcore: deregistering interface driver lirc_mceusb2
[10971.116706] lirc_mceusb2[2]: usb remote disconnected
[10980.335584] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[10980.335587] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[10980.600188] lirc_dev: lirc_register_plugin: sample_rate: 0
[10980.604183] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb5:2
[10980.604231] usbcore: registered new interface driver lirc_mceusb2
[11450.929822] usbcore: deregistering interface driver lirc_mceusb2
[11450.932159] lirc_mceusb2[2]: usb remote disconnected
[11479.972019] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.51 $
[11479.972022] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[11480.244147] lirc_dev: lirc_register_plugin: sample_rate: 0
[11480.248143] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb5:2
[11480.248185] usbcore: registered new interface driver lirc_mceusb2
[11553.962635] lirc_imon: IR port opened
[11559.628166] lirc_imon: IR port closed
```

**hardware.conf**
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc_mce"
#REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Options to lircd
#LIRCD_OPTIONS="--driver=default --device=/dev/lirc_mce --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:8765"
#LIRCD1_OPTIONS="--driver=default --device=/dev/lirc_imon --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid --listen"
#REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
```

**lircd.conf**
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

lircd $LIRCD1_OPTIONS
lircd $LIRCD_OPTIONS

killproc lircd
killproc lircd1

# Antec Imon wheel
#include /usr/share/lirc/remotes/imon/lircd.conf.imon-wheel

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

Everything seems  to be ok. But the remote does not working. Also irw does not show any reaction when a push the buttons on my remote

---

### Post by ctucker10 on 2009-04-26
Have a semi-dead remote on my system too. Upgraded from 8.10 to 9.04 a couple of days ago.

I have a Hauppauge PVR-250 tuner card and the remote that is packaged with it. I say it is semi-dead because I can get it to work by checking the "Generate dynamic button mappings" checkbox in Mythbuntu Control Centre and applying the change.

My problem is that after a reboot the remote is dead again. How do I make the settings persist after a system restart?

---

### Post by usererror on 2009-04-27
well sonuva-beach! I'm not the only one with a totally wacked out remote problem.

I've had a working remote in 7.10 and then it got funny, but worked in 8.10 and now 9.04 is totally killed.  i also did a network upgrade.

i'm on the mythtv irc channel and no one really knows a true fix.  I'm going to install mythbuntu 9.04 on a different pc and see if i can get the remote working out of the box.  if that DOES work.  I know what I'll be doing this week on my main hardware!](*,)

if anyone else is interested in the results let me know and i'll post them up...

---

### Post by pokogr on 2009-04-27
I am intrested. I own an HP hdx16 and i cant't get the remote control to work at all...

---

### Post by usererror on 2009-04-27
Success!

I did a fresh install of 9.04 with another PC.  At the setup point where it asks what kind of remote I have, I chose the MCEUSB2 (phillips new, et al) (something like that)

anyway, the remote DOES work and IRW does show input when I push buttons on the remote so that is good news.

Here is the frustrating part:

Originally when I could not get my remote to work on my existing myth box I was missing /dev/lirc0.  I had /dev/lircd/ and /dev/lircd0.

The fresh install has the following:

```

crw-rw---- 1 root root 61, 0 2009-04-27 05:53 lirc0
srw-rw-rw- 1 root root     0 2009-04-27 05:53 lircd

```

That is nothing like what my existing mythbox had.  I unplugged the Ir transmitter and powered off the mythtbox last night.  This morning I powered it back on, waited for it to boot, realized I was missing the iR receiver, so I plugged that in.  I restarted LIRC service, no dice.  Copied the hardware.conf and lirc.conf from the fresh install of myth to my existing box and restarted LIRC again.  This time it started correctly.  I checked /dev/lirc* and lo and behold I have /dev/lirc0 with the correct permissions:

```

crw-rw---- 1 root root 61, 0 2009-04-27 05:53 lirc0

```

But I do *not* have /dev/lircd ... and I don't know why.  I am going to attach my conf files to this post so you can try them.

If I had to sum all this up to get this remote working on a upgraded box i'd do this:

1) Check /dev/lirc*  If you do not have:
```

crw-rw---- 1 root root 61, 0 2009-04-27 05:53 lirc0
srw-rw-rw- 1 root root     0 2009-04-27 05:53 lircd

```

power off your mythbox and unplug the iR receiver.

2) Power your mythbox back on.

3) Wait for it to boot all the way then plug in the iR receiver.

4) Copy the config files included in this post to /etc/lirc/

5) Restart lirc: ```
 sudo /etc/init.d/lirc restart
``` It should give you an OK that it started up fine.

6) Verify your /dev/lirc* ... at the very least you will hopefully have:
```

crw-rw---- 1 root root 61, 0 2009-04-27 05:53 lirc0

```
7) Run irw and you should get some results with the remote:
```

000000037ff07be0 01 Down mceusb
000000037ff07bfa 00 Five mceusb
000000037ff07bf7 01 Eight mceusb
000000037ff07bff 00 Zero mceusb

```

Lets hope!

I did a complete reboot verified IRW worked and it did.  I unplugged the receiver and then plugged it back in, re-ran IRW and it still works.

Now here is what I'd like to understand:

1) Why were my /dev/lirc* devices all different from the fresh install?  Did those change somehow during upgrades?

2) Why when I first booted my mythtv up without the iR plugged in did I not get any /dev/lirc* devices?  Only after I plugged in the iR and then restarted the service (I think?) did I get /dev/lirc0 and it automatically had the correct permissions, unlike my old ones: /dev/lircd and /dev/lircd0 which are both now magically gone now too. :confused:

Still so much in linux i don't understand!

---

### Post by ctucker10 on 2009-04-27
> If I had to sum all this up to get this remote working on a upgraded box i'd do this:

This looks promising. I'll try it after work and report my results. Thanks.

---

### Post by lovinglinux on 2009-04-27
EDIT: FIXED!!!!!

w00t

The problem with my remote was that lirc wasn't able to read /etc/lirc/lircd.conf

Here is what the logs were saying about it:

```
lircd-0.8.4a[2600]: accepted new client on /dev/lircd
lircd-0.8.4a[2600]: caught signal
lircd-0.8.4a[6995]: error parsing child file value defined at line 13:
lircd-0.8.4a[6995]: invalid quoting
lircd-0.8.4a[6995]: reading of file '/etc/lirc//lircd.conf' failed
lircd-0.8.4a[6995]: reading of config file failed
lircd-0.8.4a[6996]: lircd(pinsys) ready
lircd-0.8.4a[6996]: accepted new client on /dev/lircd
lircd-0.8.4a[6996]: removed client
```


lircd.conf content is actually just an include statement to grab the the real configuration from /usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv

So I copied the content of /usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv to /etc/lirc/lircd.conf and commented the "include" line.

It works!

---

### Post by usererror on 2009-04-27
Where are the lirc logs stored?  I can't seem to find mine...

is that after you did the steps that I used above?

---

### Post by lovinglinux on 2009-04-27
> **usererror said:**
> Where are the lirc logs stored?  I can't seem to find mine...

In the daemon.log, but since it started working there are no more records about lirc in it.

> **usererror said:**
> is that after you did the steps that I used above?

Nope. It seems that my problem was completely unrelated. I still do not have a lirc0, but I always has a lircd file.

---

### Post by wittewim on 2009-04-28
My problem is solved. It was as simple as quoting the include path

from
```
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```

to
```
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
```

---

### Post by superm1 on 2009-04-28
> **wittewim said:**
> My problem is solved. It was as simple as quoting the include path

from
```
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```to
```
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
```
That was "supposed" to automatically happen.  Odd that it didn't..

---

### Post by lovinglinux on 2009-04-28
> **superm1 said:**
> That was "supposed" to automatically happen.  Odd that it didn't..

I guess this is the same problem I had. My solutions was to add the code to the default file instead linking it with the "include". Anyways, I didn't configured it using the configuration manager, I just copied the conf files from my backup. So I guess lirc is not recognizing the command without quotes anymore.

---

### Post by CrowBelgrade on 2009-04-28
I have prolem with lirc. When I tray to strat Lirc on System>Administration>Lirc OS is stop responding. I tray 2 week to setup Lirc on Kworld PVR Plus Philips chipset 7134

---

### Post by Lytse on 2009-04-28
Mine is still not working. It was working in 8.10 but not in Jaunty. I could use some help :S

have htpc:~$ lsmod | grep lirc
lirc_imon              26636  1
lirc_dev               22088  1 lirc_imon

also have htpc:~$ strace modprobe lirc_imon 2>&1 | grep lib/modules
open("/lib/modules/2.6.28-11-generic/modules.dep.bin", O_RDONLY) = 3
open("/lib/modules/2.6.28-11-generic/updates/dkms/lirc_dev.ko", O_RDONLY) = 3
open("/lib/modules/2.6.28-11-generic/updates/dkms/lirc_imon.ko", O_RDONLY) = 3

and: Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 15c2:0038 SoundGraph Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and: htpc:~$ ls /dev/{lirc,lcd}*
/dev/lcd0  /dev/lcd1  /dev/lirc0  /dev/lirc1  /dev/lircd

any ideas?

---

### Post by lovinglinux on 2009-04-28
> **Lytse said:**
> Mine is still not working. It was working in 8.10 but not in Jaunty. I could use some help :S

have htpc:~$ lsmod | grep lirc
lirc_imon              26636  1
lirc_dev               22088  1 lirc_imon

also have htpc:~$ strace modprobe lirc_imon 2>&1 | grep lib/modules
open("/lib/modules/2.6.28-11-generic/modules.dep.bin", O_RDONLY) = 3
open("/lib/modules/2.6.28-11-generic/updates/dkms/lirc_dev.ko", O_RDONLY) = 3
open("/lib/modules/2.6.28-11-generic/updates/dkms/lirc_imon.ko", O_RDONLY) = 3

and: Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 15c2:0038 SoundGraph Inc.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and: htpc:~$ ls /dev/{lirc,lcd}*
/dev/lcd0  /dev/lcd1  /dev/lirc0  /dev/lirc1  /dev/lircd

any ideas?

It would help if you could post the content of these files:

~/.lircrc
/etc/lirc/hardware.conf
/etc/lirc/lircd.conf
/etc/lirc/lircmd.conf

Also post the output of this command:

```
cat /var/log/daemon.log | grep lirc
```

---

### Post by CrowBelgrade on 2009-04-29
crow@crow:~$ cat /var/log/daemon.log | grep lirc
Apr 28 22:51:43 crow lircd-0.8.4a[18964]: invalid code found for lirc.conf: Enter
Apr 28 22:51:43 crow lircd-0.8.4a[18965]: lircd(devinput) ready
Apr 28 22:52:38 crow lircd-0.8.4a[18965]: accepted new client on /dev/lircd
Apr 28 22:52:38 crow lircd-0.8.4a[18965]: initializing '/dev/input/event5'
Apr 28 22:52:58 crow lircd-0.8.4a[18965]: removed client
Apr 28 22:52:58 crow lircd-0.8.4a[18965]: closing '/dev/input/event5'
Apr 28 22:53:12 crow lircd-0.8.4a[18965]: accepted new client on /dev/lircd
Apr 28 22:53:12 crow lircd-0.8.4a[18965]: initializing '/dev/input/event5'
Apr 28 22:53:30 crow lircd-0.8.4a[18965]: removed client
Apr 28 22:53:30 crow lircd-0.8.4a[18965]: closing '/dev/input/event5'
Apr 28 22:53:37 crow lircd-0.8.4a[18965]: caught signal
Apr 28 22:54:25 crow lircd-0.8.4a[2379]: invalid code found for lirc.conf: Enter
Apr 28 22:54:25 crow lircd-0.8.4a[2380]: lircd(devinput) ready
Apr 28 22:55:23 crow lircd-0.8.4a[2380]: accepted new client on /dev/lircd
Apr 28 22:55:23 crow lircd-0.8.4a[2380]: initializing '/dev/input/event5'
Apr 28 22:55:27 crow lircd-0.8.4a[2380]: removed client
Apr 28 22:55:27 crow lircd-0.8.4a[2380]: closing '/dev/input/event5'
Apr 28 23:02:17 crow lircd-0.8.4a[2380]: accepted new client on /dev/lircd
Apr 28 23:02:17 crow lircd-0.8.4a[2380]: initializing '/dev/input/event5'
Apr 28 23:03:25 crow lircd-0.8.4a[2380]: removed client
Apr 28 23:03:25 crow lircd-0.8.4a[2380]: closing '/dev/input/event5'
Apr 28 23:05:11 crow lircd-0.8.4a[2380]: caught signal

---

### Post by lovinglinux on 2009-04-29
> **CrowBelgrade said:**
> Apr 28 22:51:43 crow lircd-0.8.4a[18964]: invalid code found for lirc.conf: 

When you installed lirc, did you configure it through a graphical interface?

Post the content of the files suggested on my previous post.

---

### Post by Lytse on 2009-04-29
This hints me for checking myth control center...
And yes, it was still switched on...

I'll restart and generate the files.
...
Another restart because mcc cannot leave the files alone.
It's worse :S
...
Another restart because missed a line in lircd. Force reboot.
everything up now, but remote is not working.
...
Restart to use the lircd.conf from [http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474). No luck.

---

### Post by gator on 2009-04-29
i have upgraded from mythbuntu 8.10 to 9.04 and the remote worked for a while but it locked up the other night. Changed batterys and restarted. i thought it was a one off lockup. However ive installed mythbuntu 9.04 on a friends machine and used the same remote and receiver but it locks up regular. Pressing Alt-F2 and restarting lirc does not restart the remote - it remains locked until reboot.( the menu's still work with keyboard.:confused: I was browsing to see if anyone else was having a prob when i found this thread. Maybe its my remote?

---

### Post by lovinglinux on 2009-04-29
> **Lytse said:**
> This hints me for checking myth control center...
And yes, it was still switched on...

I'll restart and generate the files.
...
Another restart because mcc cannot leave the files alone.
It's worse :S
...
Another restart because missed a line in lircd. Force reboot.
everything up now, but remote is not working.
...
Restart to use the lircd.conf from [http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474). No luck.


I'm almost sure your problem resides in the file /etc/lirc/hardware.conf, because your log says "could not get file information for /dev/lirc0" and  you have a lot of stuff there that I don't.  Let's try a simple modification in the file first.

Replace this line on /etc/lirc/hardware.conf

```
REMOTE_MODULES="lirc_dev lirc_imon"
```

with

```
REMOTE_MODULES="false"
```

Save it.

Launch lirc again

```
sudo /etc/init.d/lirc restart
```

If it works, you should get something like this:

```
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
```

Then test the remote input running the following command and pressing a few buttons in the remote:

```
irw
```

You should get something like this:

```
~$ irw
0000000000fec63e 00 Chan-Stop PinnacleSysPCTVRemote
0000000000fec63e 00 Chan-Stop PinnacleSysPCTVRemote
0000000000fec63e 01 Chan-Stop PinnacleSysPCTVRemote
0000000000fec63e 00 Chan-Stop PinnacleSysPCTVRemote
```

If you get these kind of output when running irw test then you are good to go.

If it doesn't work, then try replacing all instances of /dev/lirc0 with /dev/ttyS0 in hardware.conf and repeat the procedure above.

---

### Post by Lytse on 2009-04-30
Thanks for the help 'lovingLinux'!

I followed your instructions and got this.

xxxx@xxxxshtpc:~$ sudo vim /etc/lirc/hardware.conf
[sudo] password for xxxx:
xxxx@xxxxshtpc:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ]
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
xxxx@xxxxshtpc:~$ irw
connect: Connection refused
xxxx@xxxxshtpc:~$ sudo vim /etc/lirc/hardware.conf
xxxx@xxxxshtpc:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ]
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
xxxx@xxxxshtpc:~$ irw
connect: Connection refused

Besides that I also found this link ([http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html](http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html)).
Do you think lirc 0.8.4a does not correctly support the Antec Fusion Remote Black?

When i change back irw starts and i see this entries in the log:
Apr 30 09:08:48 xxxxshtpc lircd-0.8.4a[1701]: accepted new client on /dev/lircd
Apr 30 09:14:43 xxxxshtpc lircd-0.8.4a[1701]: accepted new client on /dev/lircd
Apr 30 09:14:53 xxxxshtpc lircd-0.8.4a[1701]: removed client

Sometimes I also get some extra lirc devices ???

But mode2 gives
xxxx@xxxxshtpc:~$ sudo mode2 --raw --device=/dev/lirc1

code: 0x28a3d5b7
code: 0x28a395b7


These are keys i didn't code in lircd?

---

### Post by lovinglinux on 2009-04-30
> **Lytse said:**
> When i change back irw starts and i see this entries in the log:
Apr 30 09:08:48 xxxxshtpc lircd-0.8.4a[1701]: accepted new client on /dev/lircd
Apr 30 09:14:43 xxxxshtpc lircd-0.8.4a[1701]: accepted new client on /dev/lircd
Apr 30 09:14:53 xxxxshtpc lircd-0.8.4a[1701]: removed client

So keep the way it was. Don't use my modification, because it was already working. The code above shows that the client was accepted, so there is no error.

> **Lytse said:**
> Besides that I also found this link ([http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html](http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html)).
Do you think lirc 0.8.4a does not correctly support the Antec Fusion Remote Black

I think this is possible. The instructions on the link you provided are very straight forward. 

Do this

[http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html](http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html)

Then this
[http://avenard.com/media/Patches_%26_Add-Ons/Entries/2008/10/9_RM200_remote_with_LIRC.html](http://avenard.com/media/Patches_%26_Add-Ons/Entries/2008/10/9_RM200_remote_with_LIRC.html)

But ignore the line that says:

> *First, make sure you get LIRC working with the IR receiver. Follow the instructions here.*

Tell me if it works, because it could be the same problem I'm trying to help on the other thread.

---

### Post by Lytse on 2009-05-01
I tried this patch before including the LCDd part, i am now suspecting that. I'll continue that path after the weekend.

---

### Post by CrowBelgrade on 2009-05-02
Huh in my Home i dont have any .lirc folder and to etc/lirc I have onli lirc.hardware old :confused:

---

### Post by CrowBelgrade on 2009-05-02
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="false"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

----------------------------------------------------------------
lircd.conf
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter
------------------------------------------------------------------
#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian

---

### Post by superm1 on 2009-05-02
> **CrowBelgrade said:**
> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="false"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

----------------------------------------------------------------
lircd.conf
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter
------------------------------------------------------------------
#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#    /usr/share/doc/lirc/README.Debian

Just reset your remote in MCC or run these two commands:
```

sudo dpkg-reconfigure lirc

mythbuntu-lirc-generator
```

---

### Post by anorexi@ on 2009-05-02
i am going to be  crazy i made everything but i didnt remote kaffeine even though i got signal with irw on terminal 

[[IMG]http://img9.imageshack.us/img9/8458/ekrangrntsz.png[/IMG]](http://img9.imageshack.us/my.php?image=ekrangrntsz.png)


[COLOR="Red"]and this is the screenshot /root/.lirc/kaffeine content[/COLOR]

[[IMG]http://img9.imageshack.us/img9/6209/ekrangrnts1u.png[/IMG]](http://img9.imageshack.us/my.php?image=ekrangrnts1u.png)

[COLOR="Red"]ant thats the whole kaffeine file[/COLOR]

[HTML]#----------------------#
# Kaffeine lirc setup
#----------------------#
begin
        remote = mceusb
        prog = kaffeine
        button = Play
        config = dcop kaffeine KaffeineIface playDvb
        config = dcop kaffeine KaffeineIface pause
        repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Pause
        config = dcop kaffeine KaffeineIface pause
        config = dcop kaffeine KaffeineIface playDvb
        repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = More
        config = dcop kaffeine KaffeineIface dvbOSD
end
begin
        remote = mceusb
        prog = kaffeine
        button = Stop
        config = dcop kaffeine KaffeineIface stop
end
begin
        remote = mceusb
        prog = kaffeine
        button = Right
        config = dcop kaffeine KaffeineIface posPlus
end
begin
        remote = mceusb
        prog = kaffeine
        button = Left
        config = dcop kaffeine KaffeineIface posMinus
end
begin
        remote = mceusb
        prog = kaffeine
        button = ChanUp
        config = dcop kaffeine KaffeineIface next
end
begin
        remote = mceusb
        prog = kaffeine
        button = ChanDown
        config = dcop kaffeine KaffeineIface previous
end
begin
        remote = mceusb
        prog = kaffeine
        button = Power
        config = dcop kaffeine KaffeineIface quit
end
begin
        remote = mceusb
        prog = kaffeine
        button = VolUp
        config = dcop kaffeine KaffeineIface volUp
end
begin
        remote = mceusb
        prog = kaffeine
        button = Mute
        config = dcop kaffeine KaffeineIface mute
end
begin
        remote = mceusb
        prog = kaffeine
        button = VolDown
        config = dcop kaffeine KaffeineIface volDown
end
begin
        remote = mceusb
        prog = kaffeine
        button = OK
        remote = mceusb
        config = dcop kaffeine KaffeineIface fullscreen
end
begin
        remote = mceusb
        prog = kaffeine
        button = Up
        config = dcop kaffeine KaffeineIface dvbOSDNextChannel
end
begin
        remote = mceusb
        prog = kaffeine
        button = Down
        config = dcop kaffeine KaffeineIface dvbOSDPreviousChannel
end
#begin
#        remote = mceusb
#        prog = kaffeine
#        button = Left
#        config = dcop kaffeine KaffeineIface dvbOSDNextProgram
#end
#begin
#        remote = mceusb
#        prog = kaffeine
#        button = Right
#        config = dcop kaffeine KaffeineIface dvbOSDPreviousProgram
#end
begin
        remote = mceusb
        prog = kaffeine
        button = One
        config = dcop kaffeine KaffeineIface setNumber 1
        repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Two
        config = dcop kaffeine KaffeineIface setNumber 2
        repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Three
        config = dcop kaffeine KaffeineIface setNumber 3
   repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Four 
        config = dcop kaffeine KaffeineIface setNumber 4
   repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Five
        config = dcop kaffeine KaffeineIface setNumber 5
   repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Six
        config = dcop kaffeine KaffeineIface setNumber 6
   repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Seven
        config = dcop kaffeine KaffeineIface setNumber 7
   repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Eight
        config = dcop kaffeine KaffeineIface setNumber 8
   repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Nine
        config = dcop kaffeine KaffeineIface setNumber 9
   repeat = 0
end
begin
        remote = mceusb
        prog = kaffeine
        button = Zero
        config = dcop kaffeine KaffeineIface setNumber 0
   repeat = 0
end [/HTML]


[COLOR="Red"]and this is the screenshot of  /root/.lirc content[/COLOR]

[[IMG]http://img70.imageshack.us/img70/8140/ekrangrnts2.png[/IMG]](http://img70.imageshack.us/my.php?image=ekrangrnts2.png)


plz help me how can i remote kaffeine my remote device is mce remote model 1039

---

### Post by CrowBelgrade on 2009-05-02
sudo dpkg-reconfigure lirc
I dont see my tv card 114 Kworld

---

### Post by lovinglinux on 2009-05-02
> **CrowBelgrade said:**
> sudo dpkg-reconfigure lirc
I dont see my tv card 114 Kworld

Select "Custom". After installation, check if there is a config file available for your remote control at the LIRC homepage and copy it to /etc/lirc/lircd.conf. If not, start irrecord (finish all applications that access /dev/lirc first) and follow the instructions given to you by this program. Copy the resulting file to /etc/lirc/lircd.conf. If you have trouble creating a working config file please read the chapter about adding new remote controls.

Mor info: [http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)

---

### Post by CrowBelgrade on 2009-05-02
* Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ]
But not working. I using Tv time for watch Tv :confused:

---

### Post by lovinglinux on 2009-05-02
> **CrowBelgrade said:**
> * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ]
But not working. I using Tv time for watch Tv :confused:

Run irw command and press the remote buttons to see if they are being captured or not.

---

### Post by CrowBelgrade on 2009-05-03
Nope. Dont work.

---

### Post by Lytse on 2009-05-06
I got lirc working with my remote using the patch provided on [http://avenard.com/media/Home.html](http://avenard.com/media/Home.html).

The problem that it did not work before was that MCC installed it's own drivers :confused:

I am not so happy with the lcdmon library provided on this site because it does not work with xbmc. (lcd stops working and system hangs during shutdown)

Maybe I should look into the LCDproc procedure of [http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474)

Anyone any progress too?

---

### Post by usererror on 2009-05-06
Well much to my annoyance I just moved my mythbox around, had everything unplugged and when i fired it back up the remote does not work again!!  in fact the whole system is freezing again, just like it did when I was trying to get the remote working after the upgrade.  I don't know if they are related but that was my original guess.  Back to trying my steps above to see if they work, but i just don't have the time tonight. ](*,)

On boot up now lircd fails to start.

I manually stop the service.
I unplug my ir receiver.
i plug it back in.
i manually start the service, it fails.
i manually *restart* the service, it starts
irw receives blasts.
I restart mythfront end and everything is A-OK.

What should I look for in the logs to find out why it fails on start up?


UPDATE: I had some time today.  I did my earlier steps on the first page of this post, except i made one modification. I moved /etc/lirc to /etc/lirc.old.  made a new /etc/lirc and copied the 3 files in the attachment to my other post and everything works again.

---

### Post by Lytse on 2009-05-07
I think it works now. Use the lirc procedure from [http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html](http://avenard.com/media/Patches_%26_Add-Ons/Entries/2009/4/10_LIRC_to_work_with_Antec_Fusion_Remote_Black_(jaunty).html) and the lcdmon from the 8.10 patch.

Thing is that the server screen keeps blinking through the xbmc screens but that could be a xbmc problem. anyone

---

