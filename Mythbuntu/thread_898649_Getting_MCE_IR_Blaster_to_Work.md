---
title: "Getting MCE IR Blaster to Work"
date: 2008-08-23
forum: Mythbuntu
---

### Post by i.wanna.corndog on 2008-08-23
Hey everyone,

I am not exactly using Mythbuntu, but I know that this is probably the best place to get help with a remote issue.

I am trying to set up my MCE IR receiver to send IR commands to my stereo system via a web interface (in other words, I want to be able to click a link on a webpage to turn my stereo on and off and to adjust the volume, etc).

I am using an MCE version 2 remote (Philips brand) and have LIRC set up to recognize the remote I want to emulate (I can monitor button presses using irv). As a side note, I have an additional Toshiba branded IR receiver that is also supported, but the IR blaster has the same problem.

The problem is that, when I use the irsend command, nothing happens. I have tried plugging the IR blaster into ports 1 and 2 with no luck.

This is the command I use:
```
irsend --device=/dev/lircd SEND_ONCE AIWA POWER
``` where AIWA is the remote and POWER is the function.

The command appears to work (and does the same even if I leave out the device), but no IR signal is transmitted. I know that the IR blaster works (I have tested it in Windows), but I am positive that no IR signal is being emitted (I used my digital camera to verify this).

Another piece of information that may be relevant is that, when I set up LIRC, I chose "NONE" as the Transmitter. The only options under the MCE remotes were DirectTV and other cable boxes. I didn't think I needed to set that up, but I could be wrong.

I am also posting my conf files here if that helps:

lircd.conf
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

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#
# this config file was automatically generated
# using lirc-0.8.1-CVS(default) on Thu Nov  2 13:57:51 2006
#
# contributed by Carlos Fdez Manteiga <churlyATgmail.com>
#
# brand:                       AIWA
# model no. of remote control: RC-ZAS02
# devices being controlled by this remote: AIWA NSX-DR5
#

begin remote

  name  AIWA
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9082  4401
  one           662  1584
  zero          662   462
  ptrail        660
  pre_data_bits   26
  pre_data       0x1D8113F
  gap          109023
  toggle_bit      0


      begin codes
          CD1                      0x8A75
          CD2                      0x4AB5
          CD3                      0xCA35
          1                        0x807F
          2                        0x40BF
          3                        0xC03F
          4                        0x20DF
          5                        0xA05F
          6                        0x609F
          7                        0xE01F
          8                        0x10EF
          9                        0x906F
          0                        0x50AF
          +10                      0xD02F
          FUNCTION                 0x7887
          PAUSE                    0x22DD
          PLAY                     0x02FD
          PREV                     0xC23D
          NEXT                     0x42BD
          STOP                     0x827D
          VOL+                     0xB24D
          VOL-                     0x728D
          POWER                    0x00FF
      end codes

end remote

# This config file was automatically generated
# using lirc-0.8.1pre2(default) on Thu Mar 29 12:09:38 2007
#
# contributed by Adam Luker
#
# brand: Apex
# model no. of remote control: K12B-C2
# devices being controlled by this remote: Apex TV AT2702
#

begin remote

  name  APEX
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9006  4419
  one           607  1625
  zero          607   510
  ptrail        605
  repeat       9004  2176
  pre_data_bits   16
  pre_data       0x2FD
  gap          107348
  toggle_bit      0


      begin codes
          power                    0x48B7
          1                        0x807F
          2                        0x40BF
          3                        0xC03F
          4                        0x20DF
          5                        0xA05F
          6                        0x609F
          7                        0xE01F
          8                        0x10EF
          9                        0x906F
          0                        0x00FF
          ch-                      0xF807
          ch+                      0xD827
          100+                     0xD02F
          vol-                     0x7887
          vol+                     0x58A7
          timer                    0x708F
          up                       0x9867
          display                  0x6897
          left                     0x629D
          menu                     0xDA25
          right                    0xE21D
          down                     0xB847
          picture                  0x8877
          scan                     0x827D
          mute                     0x08F7
          recall                   0x02FD
          cc                       0xE817
          video                    0x28D7
      end codes

end remote
```

hardware.conf
```
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

---

### Post by i.wanna.corndog on 2008-08-24
Bump.

If this helps, I know that the serial port IR blaster requires the module lirc_serial to be running. Is there a similar module for the MCE IR blaster, or should it work out of the box?

---

### Post by i.wanna.corndog on 2008-08-29
Bump.

I went and bought a new IR blaster (mono plug) because I thought the one i had might be messed up, but I'm still having no luck. Anyone?

---

### Post by freymann on 2008-08-29
I guess since you're not exactly using MythBuntu, you may be in the wrong place looking for help!

All I can offer you is my walk-through on how I got the MCE Transceiver blasting, using MythBuntu of course. 

Try this url:

[http://ubuntuforums.org/showthread.php?p=4527005#post4527005](http://ubuntuforums.org/showthread.php?p=4527005#post4527005)

---

