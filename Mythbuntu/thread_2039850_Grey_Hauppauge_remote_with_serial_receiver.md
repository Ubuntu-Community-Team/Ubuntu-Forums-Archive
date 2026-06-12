---
title: "Grey Hauppauge remote with serial receiver?"
date: 2012-08-09
forum: Mythbuntu
---

### Post by bshanteau on 2012-08-09
I am currently using a grey Hauppauge remote with a serial receiver in MythDora. I would like to change to using MythBuntu, but can't until I get the remote problem solved.

I know the Hauppauge remote works OK, because it works fine in MythDora with the serial receiver as well as with a PVR-150 card. I have had no luck in Mythbuntu, however, with using the Hauppauge receiver connected to the PVR-150.

But I also have a Radio Shack 25-1116 remote, and that works OK in Mythbuntu, so I know the serial receiver is OK. Is this just a matter of editing the Radio Shack hardware.conf file so it refers to the right Hauppauge lircd.conf file and entering the correct label for the Hauppauge remote in the Radio Shack hardware.conf?

---

### Post by anonymousdog on 2012-08-10
Sort of.  You obviously DO have the receiver setup and working; so, we're just looking to give lirc the setup for the remote control's codes.

This is in two places in the lirc config files:
1) as a 'REMOTE_LIRCD_CONF="hauppauge_pvr150_grey.conf"' in hardware.conf, and
2) as an 'include "hauppauge_pvr150_grey.conf"' in lircd.conf

It appears from [here]("http://www.mythtv.org/wiki/PVR150_Remote") that no config file for the grey remote is available (though you might find one).  So, you may need to use irrecord to build the file (or "liberate" it from your MythDora system). 'sudo irrecord -d /dev/lirc0 hauppauge_pvr150_grey.conf'  If you do that, please submit the file to the lirc project.

It also appears you can abandon lirc and go [this way]("http://ubuntuforums.org/showthread.php?t=2000773").

---

### Post by bshanteau on 2012-08-11
Here is the lircd.conf file from MythDora that is working with my grey Hauppauge remote:

```
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R www.mythtvportal.com
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
```

I tried doing what I think you suggested and, starting with a working Radio Shack 15-2116 configuration in MythBuntu, I copied the MythDora lircd.conf file to /usr/share/lirc/extras/more_remotes/hauppauge/hauppauge_pvr150_grey.conf

Then I edited MythBuntu's lircd.conf to read:

```
#Configuration for the Hauppauge grey remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/hauppauge_pvr150_grey.conf"

```

I edited the REMOTE and REMOTE_LIRCD_CONF lines in MythBuntu's hardware.conf (MythDora has no such file) to read:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge grey"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/hauppauge_pvr150_grey.conf"
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

I rebooted and found that the Hauppauge grey remote wasn't working.

Digging around a little bit, I found that both MythDora and MythBuntu have ~/.lircrc files and that these files are specific to the remote. I tried copying the MythDora version of this file to MythBuntu, but pointing the Hauppauge grey remote at the serial receiver still has no effect in MythTV.

What now?

---

