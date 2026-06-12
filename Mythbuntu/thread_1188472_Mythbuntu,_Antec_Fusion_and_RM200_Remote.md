---
title: "Mythbuntu, Antec Fusion and RM200 Remote"
date: 2009-06-15
forum: Mythbuntu
---

### Post by drumz on 2009-06-15
I have the latest Mythbuntu (9.04) installed, and I'm using an Antec Fusion Remote case and I have everything working (including the LCD panel thanks to this thread ([http://ubuntuforums.org/showthread.php?t=1069267&highlight=antec+fusion+how+to](http://ubuntuforums.org/showthread.php?t=1069267&highlight=antec+fusion+how+to)) but for the life of me I can't get the remote to work.

```
ls /dev/lirc*
/dev/lirc0  /dev/lircd
```

running 'irw' or 'mode2 -r -d /dev/lirc0' and then pressing buttons on the remote (rm200) doesn't show anything.

```
lsusb:
Bus 003 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
```

I'm using the provided lirc package and in /etc/lirc/lircd.conf I've pointed it to what I believe to be the proper config file for the RM200 remote included with the case.
```
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-pad"
```

The /etc/lirc/hardware/conf has this:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON IR/LCD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon"
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


Does anyone have this working with Mythbuntu 9.04 (clean install) and if so how?

Thanks!

---

### Post by drumz on 2009-06-16
Update:

The knob on the case is working fine:

```
mode2 -r -d /dev/lirc0
code: 0x01000000
code: 0x01000000
code: 0x01000000
code: 0x01000000
code: 0x01000000
code: 0x01000000
code: 0x01000000
code: 0x00010000
code: 0x00010000
code: 0x00010000
code: 0x00010000
code: 0x00010000
```

If I use the included remote (RM200) I don't see anything....

---

### Post by n3utrino on 2009-06-18
Hi there.

my setup with the antec fusion is working with a logitec harmony remote 

my hardware.conf loads another REMOTE_LIRCD_CONF

```

REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"

```

I'm  not sure but i think for the knob and the remote there are two different confs to load.

---

### Post by drumz on 2009-06-18
Thanks for replying!

Are you using the same hardware as me (15c2:ffdc version) and are you using the latest Mythbuntu release?  If so, did you have to follow any how-to's to manually compile/install lcdproc and lirc?

Thanks again!

---

### Post by adsf on 2009-06-22
> **drumz said:**
> Thanks for replying!

did you have to follow any how-to's to manually compile/install lcdproc and lirc?

Thanks again!

Also interested in getting this.  Want to get my harmony control working.

---

### Post by n3utrino on 2009-06-24
Hi there.

my lsusb lists

```
Bus 007 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
```

```
lsmod | grep imon
lirc_imon              22924  2
lirc_dev               19892  2 lirc_mceusb2,lirc_imon

```

ATM I only have the remote working.

[http://www.mythtv.org/wiki/Volume_Knob_on_Antec_Fusion](http://www.mythtv.org/wiki/Volume_Knob_on_Antec_Fusion)

explains the Problem with the two lirc devices. Hope this helps.

PS:No need for compiling sources and stuff. It should work out of the box. With the latest jaunty mythbuntu release. 

cheerio
n3utrino

---

### Post by drumz on 2009-06-24
For me, to get the LCD to work I followed the steps in this post [https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD) specifically 'Part 2: Setting Up The IMON ffdc Model LCD Diplay'.

I tried a completely fresh install of MythBuntu (9.04) and the supplied lcdproc didn't work, it seems it only supports the VFD.  Following the directions patches lcdproc and ands support for the LCD panel.

I'm still working on the remote issue...

---

### Post by drumz on 2009-06-24
ok, based on what n3utrino said, I left lirc alone with what was installed by a clean Mythbuntu install.

Configuring Myth (through the Mythbuntu Control Center) I selected 'Windows Media Center Remotes New Version Philips.'

This results in the following modules being loaded:
```
lsmod | grep lirc
lirc_mceusb2           20100  0 
lirc_imon              22924  1 
lirc_dev               19892  2 lirc_mceusb2,lirc_imon

```
I then configured my Hauppauge 880 to be an MCE remote.  If I stop lirc and use the mode2 utility I'm finally seeing the remote:
```
/etc/init.d/lirc stop
mode2 -r -d /dev/lirc0
code: 0x800f041e
code: 0x800f841f
code: 0x800f841f
code: 0x800f0420
code: 0x800f0420
code: 0x800f8421
code: 0x800f8421
code: 0x800f0422
code: 0x800f0422
```

The above codes don't seem to match what's provided int the lirc files.  I am able to power the system on if it's turned off, but if I start lirc, then start Mythtv and try pressing buttons nothing happens.

So I'm almost there.....

For the Hauppauge when I configured it I added a new device (Windows Media Center PC) then added an activity that uses it.  At one point I remember selecting 'My Videos' which seems to have set everything up OK on the remote side.

---

### Post by drumz on 2009-06-24
From this post [https://help.ubuntu.com/community/IMON_VFD_and_LCD](https://help.ubuntu.com/community/IMON_VFD_and_LCD) if I take the lircd.conf posted in 'Choice 2' for the remotes it has _most_ of the codes my Hauppauge 880 outputs when configured for MCE.  I'll have to adjust a few and add a few, but at least I was able to move around the Mythtv menu's, watch live tv (couldn't input channels, could only go up/down one at a time) but at least it's working.

Thanks(!!) to all the others that took the time to respond here and on the posts I've provided links to.  Without them this would have taken me a lot longer to get working.

```
#
# /etc/lirc/lircd.conf for MCE Remote with IMON LCD IR:
#
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

---

