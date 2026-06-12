---
title: "[SOLVED] quickcam permission problem"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by jakommo on 2008-02-17
Hi,

I have a Quickcam Express installed using qc-usb-source and qc-usb-utils
the cam is working but the problem is that /dev/video0 belongs to root:root and I want it to have root:users or something like that. I've checked udev rules but there is nothing about it.
so the question is which program is making the device and setting the permissions?
or do I have to write my own udev rule for the cam?

any help appreciated

regards

jakommo

---

### Post by sisco311 on 2008-02-17
please post the output of
```
cat  /etc/udev/rules.d/40-permissions.rules
```

---

### Post by jakommo on 2008-02-18
Hi sisco311,

here ist the output. I did some changes on the GROUP because I need them to work for all users of the group "users".

```

root@point71:/etc/udev/rules.d# cat 40-permissions.rules
# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# Block devices
SUBSYSTEM!="block", GOTO="block_end"
ATTRS{removable}!="1",                  GROUP="disk"
ATTRS{removable}=="1",                  GROUP="floppy"
SUBSYSTEMS=="usb",                      GROUP="users"
SUBSYSTEMS=="ieee1394",                 GROUP="users"
SUBSYSTEMS=="mmc",                      GROUP="users"
SUBSYSTEMS=="pcmcia",                   GROUP="users"
LABEL="block_end"

# IDE devices
ENV{ID_CDROM}=="?*",                    GROUP="cdrom"
KERNEL=="ht[0-9]*",                     GROUP="tape"
KERNEL=="nht[0-9]*",                    GROUP="tape"

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your users camera,
# but it's not going to be group "users", okay?
KERNEL=="raw1394",                      GROUP="disk"
KERNEL=="dv1394*",                      GROUP="users"
KERNEL=="users1394*",                   GROUP="users"

# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",                      MODE="0644"
KERNEL=="pktcdvd[0-9]*",                GROUP="cdrom"

# Printers and Parallel devices
SUBSYSTEM=="printer",                   GROUP="lp"
SUBSYSTEM=="ppdev",                     GROUP="lp"
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",   GROUP="lp"
KERNEL=="pt[0-9]*",                     GROUP="tape"
KERNEL=="pht[0-9]*",                    GROUP="tape"

# SCSI devices
SUBSYSTEMS=="scsi", GOTO="scsi_start"
GOTO="scsi_end"
LABEL="scsi_start"
ATTRS{type}=="1",                       GROUP="tape"
ATTRS{type}=="5",                       GROUP="cdrom"
ATTRS{type}=="6",                       GROUP="scanner"
ATTRS{type}=="8",                       GROUP="tape"
ATTRS{type}=="3", ATTRS{vendor}=="HP",  GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="Epson", GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", GROUP="scanner"
LABEL="scsi_end"

# Serial devices
SUBSYSTEM=="tty",                       GROUP="dialout"
SUBSYSTEM=="capi",                      GROUP="dialout"
SUBSYSTEM=="slamr",                     GROUP="dialout"
SUBSYSTEM=="zaptel",                    GROUP="dialout"
KERNEL=="ttyLTM[0-9]*",                 GROUP="dialout", MODE="0660"

# Sound devices
SUBSYSTEM=="sound",                     GROUP="users"

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",                      GROUP="root", MODE="0600"
KERNEL=="ptmx",                         GROUP="root", MODE="0666"
KERNEL=="pty*",                         GROUP="tty", MODE="0666"
KERNEL=="tty",                          GROUP="root", MODE="0666"
KERNEL=="tty[0-9]*",                    GROUP="root"
KERNEL=="vcs*",                         GROUP="root"
LABEL="vc_end"

# Video devices
SUBSYSTEM=="drm",                       GROUP="users"
SUBSYSTEM=="dvb",                       GROUP="users"
SUBSYSTEM=="graphics",                  GROUP="users"
SUBSYSTEM=="users4linux",               GROUP="users"
KERNEL=="agpgart",                      GROUP="users"
KERNEL=="nvidia*",                      GROUP="users"

# Other devices, by name
KERNEL=="null",                         MODE="0666"
KERNEL=="zero",                         MODE="0666"
KERNEL=="full",                         MODE="0666"
KERNEL=="random",                       MODE="0666"
KERNEL=="urandom",                      MODE="0666"
KERNEL=="mem",                          GROUP="kmem", MODE="0640"
KERNEL=="kmem",                         GROUP="kmem", MODE="0640"
KERNEL=="port",                         GROUP="kmem", MODE="0640"
KERNEL=="nvram",                        GROUP="nvram"
KERNEL=="rtc",                          GROUP="users"
KERNEL=="inotify",                      MODE="0666"
KERNEL=="js[0-9]*",                     GROUP="users"
root@point71:/etc/udev/rules.d# 

```

regards jakommo

---

### Post by sisco311 on 2008-02-18
ok. edit two lines:

```
 root@point71:/etc/udev/rules.d# cat 40-permissions.rules
# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# Block devices
SUBSYSTEM!="block", GOTO="block_end"
ATTRS{removable}!="1",                  GROUP="disk"
ATTRS{removable}=="1",                  GROUP="floppy"
SUBSYSTEMS=="usb",                      GROUP="users"
SUBSYSTEMS=="ieee1394",                 GROUP="users"
SUBSYSTEMS=="mmc",                      GROUP="users"
SUBSYSTEMS=="pcmcia",                   GROUP="users"
LABEL="block_end"

# IDE devices
ENV{ID_CDROM}=="?*",                    GROUP="cdrom"
KERNEL=="ht[0-9]*",                     GROUP="tape"
KERNEL=="nht[0-9]*",                    GROUP="tape"

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your users camera,
# but it's not going to be group "users", okay?
KERNEL=="raw1394",                      GROUP="disk"
KERNEL=="dv1394*",                      GROUP="users"
[B] KERNEL=="video1394*",                   GROUP="users"
[/B] 
# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",                      MODE="0644"
KERNEL=="pktcdvd[0-9]*",                GROUP="cdrom"

# Printers and Parallel devices
SUBSYSTEM=="printer",                   GROUP="lp"
SUBSYSTEM=="ppdev",                     GROUP="lp"
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",   GROUP="lp"
KERNEL=="pt[0-9]*",                     GROUP="tape"
KERNEL=="pht[0-9]*",                    GROUP="tape"

# SCSI devices
SUBSYSTEMS=="scsi", GOTO="scsi_start"
GOTO="scsi_end"
LABEL="scsi_start"
ATTRS{type}=="1",                       GROUP="tape"
ATTRS{type}=="5",                       GROUP="cdrom"
ATTRS{type}=="6",                       GROUP="scanner"
ATTRS{type}=="8",                       GROUP="tape"
ATTRS{type}=="3", ATTRS{vendor}=="HP",  GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="Epson", GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", GROUP="scanner"
LABEL="scsi_end"

# Serial devices
SUBSYSTEM=="tty",                       GROUP="dialout"
SUBSYSTEM=="capi",                      GROUP="dialout"
SUBSYSTEM=="slamr",                     GROUP="dialout"
SUBSYSTEM=="zaptel",                    GROUP="dialout"
KERNEL=="ttyLTM[0-9]*",                 GROUP="dialout", MODE="0660"

# Sound devices
SUBSYSTEM=="sound",                     GROUP="users"

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",                      GROUP="root", MODE="0600"
KERNEL=="ptmx",                         GROUP="root", MODE="0666"
KERNEL=="pty*",                         GROUP="tty", MODE="0666"
KERNEL=="tty",                          GROUP="root", MODE="0666"
KERNEL=="tty[0-9]*",                    GROUP="root"
KERNEL=="vcs*",                         GROUP="root"
LABEL="vc_end"

# Video devices
SUBSYSTEM=="drm",                       GROUP="users"
SUBSYSTEM=="dvb",                       GROUP="users"
SUBSYSTEM=="graphics",                  GROUP="users"
** SUBSYSTEM=="video4linux",               GROUP="users"**
KERNEL=="agpgart",                      GROUP="users"
KERNEL=="nvidia*",                      GROUP="users"

# Other devices, by name
KERNEL=="null",                         MODE="0666"
KERNEL=="zero",                         MODE="0666"
KERNEL=="full",                         MODE="0666"
KERNEL=="random",                       MODE="0666"
KERNEL=="urandom",                      MODE="0666"
KERNEL=="mem",                          GROUP="kmem", MODE="0640"
KERNEL=="kmem",                         GROUP="kmem", MODE="0640"
KERNEL=="port",                         GROUP="kmem", MODE="0640"
KERNEL=="nvram",                        GROUP="nvram"
KERNEL=="rtc",                          GROUP="users"
KERNEL=="inotify",                      MODE="0666"
KERNEL=="js[0-9]*",                     GROUP="users"
```

---

### Post by jakommo on 2008-02-18
thanks

I used :%s/video/users/g in vim to change every video to users, and didn't think about that there is the word video in a non GROUP="" field.

thanks again.

greez jakommo

---

### Post by jakommo on 2008-02-18
Hmm ok added Solved to quick.

I applied the changes and rebooted but its still /dev/video0 root:root.

any other suggestions? or is there a way to see what udev is doing like a log file?

---

### Post by sisco311 on 2008-02-18
the log file is /var/log/udev (post it)

---

### Post by jakommo on 2008-02-19
Hi sisco311,

I attached it because its to long to post and had to tar it because of the filesize limit for txt files.
I had a look at the file but couldn't find anything about video0.

thanks for your help.

jakommo

---

### Post by jakommo on 2008-02-19
Ok I have another idea, the problem apears on a diskless system, and I only made the changes to the etc ramdisk, and not on the server.
I think bacause udev starts before the etc ramdisk is mounted, it didnt work last time. now I've changed it back, also in the udev rules on the server and I should work.
It will be the first thing I do tomorrow when I'm at work.

---

### Post by sisco311 on 2008-02-19
Hi  jakommo,

Good luck and [SIZE=-1]let me know if you have  more questions.

sisco311
[/SIZE]

---

### Post by jakommo on 2008-02-20
ok I've tested it right now and its working great.

Thanks for your help again.

greez

jakommo

---

