---
title: "Lirc issue"
date: 2009-09-21
forum: Mythbuntu
---

### Post by pablo79 on 2009-09-21
Dear all, I've installed Mythbuntu 9.04 in a pc with a LC16M Silverstone case. I've installed lirc 0.8.7 CVS. The VFD works correctly and also the remote works with mode2 and irw but when I run mythfrontend there is a lirc_init error, and Myth looking for a file or directory that doesn't find. Which file?

[Here]("http://mythbuntu.pastebin.com/f65ba7716") you find the log created with Log grabber.

Please help me. It's a month I'm working to have the case fully working!

Thank you,
  Pablo

---

### Post by pablo79 on 2009-09-21
I've also tried to redirect lircd output on /dev/lircd but it doesn't solve the situation. :confused::confused:

---

### Post by bsntech on 2009-09-22
A few things -

If you just type in irw at a terminal and begin pressing buttons on the remote, do you get some gibberish that shows up in the terminal window?  If so, this shows the computer is receiving the remote key presses.

next thing, ensure you do the following command (if you have not done so already) and then reboot your computer:

echo &#8220;lirc_i2c&#8221; | sudo tee &#8211;a /etc/modules

Lastly, do you have your lircrc file in your ~/.mythtv/ folder or a .lircrc file in your ~/ folder?  One or the other is needed, and the best bet is to make the .lircrc file in your ~/ folder since this is the same file that lirc looks for as the default config file.

---

### Post by williammanda on 2009-09-22
Pablo79
Post your lirc files: hardware.conf, lircd.conf and ~/.mythtv/licrc which should be a symlink to ~/.lirc/mythtv

---

### Post by pablo79 on 2009-09-23
Dear guys, my remote worked correctly with irw (now after I've tried to find a solution it is broken), the only problem seems to was mythtv. This evening I will reconfigure the system to works with irw (that is the first step). The problem I have in this moment should be the init script in init.d.

The files you requested me:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lircd.conf"
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
#/etc/lirc/lircd.conf
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

include "/home/paolo/iMON-PAD"
```

```
#/home/paolo/iMON-PAD
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.7-CVS(default) on Sat Sep 19 09:32:28 2009
#
# contributed by 
#
# brand:                       iMON-PAD
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  iMON-PAD
  bits           64
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          95990
  toggle_bit_mask 0x400000000000

      begin codes
          AppExit                  0x288195B700000101
          Power                    0x289115B700000101
          Record                   0x298115B700000101
          Play                     0x2A8115B700000101
          SlowMotion               0x29B195B700000101
          Rewind                   0x2A8195B700000101
          Pause                    0x2A9115B700000101
          FastForword              0x2B8115B700000101
          PrevChapter              0x2B9115B700000101
          Stop                     0x2B9715B700000101
          NextChapter              0x298195B700000101
          Esc                      0x0200002900000000
          Eject                    0x299395B700000101
          AppLauncher              0x29B715B700000101
          MultiMon                 0x2AB195B700000101
          TaskSwitcher             0x2A9395B700000101
          Mute                     0x2B9595B700000101
          Vol+                     0x28A395B700000101
          Vol-                     0x28A595B700000101
          Ch+                      0x289395B700000101
          Ch-                      0x288795B700000101
          Timer                    0x2B8395B700000101
          1                        0x0200001E00000000
          2                        0x0200001F00000000
          3                        0x0200002000000000
          4                        0x0200002100000000
          5                        0x0200002200000000
          6                        0x0200002300000000
          7                        0x0200002400000000
          8                        0x0200002500000000
          9                        0x0200002600000000
          Star                     0x0220002500000000
          0                        0x0200002700000000
          Hash                     0x0220002000000000
          Videos                   0x2B8515B700000101
          Music                    0x299195B700000101
          Pictures                 0x2BA115B700000101
          Tv                       0x28A515B700000101
          Bookmark                 0x288515B700000101
          Thumbnail                0x2AB715B700000101
          Zoom                     0x29A595B700000101
          FullScreen               0x2AA395B700000101
          Dvd                      0x29A395B700000101
          Menu                     0x2BA395B700000101
          Subtitle                 0x298595B700000101
          Audio                    0x2B8595B700000101
          MouseKeyboard            0x299155B700000101
          SelectSpace              0x0200002c00000000
          MouseMenu                0x0200006500000000
          RightClick               0x0102000000000000
          Enter                    0x0200002800000000
          LeftClick                0x0101000000000000
          WindowsKey               0x0280000000000000
          Backspace                0x0200002A00000000
          Up                       0x0100800000000000
          Left                     0x0100008000000000
          Down                     0x01007F0000000000
          Right                    0x0100007F00000000
      end codes

end remote

```

```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = iMON-PAD
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = RightClick
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Ch-
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Ch+
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Enter
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = LeftClick
    config = Left
    repeat = 0
    delay = 0
end

```

Thank you,
   pablo

---

### Post by pablo79 on 2009-09-23
Dear guys, it works :P:P:P:P:P
I don't know which is the difference: probably I used for the test a different version of lirc init script instead of the one I was using when irw worked and mythtv not. So when I remove the options from the start and restart daemon (I left only --device=/dev/lirc0) and restart the pc it starts to work.

Thank you, for your help.

---

