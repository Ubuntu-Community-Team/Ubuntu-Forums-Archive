---
title: "Hauppauge PVR-150 remote setup"
date: 2009-05-17
forum: Mythbuntu
---

### Post by 40-Dan on 2009-05-17
Hello all.  I'm at my wits end.  Let me start by saying that I have tried suggestions offered in the following threads several times with no success:

[http://xbmc.org/forum/showthread.php?t=46877](http://xbmc.org/forum/showthread.php?t=46877)
[http://ubuntuforums.org/showthread.php?t=1080814](http://ubuntuforums.org/showthread.php?t=1080814)

I am trying to setup the remote and receiver that came w/ a Hauppauge PVR-150.  On the page [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote), its the 3rd one from the right.

It appears that my machine is, in fact, seeing the button presses (as confirmed by mode2) but I am still unable to control it.  Following are what I think are all pertinent files and messages.  Sorry for the long post, but I wanted to get all the info out at once.  I appreciate any help in advance.

Please note that I am dealing with XBMC rather than Myth, but I was finding good info in this forum that I will assume would apply to either.  Also, I am crossposting this to the XBMC forums.

/etc/lirc/lircd.conf
```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(default) on Mon Feb 23 23:55:04 2009
#
# contributed by 
#
# brand:                       /home/xbmc/haumce.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  mceusb
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2674   870
  one           455   427
  zero          455   427
  pre_data_bits   24
  pre_data       0x1BFF82
  gap          106288
  min_repeat      1
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          TV                       0x1BB9
          Music                    0x1BB8
          Pictures                 0x1BB6
          Videos                   0x1BB5
          Power                    0x1BF3
          Stop                     0x1BE6
          Record                   0x1BE8
          Pause                    0x1BE7
          Play                     0x1BE9
          Rewind                   0x1BEA
          Foward                   0x1BEB
          Replay                   0x1BE4
          Skip                     0x1BE5
          Back                     0x1BDC
          More                     0x1BF0
          Up                       0x1BE1
          Left                     0x1BDF
          Right                    0x1BDE
          OK                       0x1BDD
          Down                     0x1BE0
          VolUp                    0x1BEF
          VolDown                  0x1BEE
          Home                     0x1BF2
          ChanDown                 0x1BED
          ChanUp                   0x1BEC
          Mute                     0x1BF1
          RecTV                    0x1BB7
          Guide                    0x1BD9
          LiveTV                   0x1BDA
          DVD                      0x1BDB
          One                      0x1BFE
          Two                      0x1BFD
          Three                    0x1BFC
          Four                     0x1BFB
          Five                     0x1BFA
          Six                      0x1BF9
          Seven                    0x1BF8
          Eight                    0x1BF7
          Nine                     0x1BF6
          Star                     0x1BE2
          Zero                     0x1BFF
          Hash                     0x1BE3
          Clear                    0x1BF5
          Enter                    0x1BF4
      end codes

end remote
```

/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf

#

#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)
"
REMOTE_MODULES="lirc_dev lirc_mceusb2"

REMOTE_DRIVER=""

REMOTE_DEVICE="/dev/lirc1"

REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"

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

output from ls -l /dev/lirc*
```
crw-rw---- 1 root root 61, 0 2009-05-17 15:56 /dev/lirc0
crw-rw---- 1 root root 61, 1 2009-05-17 15:56 /dev/lirc1
srw-rw-rw- 1 root root     0 2009-05-17 16:33 /dev/lircd
```

output from lsmod | grep lirc
```
lirc_mceusb2           20996  0
lirc_imon              22924  0
lirc_dev               19892  2 lirc_mceusb2,lirc_imon
```

output from dmesg | grep -i lirc
```
[   14.528433] lirc_dev: IR Remote Control driver registered, major 61
[   14.841433] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[   14.841436] lirc_imon: Venky Raju <dev@venky.ws>
[   14.841452] lirc_imon: imon_probe: found IMON device
[   14.841459] lirc_dev: lirc_register_plugin: sample_rate: 0
[   14.841529] lirc_imon: imon_probe: Registered iMON plugin(minor:0)
[   14.841576] lirc_imon: imon_probe: iMON device on usb<2:4> initialized
[   14.841591] usbcore: registered new interface driver lirc_imon
[   14.872904] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.51 $
[   14.872907] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   15.273069] lirc_dev: lirc_register_plugin: sample_rate: 0
[   15.280053] lirc_mceusb2[3]: SMK eHome Infrared Transceiver on usb2:3
[   15.280099] usbcore: registered new interface driver lirc_mceusb2

```

output from sudo --mode2 --device=/dev/lirc1 (after stopping lirc daemon)
```
space 450
pulse 900
space 850
pulse 450
space 400
pulse 500
space 400
pulse 450
space 450
pulse 450
space 400
pulse 500
space 400
pulse 450
space 450
pulse 900
space 850
pulse 900

```

(The above is just a snippet.  It repeats a LOT)

---

### Post by AlecJ on 2009-05-18
I think what you looking for is covered here
[http://ubuntuforums.org/showthread.php?t=1133689](http://ubuntuforums.org/showthread.php?t=1133689)

---

### Post by 40-Dan on 2009-05-18
> **AlecJ said:**
> I think what you looking for is covered here
[http://ubuntuforums.org/showthread.php?t=1133689](http://ubuntuforums.org/showthread.php?t=1133689)

I think I've tried everything in there.  No dice.

---

