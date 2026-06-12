---
title: "lirc / irblaster not working"
date: 2011-03-11
forum: Mythbuntu
---

### Post by swan1 on 2011-03-11
Edit: Hmm, posting the question seems to have fixed this.  Removed the non-existent creative
receiver and after a few errors trying to reset lirc several times it started working. 

I think I'm close, but can't get lirc to work (and thus, can't get mythtv to work either).  Running
mythbuntu 10.10.  When I try:

> /etc/init.d/lirc restartsyslog shows:

> Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2372]: lircd(creative) ready, using /var/run/lirc/lircd
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2377]: lircd(default) ready, using /var/run/lirc/lircd1
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2372]: accepted new client from 127.0.0.1
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2372]: could not reset tty
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2372]: Failed to initialize hardware
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2372]: select() failed
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2372]: Bad file descriptor
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2372]: removed client
Mar 11 12:38:23 myth-backend lircd-0.8.7-pre3[2377]: connected to localhost
Mar 11 12:38:28 myth-backend lircd-0.8.7-pre3[2377]: connected to localhost
hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Comcast_3067BC2-R"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="comcast/3067BC2-R.conf"
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

```lircd.conf:
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

#Configuration for the Custom remote:
include "/usr/share/lirc/remotes/creative/lircd.conf.creative"

#Configuration for the Serial Port (UART) : Comcast remote transmitter:
include "/usr/share/lirc/extras/transmitters/comcast/3067BC2-R.conf"

```3067BC2-R.conf:
```
# this config file was automatically generated
# using lirc-0.8.6(default) on Sat Jul 31 16:36:24 2010
#
# contributed by Kyle Anderson <kyle|xkyle.com
#
# brand: Comcast
# model no. of remote control: 3067BC2-R
# devices being controlled by this remote: Comcast DTA
#

begin remote

  name  Comcast_3067BC2-R
  bits           24
  flags XMP
  eps            20
  aeps          300

  one             0   137
  zero          250   710
  ptrail        250
  pre_data_bits   32
  pre_data       0x170F443E
  post_data_bits  8
  post_data      0x0
  pre           250 12921
  gap          81698
  toggle_bit_mask 0x0

      begin codes
          KEY_INFO                 0x170026
          KEY_1                    0x1E0001
          KEY_2                    0x1D0002
          KEY_3                    0x1C0003
          KEY_4                    0x1B0004
          KEY_5                    0x1A0005
          KEY_6                    0x190006
          KEY_7                    0x180007
          KEY_8                    0x170008
          KEY_9                    0x160009
          KEY_0                    0x1F0000
          KEY_ENTER                0x180025
          KEY_LANGUAGE             0x150082
      end codes

end remote

```

---

