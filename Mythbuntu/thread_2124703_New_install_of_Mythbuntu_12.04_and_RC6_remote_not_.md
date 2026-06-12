---
title: "New install of Mythbuntu 12.04 and RC6 remote not working with commandir"
date: 2013-03-11
forum: Mythbuntu
---

### Post by num1bryanp on 2013-03-11
Hello all,

I have a CommandIR III on a Mythbuntu 12.04 64 bit system using a RC6 remote. After upgrade to 12.04 I it stopped working... So I reinstall Mythbuntu 12.04 64 bit with no change, the RC6 remote is seen by the mini III but thats where it all stops. :-(
I have downloaded your two conf files hardware.conf and lircd.conf from comandir.com to get lirc to working, and it starts okay now.

Still all that happens is when I press buttons on the remote is the CommandIR shows a blinking red led on the top of the mini III.

If I start irw it gives no output when the remote is pressed.

System info to look at.

bryan@bryan-System-Product-Name:~$ lsb_release -irc
Distributor ID:	Ubuntu
Release:	12.04
Codename:	precise

bryan@bryan-System-Product-Name:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 003: ID 10c4:0003 Cygnal Integrated Products, Inc. CommandIR
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0461:4d0f Primax Electronics, Ltd 
Bus 002 Device 005: ID 0461:4d8a Primax Electronics, Ltd 

 
bryan@bryan-System-Product-Name:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
 
Pressing keys on the remote.
bryan@bryan-System-Product-Name:~$ irw
^C
     Giving up

bryan@bryan-System-Product-Name:~$ grep lirc /var/log/syslog
Mar 11 16:34:04 bryan-System-Product-Name lircd-0.9.0[5443]: accepted new client on /var/run/lirc/lircd
Mar 11 16:34:13 bryan-System-Product-Name lircd-0.9.0[5443]: removed client
Mar 11 16:34:13 bryan-System-Product-Name lircd-0.9.0[5443]: LIRC_deinit but keeping warm



# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="/etc/lirc/lircd.conf"

#Chosen IR Transmitter
TRANSMITTER="Command IR : Motorola Cable box"
# TRANSMITTER_MODULES="lirc_dev lirc_cmdir"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""
#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support.
#DISABLE_KERNEL_SUPPORT="true"

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
#transmitter.

include "/usr/share/lirc/extras/transmitters/directtv/general.conf"
# one space
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

# Configuration for the Command IR : Motorola Cable box transmitter:
include "/usr/share/lirc/extras/transmitters/motorola/dctxxxx.conf"
~       
       

bryan@bryan-System-Product-Name:/dev$ ls
alarm            loop5               rfkill    tty18  tty51      ttyS26
ashmem           loop6               rtc       tty19  tty52      ttyS27
autofs           loop7               rtc0      tty2   tty53      ttyS28
binder           loop-control        sda       tty20  tty54      ttyS29
block            mapper              sda1      tty21  tty55      ttyS3
bsg              mcelog              sda2      tty22  tty56      ttyS30
btrfs-control    mei                 sda5      tty23  tty57      ttyS31
bus              mem                 sdb       tty24  tty58      ttyS4
cdrom            net                 sdb1      tty25  tty59      ttyS5
cdrw             network_latency     sdb2      tty26  tty6       ttyS6
char             network_throughput  sdc       tty27  tty60      ttyS7
console          null                sdc1      tty28  tty61      ttyS8
core             nvidia0             sdd       tty29  tty62      ttyS9
cpu              nvidiactl           sdd1      tty3   tty63      uinput
cpu_dma_latency  oldmem              sg0       tty30  tty7       urandom
disk             port                sg1       tty31  tty8       vcs
dvd              ppp                 sg2       tty32  tty9       vcs1
dvdrw            psaux               sg3       tty33  ttyprintk  vcs2
ecryptfs         ptmx                sg4       tty34  ttyS0      vcs3
fb0              pts                 shm       tty35  ttyS1      vcs4
fd               ram0                snapshot  tty36  ttyS10     vcs5
full             ram1                snd       tty37  ttyS11     vcs6
fuse             ram10               sr0       tty38  ttyS12     vcsa
fw0              ram11               stderr    tty39  ttyS13     vcsa1
hidraw0          ram12               stdin     tty4   ttyS14     vcsa2
hidraw1          ram13               stdout    tty40  ttyS15     vcsa3
hidraw2          ram14               tty       tty41  ttyS16     vcsa4
hpet             ram15               tty0      tty42  ttyS17     vcsa5
input            ram2                tty1      tty43  ttyS18     vcsa6
kmsg             ram3                tty10     tty44  ttyS19     vga_arbiter
lircd            ram4                tty11     tty45  ttyS2      vhost-net
log              ram5                tty12     tty46  ttyS20     zero
loop0            ram6                tty13     tty47  ttyS21
loop1            ram7                tty14     tty48  ttyS22
loop2            ram8                tty15     tty49  ttyS23
loop3            ram9                tty16     tty5   ttyS24
loop4            random              tty17     tty50  ttyS25


Help,
Bryan

---

