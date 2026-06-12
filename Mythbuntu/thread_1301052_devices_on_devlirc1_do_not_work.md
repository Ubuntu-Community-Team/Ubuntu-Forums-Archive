---
title: "devices on /dev/lirc1 do not work"
date: 2009-10-25
forum: Mythbuntu
---

### Post by Don Giovanni on 2009-10-25
*Solved see bottom of post*
I have an issue where devices set to /dev/lirc0 will work but devices set to /dev/lirc1 will not.

remote(ir receiver) on lirc0 and ir transmitter on lirc1 = remote only works
If i switch it around
transmitter to lirc0 and remote to lirc1 = transmitter only works

I've tested both devices and they are both fully functional when assigned to lirc0 but both stop working when assigned to lirc1.  So for some reason lirc1 isn't being looked at or isn't loading properly

If I look under /dev/   lirc0, lirc1, lircd and lircd1 are all there.

Here are my current configs.

/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#

#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="SRC-200A_3"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="mts/lircd.conf.mts"
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
```

/etc/lirc/lircd.conf
```
#/etc/lirc/lircd.conf
#
#Moved transmitter entry in front of remote entry
#Neither will function if transmitter is entered second
#reason unknown - worked in previous versions

#Configuration for SRC-200A_3 transmitter:
include "/usr/share/lirc/extras/transmitters/mts/lircd.conf.mts"

#Configuration for the Hauppauge TV card remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

```

A quick ls /dev/lirc* shows
```

/dev/lirc0  /dev/lirc1  /dev/lircd  /dev/lircd1
```

*Update October 29,2009*
I posted this issue to the lirc email list.  Jeremy Yoder confirmed there was an issue in his /etc/init.d/lirc script and with testing on my side he created a patch.
Quoting his post on the lirc email list [http://sourceforge.net/mailarchive/forum.php?thread_name=4AEA5262.60006%40umich.edu&forum_name=lirc-list]("http://sourceforge.net/mailarchive/forum.php?thread_name=4AEA5262.60006%40umich.edu&forum_name=lirc-list")

"Just to update, the bug was mine in the /etc/init.d/lirc script (as I
suspected). It turns out I'm linking both /dev/lircd and /dev/lircd1 to
/var/run/lirc/lircd. Doh.

I should have a patch ready for Ubuntu in a day or two.

Jeremy"

So in case someone else is having trouble with this you should see a fix come down the line soon :D

---

### Post by dutcher on 2009-11-21
I applied Jeremy Yoder's patch to the /etc/init.d/lirc linked to here:
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/475664](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/475664)  
and it solved the problem. 
wget [http://launchpadlibrarian.net/35182403/lirc.patch.gz](http://launchpadlibrarian.net/35182403/lirc.patch.gz)
gunzip lirc.patch.gz
patch -p1 <lirc.patch

It asked for the file to patch, and I entered /etc/init.d/lirc.
I restarted lirc and imy IR Blaster is now changing channels!

---

### Post by plizzba on 2009-12-02
I also had the problem that my lirc blaster wouldn't work, but my remote was working fine. It was due to the bug in the init script as mentioned above.

I was hitting my head against a wall for hours because of this bug. So, here is a hint to people trying to detect it. When I looked at /dev, I saw:

```
$ ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2009-12-02 22:08 /dev/lirc0
crw-rw---- 1 root root 61, 1 2009-12-02 22:09 /dev/lirc1
lrwxrwxrwx 1 root root    19 2009-12-02 22:09 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root    20 2009-12-02 22:09 /dev/lircd1 -> /var/run/lirc/lircd
```Note the two lircd files point to the same place. That's wrong. After fixing it, /dev/lircd1 should point to /var/run/lirc/lircd1.

Presumably, if you see something like the above, Jeremy Yoder's patch should fix it. Thanks dutcher!

---

### Post by elp99jcm on 2009-12-08
Well after many hours trying to resolve this issue I finally figured out the bug in the /etc/init.d/lirc script. I went on the forums to post my solution, only to find a patch has already been posted!

Oh well, good practice I suppose.

It's a very simple change to the lirc script, change line 158 to the following:

rm -f ${OLD_SOCKET}1 && ln -s ${TRANSMITTER_SOCKET}1 ${OLD_SOCKET}1

So for the record, I now have a remote (Hauppauge PVR-150) and home brew serial transmitter working fine.

---

