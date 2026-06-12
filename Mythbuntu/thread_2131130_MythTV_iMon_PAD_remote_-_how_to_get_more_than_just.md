---
title: "MythTV iMon PAD remote - how to get more than just the PAD working."
date: 2013-03-31
forum: Mythbuntu
---

### Post by Fynn on 2013-03-31
Installed Mythbuntu on my htpc, which comes equipped with a VFD plus iMon PAD remote.  At present the only thing that is working on it is the directional pad in the middle, plus the Select button.  The VFD display is working ok.

lsusb shows:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 15c2:0036 SoundGraph Inc. LC16M VFD Display/IR Receiver
Bus 001 Device 004: ID 05e3:070e Genesys Logic, Inc. USB 2.0 Card Reader
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk [Elements]
Bus 002 Device 004: ID 20e8:5861
Bus 001 Device 006: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 007: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse

```

/etc/lirc/hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-pad"
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
LOAD_MODULES="false"

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

/etc/lirc/lircd.conf:

```

#Configuration for the Soundgraph iMON PAD IR/VFD remote:
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-pad"

```

/usr/share/lirc/remotes/imon/lircd.conf.imon-pad:
```

#
# this config file was automatically generated
# using lirc-0.7.1pre2(imon) on Tue Mar  1 23:15:44 2005
#
# contributed by Venky Raju
#
# brand:                       iMON-New
# model no. of remote control: iMON-PAD
# devices being controlled by this remote:
#

begin remote

  name     iMON-PAD
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          235965
  min_repeat      1
  toggle_bit      0


      begin codes
          KEY_EXIT                 0x288195B7
          KEY_POWER                0x289115B7
          KEY_RECORD               0x298115B7
          KEY_PLAY                 0x2A8115B7
          SlowMotion               0x29B195B7
          KEY_REWIND               0x2A8195B7
          KEY_PAUSE                0x2A9115B7
          KEY_FASTFORWARD          0x2B8115B7
          KEY_PREVIOUS             0x2B9115B7
          KEY_STOP                 0x2B9715B7
          KEY_NEXT                 0x298195B7
          KEY_ESC                  0x2BB715B7
          Eject                    0x299395B7
          AppLauncher              0x29B715B7
          MultiMon                 0x2AB195B7
          TaskSwitcher             0x2A9395B7
          KEY_MUTE                 0x2B9595B7
          KEY_VOLUMEUP             0x28A395B7
          KEY_VOLUMEDOWN           0x28A595B7
          KEY_CHANNELUP            0x289395B7
          KEY_CHANNELDOWN          0x288795B7
          Timer                    0x2B8395B7
          KEY_1                    0x28B595B7
          KEY_2                    0x2BB195B7
          KEY_3                    0x28B195B7
          KEY_4                    0x2A8595B7
          KEY_5                    0x299595B7
          KEY_6                    0x2AA595B7
          KEY_7                    0x2B9395B7
          KEY_8                    0x2A8515B7
          KEY_9                    0x2AA115B7
          KEY_0                    0x2BA595B7
          ShiftTab                 0x28B515B7
          KEY_TAB                  0x29A115B7
          KEY_VIDEO                0x2B8515B7
          KEY_AUDIO                0x299195B7
          KEY_PHOTO                0x2BA115B7
          KEY_TV                   0x28A515B7
          KEY_BOOKMARKS            0x288515B7
          Thumbnail                0x2AB715B7
          AspectRatio              0x29A595B7
          FullScreen               0x2AA395B7

          KEY_DVD                  0x29A295B7
          KEY_MENU                 0x2BA385B7
# different codes
          KEY_DVD                  0x29A3D5B7
          KEY_MENU                 0x2BA3D5B7

          Caption                  0x298595B7
          KEY_LANGUAGE             0x2B8595B7
          MouseKeyboard            0x299115B7
          SelectSpace              0x2A9315B7
          MouseMenu                0x28B715B7
          BTN_RIGHT                0x688481B7
          KEY_ENTER                0x28A195B7
          BTN_LEFT                 0x688301B7
          WindowsKey               0x2B8195B7
          KEY_BACKSPACE            0x28A115B7
# Corrin added
	  KEY_SPACE                0x2B9B15F7
          KEY_UP                   0xEB53F9B7
          KEY_LEFT                 0x6ABAFFBF
          KEY_DOWN                 0x6F9ECBB7
          KEY_RIGHT                0x69A281B7
# Variants and additions of keys reported by Ryan Gardner
          KEY_1                    0x0200001E
          KEY_2                    0x0200001F
          KEY_3                    0x02000020
          KEY_4                    0x02000021
          KEY_5                    0x02000022
          KEY_6                    0x02000023
          KEY_7                    0x02000024
          KEY_8                    0x02000025
          KEY_9                    0x02000026
          Star                     0x02200025
          KEY_0                    0x02000027
          Hash                     0x02200020
          KEY_BACKSPACE            0x0200002A
          KEY_SELECT               0x0200002C
          LeftMenu                 0x02800000
          RightMenu                0x02000065
          KEY_ENTER                0x02000028
          KEY_ESC                  0x02000029
          BTN_LEFT                 0x01010000
          BTN_RIGHT                0x01020000
          KEY_UP                   0x01008000
          KEY_DOWN                 0x01007F00
          KEY_LEFT                 0x01000080
          KEY_RIGHT                0x0100007F
# Variations on the mouse buttons from Jan Schneider
          BTN_LEFT                 0x01010080
          BTN_RIGHT                0x01020080

      end codes

end remote

#
# this config file was automatically generated
# using lirc-0.8.0(userspace) on Tue Oct 17 22:45:11 2006
#
# contributed by 
#
# brand:                       Antec Fusion Wheel
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  Antec_Fusion_Wheel
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  16
  post_data      0xFF
  gap          131971
  min_repeat      1
  toggle_bit      0


      begin codes
          CCW                      0x0100
          CW                       0x0001
      end codes

end remote

#
# this config file was automatically generated
# using lirc-0.8.5(default) on Tue May 26 22:07:16 2009
#
# contributed by Karl Newman, based on lircd.conf.imon-pad in lirc-0.8.4
# devices with USB ID 0x15c2, 0x0038 are using 64 codes in 0.8.5
#
# brand:                       iMON-New
# model no. of remote control: iMON-PAD
# devices being controlled by this remote:
#

begin remote

  name   iMON-PAD64
  bits           64
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          135993
  toggle_bit_mask 0x0
  ignore_mask 0x00000000FFFFFFFF

      begin codes
          KEY_EXIT                 0x288195B700002401
          KEY_POWER                0x289115B700002401
          KEY_RECORD               0x298115B700002401
          KEY_PLAY                 0x2A8115B700002401
          SlowMotion               0x29B195B700002401
          KEY_REWIND               0x2A8195B700002401
          KEY_PAUSE                0x2A9115B700002401
          KEY_FASTFORWARD          0x2B8115B700002401
          KEY_PREVIOUS             0x2B9115B700002401
          KEY_STOP                 0x2B9715B700002401
          KEY_NEXT                 0x298195B700002401
          KEY_ESC                  0x2BB715B700002401
          KEY_EJECT                0x299395B700002401
          AppLauncher              0x29B715B700002401
          MultiMon                 0x2AB195B700002401
          TaskSwitcher             0x2A9395B700002401
          KEY_MUTE                 0x2B9595B700002401
          KEY_VOLUMEUP             0x28A395B700002401
          KEY_VOLUMEDOWN           0x28A595B700002401
          KEY_CHANNELUP            0x289395B700002401
          KEY_CHANNELDOWN          0x288795B700002401
          Timer                    0x2B8395B700002401
          KEY_1                    0x28B595B700002401
          KEY_2                    0x2BB195B700002401
          KEY_3                    0x28B195B700002401
          KEY_4                    0x2A8595B700002401
          KEY_5                    0x299595B700002401
          KEY_6                    0x2AA595B700002401
          KEY_7                    0x2B9395B700002401
          KEY_8                    0x2A8515B700002401
          KEY_9                    0x2AA115B700002401
          KEY_0                    0x2BA595B700002401
          ShiftTab                 0x28B515B700002401
          KEY_TAB                  0x29A115B700002401
          KEY_VIDEO                0x2B8515B700002401
          KEY_AUDIO                0x299195B700002401
          KEY_PHOTO                0x2BA115B700002401
          KEY_TV                   0x28A515B700002401
          KEY_BOOKMARKS            0x288515B700002401
          Thumbnail                0x2AB715B700002401
          AspectRatio              0x29A595B700002401
          FullScreen               0x2AA395B700002401

          KEY_DVD                  0x29A295B700002401
          KEY_MENU                 0x2BA385B700002401
# different codes
# These codes are the button release codes, which will cause duplicate
# events, so they are commented out here.
#          KEY_DVD                  0x29A3D5B700002401
#          KEY_MENU                 0x2BA3D5B700002401

          Caption                  0x298595B700002401
          KEY_LANGUAGE             0x2B8595B700002401
          MouseKeyboard            0x299115B700002401
          SelectSpace              0x2A9315B700002401
          MouseMenu                0x28B715B700002401
          BTN_RIGHT                0x688481B700002401
          KEY_ENTER                0x28A195B700002401
          BTN_LEFT                 0x688301B700002401
          WindowsKey               0x2B8195B700002401
          KEY_BACKSPACE            0x28A115B700002401
# Corrin added
          KEY_SPACE                0x2B9B15F700002401
          KEY_UP                   0xEB53F9B700002401
          KEY_LEFT                 0x6ABAFFBF00002401
          KEY_DOWN                 0x6F9ECBB700002401
          KEY_RIGHT                0x69A281B700002401
# Variants and additions of keys reported by Ryan Gardner
          KEY_1                    0x0200001E00000000
          KEY_2                    0x0200001F00000000
          KEY_3                    0x0200002000000000
          KEY_4                    0x0200002100000000
          KEY_5                    0x0200002200000000
          KEY_6                    0x0200002300000000
          KEY_7                    0x0200002400000000
          KEY_8                    0x0200002500000000
          KEY_9                    0x0200002600000000
          Star                     0x0220002500000000
          KEY_0                    0x0200002700000000
          Hash                     0x0220002000000000
          KEY_BACKSPACE            0x0200002A00000000
          KEY_SELECT               0x0200002C00000000
          LeftMenu                 0x0280000000000000
          RightMenu                0x0200006500000000
          KEY_ENTER                0x0200002800000000
          KEY_ESC                  0x0200002900000000
          BTN_LEFT                 0x0101000000000000
          BTN_RIGHT                0x0102000000000000
          KEY_UP                   0x0100800000000000
          KEY_DOWN                 0x01007F0000000000
          KEY_LEFT                 0x0100008000000000
          KEY_RIGHT                0x0100007F00000000
      end codes

end remote

```

Can anyone help me get this debugged and working in MythTV?  

thanks

---

### Post by mschaefe on 2013-04-08
Hi Fynn,

     We're in a similar boat right now.  I have a Silverstone LC-16, I think, with similar stuff as yours.  I can't remember the difference between the 16 and 16m.

     I have mixed results with the remote as well.  I found that the "iMon KNOB" setting worked better.  However, that will need to be updated as well.  Here's how I debugged:

The lircd.conf.xxx files are located in /usr/share/lirc/remotes/xxx/xxx.conf
The files are configured in /etc/lircd/hardware.conf and /etc/lircd/lircd.conf

I'm sure there is an official way to get the codes from the remotes, but what I've done is looked for messages in the /var/log/syslog file that look like this:

Apr  7 11:22:34 myth kernel: [ 5486.356705] imon 1-7.1:1.0: imon_incoming_packet: unknown keypress, code 0x6902a9b7

and then searched for that code in the conf files: e.g. grep -i 6902a9b7 /usr/share/lirc/remotes/imon/*.conf

None of the files are exactly what I have -- I have a PAD according to the pictures, but very few of the buttons work.  My thought is to tail -f the syslog file in one window, open the conf file in another window and fix it button by button.  I've already copied the antec knob file into the soundgraph file as lircd.conf.imon-silverstone.

Another gotcha (I'm not sure how much of a gotcha yet) is this line from the dmesg log:

[    7.411021] input: iMON Panel, Knob and Mouse(15c2:ffdc) as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7.1/1-7.1:1.0/input/input6
[    7.428026] imon 1-7.1:1.0: Unknown 0xffdc device, defaulting to VFD and iMON IR
[    7.428031]  (id 0x2e)

I think the behavior is okay, but you may want to force something else through kernel params.  I'm thinking I do need to apply a pad_stabilize parameter.

modinfo imon

...
parm:           display_type:Type of attached display. 0=autodetect, 1=vfd, 2=lcd, 3=vga, 4=none (default: autodetect) (int)
parm:           pad_stabilize:Apply stabilization algorithm to iMON PAD presses in arrow key mode. 0=disable, 1=enable (default). (int)
parm:           nomouse:Disable mouse input device mode when IR device is open. 0=don't disable, 1=disable. (default: don't disable) (bool)
parm:           pad_thresh:Threshold at which a pad push registers as an arrow key in kbd mode (default: 28) (int)

---

### Post by JamesNorris on 2013-04-10
[t=2026951]("http://ubuntuforums.org/showthread.php?t=2026951") is where I got the most help when the driver for the PAD moved into the kernel and lirc stopped cooperating. You might want to try there and see if that helps.

---

### Post by Fynn on 2013-04-10
Thank you both, will set some time aside and try to fix it.

---

