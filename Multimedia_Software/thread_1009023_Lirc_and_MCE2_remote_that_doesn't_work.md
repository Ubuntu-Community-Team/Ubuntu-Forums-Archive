---
title: "Lirc and MCE2 remote that doesn't work"
date: 2008-12-12
forum: Multimedia Software
---

### Post by MauroKTM on 2008-12-12
Hallo guys,
I tried to install a remote on my Ubuntu intrepid with lirc

This is a Vista MCE (new version) remote that LIRC should support.

The machine install the hardware and a /dev/lirc0 device is created.

But it works only for the "first" command from remote. 
If I type irw it give me only the first key on the remote than... nothing! Until I discontect the device and i reconnect it.
```

mauro@mauro-XPS:~$ irw
000000037ff07bdd 00 OK mceusb


```

This is my hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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

```

```

mauro@mauro-XPS:~$ dmesg|grep lirc
[   34.344452] lirc_dev: IR Remote Control driver registered, major 61 
[   34.354111] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   34.354115] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   34.358795] usbcore: registered new interface driver lirc_mceusb2
[  200.568896] lirc_dev: lirc_register_plugin: sample_rate: 0
[  200.573100] lirc_mceusb2[6]: Formosa21 SnowflakeEmulation on usb7:6
```

the red one is the usb IR receiver
```

lsusb
Bus 007 Device 005: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 007 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0af0:7211 Option 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 004 Device 008: ID 147a:e017 Formosa Industrial Computing, Inc.[/COLOR] 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 005: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


please help!!!!!!!

thnx

---

### Post by laceration on 2008-12-12
I can't really say I understand what's going on, but I have some hunches...you might try my suggestions if no other solution comes along.

The lirc_mceusb2.c driver file has had numerous updates since the .083pre version of lirc that is in the software repositories.  It could very well be that a more current version could handle your remote.  That was the case for me.
 
Download the lirc-module-source package.
get the latest lirc_mceusb2.c from cvs. I would also get lirc_dev.
Replace the older driver files with the ones you got from cvs
Build your drivers with dkms
 
This post has more detailed instructions:
[http://ubuntuforums.org/showthread.php?p=5126843#post5126843](http://ubuntuforums.org/showthread.php?p=5126843#post5126843)

---

### Post by MauroKTM on 2008-12-15
Build your drivers with dkms...

how?


Thnx

---

### Post by laceration on 2008-12-15
What I'm saying is that maybe there is something in the driver code that can't handle the signal from your remote and its crashing it.  This is just a guess though.

What I do know is the drivers in the standard repositories are old old old!  If that is the problem there is a good chance it could have been fixed because the driver files are revised all the time.  Ubuntu seemingly does not update them at all.  It could be worth a shot for you even though its a little bit of work.

I just posted in another thread where I went into some detail on how to update your lirc drivers, here is the link:
[http://ubuntuforums.org/showpost.php?p=6373995&postcount=6](http://ubuntuforums.org/showpost.php?p=6373995&postcount=6)

That guy had a different setup that you though the newest driver file for you is at: [http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_mceusb2/lirc_mceusb2.c?revision=1.54&view=markup](http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_mceusb2/lirc_mceusb2.c?revision=1.54&view=markup)

You should update lirc_dev driver as in that post too.

---

