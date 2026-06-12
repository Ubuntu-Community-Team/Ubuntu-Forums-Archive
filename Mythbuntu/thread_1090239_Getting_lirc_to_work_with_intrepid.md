---
title: "Getting lirc to work with intrepid"
date: 2009-03-08
forum: Mythbuntu
---

### Post by Lido on 2009-03-08
Does anyone know if lirc works with intrepid? It seems that lots of people are having similar trouble with it. I can't get it working and can't even figure out if the daemon is running because it seems to start ok, but if I run irw it seems to kill lirc.

```
$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC	[ OK ] 
 * Loading LIRC modules	[ OK ] 
 * Starting remote control daemon(s) : LIRC	[ OK ] 

$ sudo irw

$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC	[fail] 
 * Loading LIRC modules	[ OK ] 
 * Starting remote control daemon(s) : LIRC	[ OK ] 

```

This is one thing that I'd really like to get working on my system, but I've tried and never successfully got it working on any machine.

---

### Post by scary_jeff on 2009-03-08
What remote have you got?

---

### Post by azmyth on 2009-03-08
Can you post your /etc/lirc/hardware.conf file?

---

### Post by Lido on 2009-03-08
Well, I've got two receivers and two remotes. One receiver is the built in imon one that's in the Antec Fusion Remote case that I have. The other is an Anywhere MCE generic remote and USB receiver that I got from Newegg. I'm hoping to use the Anywhere remote and the imon built in receiver, but I'll use the external receiver if necessary. I'm pretty sure the imon receiver will accept codes from the MCE remote though. Here's the remote on Newegg:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001&Tpk=ha-ir01sv]("http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001&Tpk=ha-ir01sv")

Here's my hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="ABBAHOME"
RECEIVER_VENDOR="Linux Input Device"

```

---

### Post by azmyth on 2009-03-08
I assume you want both receivers to work so you'll need run two instances of lirc. I've never tried two receivers but I don't see why it wouldn't work. I believe you'll have to edit the hardware.conf to reflect two receivers like

REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
REMOTE_LIRCD_ARGS=""

REMOTE="name of remote in lircd.conf.anywhere"
REMOTE_MODULES="lirc_dev lirc_moduleforanywhere"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc1"
REMOTE_LIRCD_CONF="anywhere/lircd.conf.anywhere"
REMOTE_LIRCD_ARGS=""

then once you reboot, you can do a ps -A | grep lirc to see if you have two instances of lirc running.

---

### Post by Lido on 2009-03-08
Acutally, I don't need both receivers working. I just happen to have the MCE remote which I like better so I was hoping to use that with the Antec/IMON receiver.

---

### Post by azmyth on 2009-03-08
Okay, you won't need to add those additional lines in your hardware.conf. Make sure that the remote name in the imon/lircd.conf.imon-pad file matches this line REMOTE="Soundgraph iMON PAD IR/VFD". Restart lirc and do a ls -al /dev | grep lirc and make sure you have two entries.

---

### Post by Lido on 2009-03-09
I don't have an imon directory in /etc/lirc. I'm using MythTV installed on standard 8.10 64 bit ubuntu, not mythbuntu:```
$ ls -al /dev | grep lirc
srw-rw-rw-   1 root   root           0 2009-03-08 22:17 lircd

```

---

### Post by azmyth on 2009-03-09
Where is this file located imon/lircd.conf.imon-pad? What parent directory is it in?

imon/lircd.conf.imon-pad

---

### Post by rodercot on 2009-03-09
Can you give us an lsusb output please. you will likely see

 a number, device and description the normal are

 0036 or 0038 or ffdc. If you have the ffdc I think you are going to need to get the LCD and the ir functioning at the same time. 

 Do you have the VFD with buttons and know OR the LCD with the KNOB only. 

 The path you are looking for is

 /usr/share/lirc/remotes.

 If you want to use the MCE remote you will need another lircd files anyhow, and you cannot use the stock supplied MCE remote file and the remote bits are not the same. 

 here is a lircd file that works with the imon IR and MCE remote. You could save this in your /etc/lirc as a lircd.conf file after you rename the old one to .bak

 ```
#Configuration for MCE Remote using the Soundgraph iMON IR/LCD:
begin remote

  name         mceusb
  bits         32
  eps          30
  aeps        100

  one             0     0
  zero            0     0
  gap         203992
  toggle_bit_mask 0x8000

      begin codes
          Power                0x800F040C
          TV_power             0x800F0465
          Home                 0x800F040D
          Guide                0x800F0426
          LiveTV               0x800F0425
          DVD                  0x800F0424
          Teletext             0x800F045A
          RecordTV             0x800F0448
          Back                 0x800F0423
          Forward              0x800F0414
          Stop                 0x800F0419
          Replay               0x800F041B
          Skip                 0x800F041A
          Play                 0x800F0416
          Record               0x800F0417
          Rewind               0x800F0415
          Pause                0x800F0418
          More                 0x800F040F
          Left                 0x800F0420
          Right                0x800F0421
          Up                   0x800F041E
          Down                 0x800F041F
          OK                   0x800F0422
          Chan_Down            0x800F0413
          Chan_Up              0x800F0412
          Vol_Down             0x800F0411
          Vol_Up               0x800F0410
          Mute                 0x800F040E
          1                    0x800F0401
          2                    0x800F0402
          3                    0x800F0403
          4                    0x800F0404
          5                    0x800F0405
          6                    0x800F0406
          7                    0x800F0407
          8                    0x800F0408
          9                    0x800F0409
          Zero                 0x800F0400
          *                    0x800F041D
          Clear                0x800F040A
          #                    0x800F041C
          Enter                0x800F040B
          Red                  0x800F045B
          Green                0x800F045C
          Yellow               0x800F045D
          Blue                 0x800F045E
          Antec_knob_left      0x01000000
          Antec_knob_right     0x00010000
      end codes

end remote

```

 This is all hinges on which device you have from above. my hardware.conf remotes section is like so, but I also have the lcd working via lcdproc 0.5.2 and patched. 

 hardware.conf 

 ```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="custom"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="etc/lircd.conf"
REMOTE_LIRCD_ARGS=""

```

 Make sure you have the or any usb remote dongles unplugged while your setting up the first device.

 Dave

---

### Post by Lido on 2009-03-09
Thanks. Looks like I've got the 0038. I've got the Antec Fusion remote case so there are no buttons on the LCD, just the LCD (presumably with a receiver on it) and the big volume knob (which I don't really care about using). Here's lsusb:```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05d5:6781 Super Gate Technology Co., Ltd 
Bus 003 Device 002: ID 15c2:0038 SoundGraph Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I used your lircd.conf file and copied your hardware.conf too (see below), but I'm still getting this problem where irw doesn't do anything and seems to be killing lirc:
```
$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC		[ OK ] 
 * Loading LIRC modules					[ OK ] 
 * Starting remote control daemon(s) : LIRC		[ OK ] 

$ ls -al /dev | grep lirc
srw-rw-rw-   1 root   root           0 2009-03-09 20:56 lircd

/etc/lirc$ sudo irw

$ ls -al /dev | grep lirc
srw-rw-rw-   1 root   root           0 2009-03-09 20:56 lircd

/etc/lirc$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC		[fail] 
 * Loading LIRC modules					[ OK ] 
 * Starting remote control daemon(s) : LIRC		[ OK ]

$ ls -al /dev | grep lirc
srw-rw-rw-   1 root   root           0 2009-03-09 20:56 lircd

/etc/lirc$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC		[ OK ] 
 * Loading LIRC modules					[ OK ] 
 * Starting remote control daemon(s) : LIRC		[ OK ]

$ ls -al /dev | grep lirc
srw-rw-rw-   1 root   root           0 2009-03-09 20:56 lircd

$ sudo irrecord test.txt

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
```

Here's hardware.conf now:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="etc/lircd.conf"
#REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

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

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="ABBAHOME"
RECEIVER_VENDOR="Linux Input Device"

```

---

### Post by azmyth on 2009-03-10
You should be seeing a /dev/lirc0 when you do a ls -al /dev | grep lirc. As currently your lircd is linked to a non existent socket.

Try

#dmesg | grep lirc

to see if you're getting any errors and also

#lsmod | grep lirc to make sure your modules are being loaded as you should see lirc_dev and lirc_imon.

If you don't see any errors then try removing the modules and then reloading

#rmmod lirc_dev
#rmmod lirc_imon

Then reload to see if you get any errors.

modprobe lirc_dev
modprobe lirc_imon.

---

### Post by Lido on 2009-03-10
I don't see any errors.

```
$ dmesg | grep lirc
[   32.917970] lirc_dev: IR Remote Control driver registered, major 61 
[   32.929631] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   32.929643] lirc_imon: Venky Raju <dev@venky.ws>
[   32.929711] usbcore: registered new interface driver lirc_imon

```

Modules seem to be loaded too.

```
$ lsmod | grep lirc
lirc_imon              26252  0 
lirc_dev               22216  1 lirc_imon
usbcore               175888  5 lirc_imon,usbhid,ohci_hcd,ehci_hcd

```

I rmmod'ed them and reloaded them, but no change. Still can't get irw to do anything but seemingly kill lirc.

```
$ sudo rmmod lirc_imon
$ sudo rmmod lirc_dev
$ sudo modprobe lirc_dev
$ sudo modprobe lirc_imon

$ lsmod | grep lirc
lirc_imon              26252  0 
lirc_dev               22216  1 lirc_imon
usbcore               175888  5 lirc_imon,usbhid,ohci_hcd,ehci_hcd

```

---

### Post by azmyth on 2009-03-10
Can you post your lircd.conf.

For your irrecord test, you need to specify the socket irrecord -d /dev/lircd test.txt

---

### Post by rodercot on 2009-03-10
You may want to change the name or your remote in your hardware.conf to like custom for example.

 What are the guys saying at codeka about the 0038, I know it was a bit trickier than the new ffdc LCD device. 

 But yes, right now YOu have a socket (lircd) and no device, which does not make any sense as you are forcing it with the device /dve/lirc0 in you hardware.conf.
 
 My lircd file may not work with your IR rcvr in that case, that is for the ir in the fusion 430 model with the LCD.
 
 Dave

---

### Post by Lido on 2009-03-11
I'm using the lircd.conf from post #10 in this thread.

The Fusion Remote seems to be identical to the 430, the only difference seems to be that the "Remote" comes with a remote controll and doesn't come with a power supply. The Fusion Remote has an LCD in the front just like the Fusion 430. I know some older Fusion cases came with a VFD rather than an LCD, but this case has an LCD.

Thanks for the tip about specifying the device. I can now run irrecord, but just like irw, it seems to kill whatever lirc process is running. At least irrecord generates an error with some output:
```
Press RETURN now to start recording.
irrecord: error reading from /dev/lircd
irrecord: No such file or directory
Bus error

```

---

### Post by azmyth on 2009-03-11
Your device isn't being created so the irrecord link to /dev/lircd will not work. I made sure the name of the remote matched in the hardware.conf

so

name mceusb #from lircd.conf
REMOTE="mceusb" #in hardware.conf

If that doesn't work, I'd just try it manually to see if you can get it to work.

rename the hardware.conf to hardware.conf.old reboot

then
modprobe lirc_dev
modprobe lirc_imon

lircd -d /dev/lirc0 /etc/lircd.conf --nodaemon

The nodaemon will keep lircd running in a terminal so you can see any errors. If that looks good then

lircd -d /dev/lirc0 /etc/lircd.conf

then try irw and irrecord

If that doesn't work, I'm out of ideas.

---

### Post by Lido on 2009-03-11
Thanks. Changing hardware.conf with mceusb didn't seem to help. I moved hardware.conf, rebooted and then ran lirc nodaemon and got this:
```
$ sudo lircd -d /dev/lirc0 /etc/lircd.conf --nodaemon
lircd-0.8.3[6936]: lircd(userspace) ready

```
So I opened another terminal to see if lirc0 was in dev, but:
```
$ ls -al /dev | grep lirc
srw-rw-rw-   1 root   root           0 2009-03-10 23:57 lircd

```
I tried running it manually, but irw just dumped me back to the command line as usual and irrecord fails the same way as before:
```

$ sudo lircd -d /dev/lirc0 /etc/lircd.conf
$ irw
$ ls -al /dev | grep lirc
srw-rw-rw-   1 root   root           0 2009-03-11 00:02 lircd
$ ps aux | grep lirc
user2      7049  0.0  0.0   7452   880 pts/0    R+   00:03   0:00 grep lirc

$ sudo irrecord -d /dev/lircd test.txt

irrecord -  application for recording IR-codes for usage with lirc
...{snip}...
Press RETURN now to start recording.
irrecord: error reading from /dev/lircd
irrecord: No such file or directory
Bus error

```

---

### Post by rodercot on 2009-03-11
Try this post and see if it helps you out at all.

 [http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)

 Dave

---

### Post by Kalibur on 2009-03-11
> **rodercot said:**
> Try this post and see if it helps you out at all.

 [http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)

 Dave

I have been thru that thread several times but with no luck.  Some patches are outdated/missing.  But let me know how it goes.

PS:  I have the fusion remote case as well (15c9:0038).  And I have never got a single twitch out of the remote, Lcd or volume knob.  Its a brilliant peace of hardware so lets not give up on it.

---

### Post by Lido on 2009-03-13
Would it make any difference if I tried the external USB receiver that came with the MCE remote? I'd prefer to use the case's receiver, but if that won't work, I'll try the other one that I have.

---

### Post by rodercot on 2009-03-13
> **Lido said:**
> Would it make any difference if I tried the external USB receiver that came with the MCE remote? I'd prefer to use the case's receiver, but if that won't work, I'll try the other one that I have.

 You would need to open up the case and remove the USB connection from the LCD and the power to the device and then setup your usb rcvr. If you do this and then plug in the dongle you should be able to use the Myth Control Center and setup your device as an MCE New version et all and you should be off and running. Control Centre should overwrite your existing Lurc files and set you up using the new generic files for the mce remote. Now the only issue with this is if the remote you have does not respond to the same codes that are in the generic MCE Lircd file, if this is the case you may have to do an irrecord on your device. 

 Dave

---

