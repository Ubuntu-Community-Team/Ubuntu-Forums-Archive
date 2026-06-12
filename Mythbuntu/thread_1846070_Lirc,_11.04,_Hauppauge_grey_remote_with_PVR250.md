---
title: "Lirc, 11.04, Hauppauge grey remote with PVR250"
date: 2011-09-18
forum: Mythbuntu
---

### Post by ozite on 2011-09-18
I recently upgraded to 11.04 and this broke LIRC and remote for MythTV.  The remote is the grey Hauppauge and I'm using the IR receiver connected to PVR-250 model 890. On trying to solve a mouse related problem, I included pre-released updates for natty.  This appeared to break lirc for me. Here are the things I have tried.

Followed some directions from MythTV.org - [Ubuntu lirc install]("http://www.mythtv.org/wiki/Ubuntu_lirc_install").

```
htpc@htpc-EP35-DS3L:~$ uname -r
2.6.38-11-generic

```

```
htpc@htpc-EP35-DS3L:~$ sudo apt-get install lirc lirc-modules-source module-assistant[sudo] password for htpc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
module-assistant is already the newest version.
lirc-modules-source is already the newest version.
lirc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The following completes successfully
```
htpc@htpc-EP35-DS3L:~$ sudo dpkg-reconfigure lirc-modules-source 

```


sudo nano /etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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


```

Lirc appears to be running.
```
htpc@htpc-EP35-DS3L:~$ ls -al /dev/lirc*
crw------- 1 root root 250, 0 2011-09-18 09:55 /dev/lirc0
lrwxrwxrwx 1 root root     19 2011-09-18 09:55 /dev/lircd -> /var/run/lirc/lircd

```

IRW doesn't show and keypresses.

dmesg suggests:
```
htpc@htpc-EP35-DS3L:~$ dmesg |grep -i lirc
[   32.806775] lirc_dev: IR Remote Control driver registered, major 250 
[   32.807589] IR LIRC bridge handler initialized
[   33.070323] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0

```

In previous version, I was able to get the following modprobe to work.
```
htpc@htpc-EP35-DS3L:~$ sudo modprobe lirc_i2c
FATAL: Module lirc_i2c not found.
```

After the update, the following is at the end of /var/log/syslog.
```
Sep 18 10:04:27 htpc-EP35-DS3L lircd-0.8.7[836]: accepted new client on /var/run/lirc/lircd
Sep 18 10:04:27 htpc-EP35-DS3L lircd-0.8.7[836]: could not get file information for /dev/lirc/0
Sep 18 10:04:27 htpc-EP35-DS3L lircd-0.8.7[836]: default_init(): No such file or directory
Sep 18 10:04:27 htpc-EP35-DS3L lircd-0.8.7[836]: Failed to initialize hardware
Sep 18 10:04:30 htpc-EP35-DS3L lircd-0.8.7[836]: removed client
Sep 18 10:09:01 htpc-EP35-DS3L CRON[2760]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/li$
Sep 18 10:13:39 htpc-EP35-DS3L lircd-0.8.7[836]: accepted new client on /var/run/lirc/lircd
Sep 18 10:13:39 htpc-EP35-DS3L lircd-0.8.7[836]: could not get file information for /dev/lirc/0
Sep 18 10:13:39 htpc-EP35-DS3L lircd-0.8.7[836]: default_init(): No such file or directory
Sep 18 10:13:39 htpc-EP35-DS3L lircd-0.8.7[836]: Failed to initialize hardware
Sep 18 10:13:43 htpc-EP35-DS3L lircd-0.8.7[836]: removed client
Sep 18 10:17:01 htpc-EP35-DS3L CRON[2791]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 18 10:17:03 htpc-EP35-DS3L CRON[2790]: (CRON) error (grandchild #2791 failed with exit status 1)
Sep 18 10:17:03 htpc-EP35-DS3L CRON[2790]: (CRON) info (No MTA installed, discarding output)

```


I can try to restart lirc.
```
htpc@htpc-EP35-DS3L:/var/log$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                         [ OK ] 
 * Loading LIRC modules                                                                            [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

Results in:
```
htpc@htpc-EP35-DS3L:~$ irw
connect: Connection refused
```

I tried changing a line in /etc/lirc/hardware.conf

```
REMOTE_DEVICE="/dev/lirc0"

```

Tried to restart lirc, with fail result.

```
htpc@htpc-EP35-DS3L:/var/log$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                         [fail] 
 * Loading LIRC modules                                                                            [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

Changed back
```
REMOTE_DEVICE="/dev/lirc/0"

```

Restarted.

```
htpc@htpc-EP35-DS3L:~$ sudo dpkg-reconfigure lirc
 * Stopping remote control daemon(s): LIRC                               [fail] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

Any suggestions?  Do I need to remove old drivers and build lirc modules?

```
sudo m-a update,prepare

Updated infos about 40 packages
Getting source for kernel version: 2.6.38-11-generic
Kernel headers available in /usr/src/linux-headers-2.6.38-11-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
```

 Build of the package lirc-modules-source failed! How do you wish to proceed?

Build log starting, file:                                                   
/var/cache/modass/lirc-modules-source.buildlog.2.6.38-11-generic.131635900

I tried using the Mythbuntu Control Center to set up remote.  I restarted the PC, enabled remote control and selected Hauppauge TV Card.  irw now gives "connect: No such file or directory"

---

### Post by ozite on 2011-10-08
```
uname -r
2.6.38-12-generic
```

Based on the information [here]("http://www.gossamer-threads.com/lists/mythtv/users/476205#476205"), I tried the following:

```
 modprobe ir-kbd-i2c hauppauge=1
```

which gave the following with :
```

dmesg |tail -n 4
[  145.900032] Registered IR keymap rc-rc5-tv
[  145.900125] input: i2c IR (Hauppauge) as /devices/virtual/rc/rc1/input5
[  145.900199] rc1: i2c IR (Hauppauge) as /devices/virtual/rc/rc1
[  145.900202] ir-kbd-i2c: i2c IR (Hauppauge) detected at i2c-1/1-0018/ir0 [ivtv i2c driver #0]


```

It would read the numbers, but no other keys.

I installed input-utils, running:

```

sudo lsinput

/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0x425
   product : 0xf102
   version : 256
   name    : "G-Tech CHINA U+P Wireless Mouse "
   phys    : "usb-0000:00:1a.2-1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_MSC

/dev/input/event4
   bustype : BUS_PCI
   vendor  : 0x7063
   product : 0x5500
   version : 1
   name    : "cx88 IR (pcHDTV HD5500 HDTV)"
   phys    : "pci-0000:05:01.0/ir0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_REP

/dev/input/event5
   bustype : BUS_I2C
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "i2c IR (Hauppauge)"
   phys    : "i2c-1/1-0018/ir0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_REP

```

Looks okay so far:
```
tail -n 10 /proc/bus/input/devices 
N: Name="i2c IR (Hauppauge)"
P: Phys=i2c-1/1-0018/ir0
S: Sysfs=/devices/virtual/rc/rc1/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=100013
B: KEY=c0010 201080400000000 0 30200a000 18000004801 9e000000000000 ffc
B: MSC=10

```

```
ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
	Driver cx88xx, table rc-rc5-hauppauge-new
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>
Found /sys/class/rc/rc1/ (/dev/input/event5) with:
	Driver ir-kbd-i2c, table rc-rc5-tv
	Supported protocols: RC-5 
	Enabled protocols: 
	Extra capabilities: <access denied>

```

and

```
dmesg | grep i2c
[    0.533073] i2c-core: driver [adp5520] using legacy suspend method
[    0.533074] i2c-core: driver [adp5520] using legacy resume method
[   32.659713] i2c-core: driver [tuner] using legacy suspend method
[   32.659716] i2c-core: driver [tuner] using legacy resume method
[   32.841622] saa7115 1-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   32.974217] i2c-core: driver [msp3400] using legacy suspend method
[   32.974219] i2c-core: driver [msp3400] using legacy resume method
[   32.988111] msp3400 1-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #0)
[   33.005019] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[  145.900125] input: i2c IR (Hauppauge) as /devices/virtual/rc/rc1/input5
[  145.900199] rc1: i2c IR (Hauppauge) as /devices/virtual/rc/rc1
[  145.900202] ir-kbd-i2c: i2c IR (Hauppauge) detected at i2c-1/1-0018/ir0 [ivtv i2c driver #0]

```


I made a hauppauge.conf file.
```
0x003d = KEY_F2 # Power button
0x003b = KEY_F10 # Go button: /ulb/play_mp3.sh
0x0001 = KEY_1 # 1 button
0x0002 = KEY_2 # 2 button
0x0003 = KEY_3 # 3 button
0x0004 = KEY_4 # 4 button
0x0005 = KEY_5 # 5 button
0x0006 = KEY_6 # 6 button
0x0007 = KEY_7 # 7 button
0x0008 = KEY_8 # 8 button
0x0009 = KEY_9 # 9 button
0x001f = KEY_ESC # Back/Exit button
0x0000 = KEY_0 # 0 button
0x000d = KEY_M # Menu button
0x0010 = KEY_RIGHT # Right arrow button
0x0011 = KEY_LEFT # Left arrow button
0x0020 = KEY_UP # Up arrow button
0x0021 = KEY_DOWN # Down arrow button
0x0025 = KEY_ENTER # OK button
0x000b = KEY_D # RED button
0x002e = KEY_G # GREEN button (signal monitor)
0x0038 = KEY_P # YELLOW button (Pause; was F10: volume down)
0x0029 = KEY_B # BLUE button (adjust audio sync)
0x000f = KEY_F9 # Mute button
0x000c = KEY_F9 # blank (no label) button: Mute or DVD menu
0x003c = KEY_W # Full button
0x0032 = KEY_COMMA # << button
0x0035 = KEY_F # Play button
0x0034 = KEY_DOT # >> button
0x0037 = KEY_R # Record button
0x0036 = KEY_Y # Stop button
0x0030 = KEY_P # Pause button
0x0024 = KEY_HOME # |< button (was KEY_Q)
0x001e = KEY_END # >| button (was KEY_Z)
0x000a = KEY_TEXT
0x000e = KEY_SUBTITLE
0x0012 = KEY_PREVIOUS
0x0014 = KEY_UP
0x0015 = KEY_DOWN
0x0016 = KEY_LEFT
0x0017 = KEY_RIGHT
0x0018 = KEY_VIDEO
0x0019 = KEY_AUDIO
0x0026 = KEY_SLEEP
0x0022 = KEY_CHANNEL
0x001a = KEY_MHP
0x001b = KEY_EPG
0x001c = KEY_TV 
```

```
sudo input-kbd -f hauppauge.conf 5
```

which returned:
```
/dev/input/event5
map: 33 keys, size: 33/64
scancode 61 out of range (0-33)

```

Didn't work.

I tried:
```
sudo input-kbd -f hauppauge.conf 4
/dev/input/event4
map: 84 keys, size: 84/128
set: 0x003d =  60  # KEY_F2
set: 0x003b =  68  # KEY_F10
set: 0x0001 =   2  # KEY_1
set: 0x0002 =   3  # KEY_2
set: 0x0003 =   4  # KEY_3
set: 0x0004 =   5  # KEY_4
set: 0x0005 =   6  # KEY_5
set: 0x0006 =   7  # KEY_6
set: 0x0007 =   8  # KEY_7
set: 0x0008 =   9  # KEY_8
set: 0x0009 =  10  # KEY_9
set: 0x001f =   1  # KEY_ESC
set: 0x0000 =  11  # KEY_0
set: 0x000d =  50  # KEY_M
set: 0x0010 = 106  # KEY_RIGHT
set: 0x0011 = 105  # KEY_LEFT
set: 0x0020 = 103  # KEY_UP
set: 0x0021 = 108  # KEY_DOWN
set: 0x0025 =  28  # KEY_ENTER
set: 0x000b =  32  # KEY_D
set: 0x002e =  34  # KEY_G
set: 0x0038 =  25  # KEY_P
set: 0x0029 =  48  # KEY_B
set: 0x000f =  67  # KEY_F9
set: 0x000c =  67  # KEY_F9
set: 0x003c =  17  # KEY_W
set: 0x0032 =  51  # KEY_COMMA
set: 0x0035 =  33  # KEY_F
set: 0x0034 =  52  # KEY_DOT
set: 0x0037 =  19  # KEY_R
set: 0x0036 =  21  # KEY_Y
set: 0x0030 =  25  # KEY_P
set: 0x0024 = 102  # KEY_HOME
set: 0x001e = 107  # KEY_END
set: 0x000a = 388  # KEY_TEXT
set: 0x000e = 370  # KEY_SUBTITLE
set: 0x0012 = 412  # KEY_PREVIOUS
set: 0x0014 = 103  # KEY_UP
set: 0x0015 = 108  # KEY_DOWN
set: 0x0016 = 105  # KEY_LEFT
set: 0x0017 = 106  # KEY_RIGHT
set: 0x0018 = 393  # KEY_VIDEO
set: 0x0019 = 392  # KEY_AUDIO
set: 0x0026 = 142  # KEY_SLEEP
set: 0x0022 = 363  # KEY_CHANNEL
set: 0x001a = 367  # KEY_MHP
set: 0x001b = 365  # KEY_EPG
set: 0x001c = 377  # KEY_TV

```

I tried changing the /etc/lirc/hardware.conf  according to the following [link]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/454371").

The top portion of the hardware.conf contents:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
#REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_MODULES="ir_kbd_i2c"
#REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="dev/input"
#REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/event4"
#REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""


```



I tried restarting lirc, 

```
sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                                            [ OK ] 
 * Loading LIRC modules                                                                                               [ OK ] 
 * Starting remote control daemon(s) : LIRC                                                                           [ OK ] 


```


irw still only shows numbers as the accepted input, volume control works .

mythfrontend:

```
2011-10-08 12:48:08.578 LIRC: Successfully initialized '/dev/lircd' using '/home/htpc/.mythtv/lircrc' config

```


I tried adding a line to the /etc/rc_maps.cfg, as suggested [here]("https://bbs.archlinux.org/viewtopic.php?pid=918927").  

Based on the above, I added the following to the bottom of the /etc/rc_maps.cfg file:

```
*    rc-rc5-hauppauge-new     haupp

```

I tried:
```
cp /usr/share/lirc/remotes/devinput/lircd.conf.devinput /etc/lirc/lircd.conf
```

I tried the following [here]("http://www.mythtv.org/wiki/LIRC#Debian_Wheezy_amd64_Hauppauge_PVR_350"):

```
sudo cp /lib/udev/rc_keymaps/haupp /etc/rc_keymaps/

```

renamed to haupp250, edited /etc/rc_maps.cfg and put the following on the last line.

```
*    rc-rc5-tv     haupp250
```

Replaced text in /ect/rc_keymaps/ with values below.  

```
# table haupp, type: UNKNOWN
0x003d = KEY_F2 # Power button
0x003b = KEY_F10 # Go button: /ulb/play_mp3.sh
0x0001 = KEY_1 # 1 button
0x0002 = KEY_2 # 2 button
0x0003 = KEY_3 # 3 button
0x0004 = KEY_4 # 4 button
0x0005 = KEY_5 # 5 button
0x0006 = KEY_6 # 6 button
0x0007 = KEY_7 # 7 button
0x0008 = KEY_8 # 8 button
0x0009 = KEY_9 # 9 button
0x001f = KEY_ESC # Back/Exit button
0x0000 = KEY_0 # 0 button
0x000d = KEY_M # Menu button
0x0010 = KEY_RIGHT # Right arrow button
0x0011 = KEY_LEFT # Left arrow button
0x0020 = KEY_UP # Up arrow button
0x0021 = KEY_DOWN # Down arrow button
0x0025 = KEY_ENTER # OK button
0x000b = KEY_D # RED button
0x002e = KEY_G # GREEN button (signal monitor)
0x0038 = KEY_P # YELLOW button (Pause; was F10: volume down)
0x0029 = KEY_B # BLUE button (adjust audio sync)
0x000f = KEY_F9 # Mute button
0x000c = KEY_F9 # blank (no label) button: Mute or DVD menu
0x003c = KEY_W # Full button
0x0032 = KEY_COMMA # << button
0x0035 = KEY_F # Play button
0x0034 = KEY_DOT # >> button
0x0037 = KEY_R # Record button
0x0036 = KEY_Y # Stop button
0x0030 = KEY_P # Pause button
0x0024 = KEY_HOME # |< button (was KEY_Q)
0x001e = KEY_END # >| button (was KEY_Z)
0x000a = KEY_TEXT
0x000e = KEY_SUBTITLE
0x0012 = KEY_PREVIOUS
0x0014 = KEY_UP
0x0015 = KEY_DOWN
0x0016 = KEY_LEFT
0x0017 = KEY_RIGHT
0x0018 = KEY_VIDEO
0x0019 = KEY_AUDIO
0x0026 = KEY_SLEEP
0x0022 = KEY_CHANNEL
0x001a = KEY_MHP
0x001b = KEY_EPG
0x001c = KEY_TV
```

The /etc/lirc/hardware.conf contains the following at the start of the file:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
#REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_MODULES="ir_kbd_i2c"
#REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="dev/input"
#REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/event4"
#REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#ML ADDED
# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="devinput"
# usually /dev/lirc0 is the correct setting for systems using udev
DEVICE="/dev/input/event5"
MODULES="ir-kbd-i2c"

```


This solved the problem upon a restart.  Hopefully the messy information above will help someone.

---

### Post by laci63 on 2011-12-31
Thanks, that was very helpful. Worked with my PVR350 too.

---

### Post by ozite on 2012-04-29
The remote was only partly working in MythTV upon upgrading to 12.04.  The arrow keys worked on the remote but not much else.  

A few simple steps corrected the problem. 

```
sudo lsinput
```

showed that the input even number for the "i2c IR (Hauppauge)" changed.  I edited the hardware.conf in /etc/lirc to match the new input number in two places.  In my case this changed from /event9 to /event18.  

My hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event18"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

DRIVER="devinput"
DEVICE="/dev/input/event18"
MODULES="ir-kbd-i2c"


#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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

```

I'm sure there is a more elegant solution to get ir-kbd-i2c to work, but I wasn't able to get it working for my system.

The grey Hauppauge remote now works in 12.04 as it did before in versions of Ubuntu all the way back to 6.06.

---

### Post by ozite on 2012-08-04
Using 3.2.0-29-generic and after some updates, the gray remote is no longer working. 
For the first two starts a crash "Sorry, Ubuntu 12.04 has experienced an internal error".  On first restart, the arrow keys worked in MythTV but the OK button did not. Also, irw showed strange characters and letters in brackets when pressed. The error was detected in 'ir-keytable'.  I added my /etc/rc_maps.cfg to the bug report. 

```

sudo lsinput

...cut

/dev/input/event15
   bustype : BUS_I2C
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "i2c IR (Hauppauge)"
   phys    : "i2c-0/0-0018/ir0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_REP

```

I edited the /etc/lirc/hardware.conf to have the following

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev"
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event15"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

DRIVER="devinput"
DEVICE="/dev/input/event15"
MODULES="ir-kbd-i2c"


#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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

```

No response in irw or mythtv or a terminal window.
```

ir-keytable

Found /sys/class/rc/rc0/ (/dev/input/event13) with:
	Driver cx88xx, table rc-hauppauge
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>
Found /sys/class/rc/rc1/ (/dev/input/event15) with:
	Driver ir-kbd-i2c, table rc-hauppauge
	Supported protocols: RC-5 
	Enabled protocols: 
	Extra capabilities: <access denied>
```

Does anyone have any suggestions on what to do to get the remote working again?

---

