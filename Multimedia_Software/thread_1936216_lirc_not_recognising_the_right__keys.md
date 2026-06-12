---
title: "lirc not recognising the right  keys"
date: 2012-03-05
forum: Multimedia Software
---

### Post by BertN45 on 2012-03-05
I have a problem with my remote control for me Encore ENLTV+FM card. I am using tvtime and it works fine using keyboard and mouse. I am using Ubuntu 12.04. The remote control works also, but the keys have a different result as I defined. I am trying to use lirc and I am trying now for more than 2 days, please help.
I lost the original remote control, but use another one from freecom, the freecom codes recorded by irrecord are:

```
# using lirc-0.9.0(devinput) on Mon Mar  5 15:10:00 2012
#
# contributed by 
#
# brand:                       lircd.conf.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  lircd.conf
  bits           56
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x0
  gap          195847
  toggle_bit_mask 0x0

      begin codes
          KEY_POWER                0x04000400000012 0x00000000000001
          KEY_MUTE                 0x04000400000001 0x00000000000001
          KEY_VOLUMEUP             0x0400040000001A 0x00000000000001
          KEY_VOLUMEDOWN           0x04000400000002 0x00000000000001
          KEY_CHANNELUP            0x0400040000001E 0x00000000000001
          KEY_CHANNELDOWN          0x04000400000003 0x00000000000001
          KEY_1                    0x04000400000004 0x00000000000001
          KEY_2                    0x04000400000005 0x00000000000001
          KEY_3                    0x04000400000006 0x00000000000001
          KEY_4                    0x04000400000007 0x00000000000001
          KEY_5                    0x04000400000008 0x00000000000001
          KEY_6                    0x04000400000009 0x00000000000001
          KEY_7                    0x0400040000000A 0x00000000000001
          KEY_8                    0x0400040000001B 0x00000000000001
          KEY_9                    0x0400040000001F 0x00000000000001
          KEY_0                    0x0400040000000D 0x00000000000001
          KEY_ZOOM                 0x0400040000000C 0x00000000000001
          KEY_BACK                 0x0400040000000E 0x00000000000001
      end codes

end remote
```For instance channel-down button results in 2, the button 1 results in 3, the 2 in 4, the 3 in 6, etc. Some buttons have no reaction at all. My .lircrc file looks like:

```
begin
    prog = irexec
    button = KEY_SCREEN
    config = tvtime-command TOGGLE_FULLSCREEN
end

begin
    prog = irexec
    button = KEY_MUTE
    config = xsendkeycode 121 1; xsendkeycode 121 0
end

# Menu navigation.
begin
    prog = irexec
    button = KEY_CHANNELUP
    config = tvtime-command UP
end

begin
    prog = irexec
    button = KEY_CHANNELDOWN
    config = tvtime-command DOWN
end

begin
   prog = irexec
   button = KEY_VOLUMEUP
   config = xsendkeycode 123 1; xsendkeycode 123 0
end

begin
   prog = irexec
   button = KEY_VOLUMEDOWN
   config = xsendkeycode 122 1; xsendkeycode 122 0
end

begin
    prog   = irexec
    button = KEY_1
    config = tvtime-command CHANNEL_1
end

begin
    prog   = irexec
    button = KEY_2
    config = tvtime-command CHANNEL_2
end

begin
    prog   = irexec
    button = KEY_3
    config = tvtime-command CHANNEL_3
end
begin
    prog   = irexec
    button = KEY_4
    config = tvtime-command CHANNEL_4
end
begin
    prog   = irexec
    button = KEY_5
    config = tvtime-command CHANNEL_5
end
begin
    prog   = irexec
    button = KEY_6
    config = tvtime-command CHANNEL_6
end
begin
    prog   = irexec
    button = KEY_7
    config = tvtime-command CHANNEL_7
end
begin
    prog   = irexec
    button = KEY_8
    config = tvtime-command CHANNEL_8
end
begin
    prog   = irexec
    button = KEY_9
    config = tvtime-command CHANNEL_9
end
begin
    prog   = irexec
    button = KEY_0
    config = tvtime-command CHANNEL_0
end
begin
    prog = irexec
    button = KEY_BACK
    config = tvtime-command ENTER
end

begin
    prog = irexec
    button = KEY_POWER
    config = tvtime &
    config = tvtime-command QUIT
end

```My hardware.conf file looks like:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Encore ELTV-FM"
#REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
#REMOTE_DEVICE="/dev/lirc0"
#REMOTE_DEVICE="/dev/input/event3"
REMOTE_DEVICE="/dev/lirc"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
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
```t looks like these tables are not used and tvtime gets its commands  directly from a keyboard type of device. Whatever I change in the  lircd.conf and .lircrc files the result remains the same mismatch.

---

### Post by BertN45 on 2012-03-10
Nobody?? The hardware works. I can change channels, but the key assignment is wrong and some keys are missing. The key assignment is independent of the lircd.conf, What could be the problem?

---

### Post by BertN45 on 2012-03-14
I solved the problem. By using the Freecom remote with the Encore ENLTV+FM TV card the code were unequal to the TV card and unequal to the Freecom remote. Irrecord created a file with the raw codes and that did not work either.

I have used the generic lircd.conf.gnome which contains all codes that can be generated and renamed it to lircd.conf. I have started irw and checked which codes were generated by which button of the remote. I have created a new lircd.conf file with the freecom button names and the codes generated using lircd.conf.gnome.

I have used irxevent in order to use the keyboard shortcuts published by tvtime. Afterwards my remote worked, except volume control. I have assigned the F11 and F12 keys for Volume Control in system settings -> keyboard -> Shortcuts -> Sound and Media. And I have used the program xte from the xautomation package in .lircrc as follows:

```
begin
    prog = irxevent
    button = KEY_ZOOM
    config = Key f CurrentWindow
end
begin
    prog = irxevent
    button = KEY_CHANNELUP
    config = Key Up CurrentWindow
end
begin
    prog = irxevent
    button = KEY_CHANNELDOWN
    config = Key Down CurrentWindow
end
begin
   prog = irexec
   button = KEY_VOLUMEUP
   config = /usr/bin/xte "key F12"
   repeat = 1
end
begin
   prog = irexec
   button = KEY_VOLUMEDOWN
   config = /usr/bin/xte "key F11"
   repeat = 1
end
begin
    prog   = irxevent
    button = KEY_1
    config = Key 1 CurrentWindow
end
begin
    prog   = irxevent
    button = KEY_2
    config = Key 2 CurrentWindow
end

etc
```

The last step was to write a small script for the start-up applications that starts irexec and irxevent as a daemon.

Yesterday I was able to watch TV from the couch using the remote.

---

