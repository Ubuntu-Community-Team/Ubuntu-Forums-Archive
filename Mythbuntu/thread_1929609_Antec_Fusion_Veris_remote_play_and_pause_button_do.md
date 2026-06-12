---
title: "Antec Fusion Veris remote play and pause button do not work"
date: 2012-02-22
forum: Mythbuntu
---

### Post by pcooley on 2012-02-22
Problem:
Play/Pause buttons on the Veris RM200 remote for the Antec Fusion case are not working in Mythbuntu 11.10.  However, all the other buttons are working.  I've spent a little time trying to determine the problem, but have been unsuccesful so far.  I am willing to dive deeper but I am uncertain what the next best course of action is.  I've attempted to run irw from the command-line, but I suspect with some of the modernization of the dev locations, it might not be watching the correct things (I was able to do this back in the 9.04 days).

Any hints/clues to next steps would be appreciated.  The more specific details are down below.

Distro and release:
Mythbuntu 11.10

Full version of the lirc package (eg. dpkg -l lirc*):
0.9.0-0ubuntu1

Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
Mythbuntu

Case:
Antec Fusion Veris Vendor product 15c2:0038

Remote:
Remote Veris RM200

Kernel Version (uname -a):
Linux tv 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Lircd config:
Used the mythbuntu control center to select: infrared -> usb & serial remote ... -> Soundgraph iMON Antec Veris
This had /etc/lirc/lircd.conf include /usr/share/lirc/remotes/imon/lircd.conf.imon-antec-veris plus a stock ~/.lirc/mythtv

/etc/lirc/lircd.conf

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

#Configuration for the Soundgraph iMON Antec Veris remote:
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-antec-veris"

```

/usr/share/lirc/remotes/imon/lircd.conf.imon-antec-veris
```

#
# this config file was hand-generated
# using lirc-0.8.4a (imon) on Fri Nov  7 13:55:44 2008
#
# contributed by Jarod Wilson <jarod@wilsonet.com>
#
# brand:                       Antec Veris
# model no. of remote control: RM200 (Rebadged iMon PAD)
# devices being controlled by this remote:
# 	-Antec Veris Multimedia Station Premiere
# 	-Antec Veris Multimedia Station Elite, possibly
#
# nb: most codes appear to come in with an initial keypress value, as well as
# a "this key is no longer being pressed" value, which is "key | 0x00004000"

begin remote

  name   Antec_Veris_RM200
  bits                  64
  eps                   30
  aeps                 100

  one              0     0
  zero             0     0
  gap               139998
  ignore_mask 0x0000000000000301
  min_repeat             1
  toggle_bit             0

      begin codes
          KEY_EXIT                 0x2881d5b700000201 # AppExit
          KEY_POWER                0x289115b700000201 # Power
          KEY_RECORD               0x298115b700000201 # Record
          KEY_PLAY                 0x2a8115b700000201 # Play
          KEY_OPEN                 0x29b195b700000201 # Tray Open
          KEY_REWIND               0x2a8195b700000201 # Rewind
          KEY_PAUSE                0x2a9115b700000201 # Pause
          KEY_FASTFORWARD          0x2b8115b700000201 # Fast Forward
          KEY_PREVIOUS             0x2b9115b700000201 # Previous Chapter
          KEY_STOP                 0x2b9715b700000201 # Stop
          KEY_NEXT                 0x298195b700000201 # Next Chapter
          KEY_ESC                  0x0200002900000201 # Esc
          KEY_EJECTCD              0x299395b700000201 # Eject
          AppLauncher              0x29b715b700000201 # App. Launcher
          Go                       0x2ab195b700000201 # Go
          TaskSwitcher             0x2a9395b700000201 # Task Switcher
          KEY_MUTE                 0x2b9595b700000201 # Mute
          KEY_VOLUMEUP             0x28a395b700000201 # VOL +
          KEY_VOLUMEDOWN           0x28a595b700000201 # VOL -
          KEY_CHANNELUP            0x289395b700000201 # CH +
          KEY_CHANNELDOWN          0x288795b700000201 # CH -
          Timer                    0x2b8395b700000201 # Timer
          KEY_1                    0x0200001e00000201 # 1
          KEY_2                    0x0200001f00000201 # 2
          KEY_3                    0x0200002000000201 # 3
          KEY_4                    0x0200002100000201 # 4
          KEY_5                    0x0200002200000201 # 5
          KEY_6                    0x0200002300000201 # 6
          KEY_7                    0x0200002400000201 # 7
          KEY_8                    0x0200002500000201 # 8
          KEY_9                    0x0200002600000201 # 9
          KEY_0                    0x0200002700000201 # 0
          Star                     0x0220002500000201 # *
          Hash                     0x0220002000000201 # #
          KEY_VIDEO                0x2b8515b700000201 # Videos
          KEY_AUDIO                0x299195b700000201 # Music
          KEY_PHOTO                0x2ba115b700000201 # Pictures
          KEY_TV                   0x28a515b700000201 # TV
          KEY_BOOKMARKS            0x288515b700000201 # Bookmark
          Thumbnail                0x2ab715b700000201 # Thumbnail
          Zoom                     0x29a595b700000201 # Zoom
          FullScreen               0x2aa395b700000201 # Full Screen
          KEY_DVD                  0x29a395b700000201 # DVD
          KEY_DVD                  0x29a295b700000201 # DVD, version 2
          KEY_MENU                 0x2ba395b700000201 # Menu
          KEY_MENU                 0x2ba385b700000201 # Menu, version 2
          Subtitle                 0x298595b700000201 # Subtitle
          KEY_LANGUAGE             0x2b8595b700000201 # Audio
          MouseKeyboard            0x299115b700000201 # Mouse/Keyboard
# MouseKeyboard also spews 0100007f between press and release...
          KEY_BACKSPACE            0x0200002a00000201 # Backspace
          KEY_SELECT               0x0200002c00000201 # Select/Space
# SelectSpace also spews 2b9115b7 and 289115b7 between press and release...
          LeftMenu                 0x0280000000000201 # Left Menu
          RightMenu                0x0200006500000201 # Right Menu
          BTN_LEFT                 0x0101000000000201 # L. Click
          BTN_LEFT                 0x0101008000000201 # L. Click, version 2
# LeftClick flips to 01010001 when held
          BTN_RIGHT                0x0102000000000201 # R. Click
          BTN_RIGHT                0x0102008000000201 # R. Click, version 2
# Un-click for both right and left is 01000000
          KEY_ENTER                0x0200002800000201 # ENTER
# Un-click for all 0x02foo buttons is 02000000
          KEY_UP                   0x0100800000000201 # Pad Up
          KEY_DOWN                 0x01007f0000000201 # Pad Down
          KEY_LEFT                 0x0100008000000201 # Pad Left
          KEY_RIGHT                0x0100007f00000201 # Pad Right
      end codes

end remote

#
# this config file was hand-generated
# using lirc-0.8.4a (imon) on Fri Nov  7 13:55:44 2008
#
# contributed by Jarod Wilson <jarod@wilsonet.com>
#
# brand:                       Antec Veris
# model no. of remote control: Multimedia Station Premiere Front Panel
# devices being controlled by this remote:
# 	-Antec Veris Multimedia Station Premiere
#

begin remote

  name   Antec_Veris_Premiere
  bits                  64
  eps                   30
  aeps                 100

  one              0     0
  zero             0     0
  gap               139998
  ignore_mask 0x0000000000000301
  min_repeat             1
  toggle_bit             0

      begin codes
# Front Panel Buttons
          Go                       0x000000000f0002ee # Go
          KEY_AUDIO                0x000000001f0002ee # Music
          KEY_VIDEO                0x00000000200002ee # Videos
          KEY_PHOTO                0x00000000210002ee # Pictures
          KEY_DVD                  0x00000000270002ee # DVD
#          KEY_TV                   gack. mine doesn't send *anything*, might be busted
          KEY_PREVIOUS             0x00000000050002ee # Prev
          KEY_REWIND               0x00000000070002ee # Rewind
          KEY_STOP                 0x00000000040002ee # Stop
          KEY_PLAYPAUSE            0x000000003c0002ee # Play/Pause
          KEY_FASTFORWARD          0x00000000080002ee # F.Fwd
          KEY_NEXT                 0x00000000060002ee # Next
          KEY_RIGHT                0x00000001000002ee # Navigation Clockwise
          KEY_LEFT                 0x00000100000002ee # Navigation Counter-Clockwise
          KEY_SELECT               0x000000003d0002ee # Navigation Knob Push
          KEY_VOLUMEUP             0x00010000000002ee # Volume Up (CW)
          KEY_VOLUMEDOWN           0x01000000000002ee # Volume Down (CCW)
          KEY_MUTE                 0x00000000010002ee # Mute (Volume Knob Push)
      end codes

end remote
#
# this config file was hand-generated
# using lirc-0.8.5-CVS (imon) on Wed Jan 14 2009
#
# contributed by Michel Quercia <michel.quercia|prepas.org>
#
# brand:                       Antec Veris
# model no. of remote control: RM100 (Rebadged iMon PAD)
# devices being controlled by this remote:
# 	-Antec Veris Fusion 350
#
# nb: most codes appear to come in with an initial keypress value, as well as
# a "this key is no longer being pressed" value, which is "key | 0x00004000"

begin remote

  name   Antec_Veris_RM100
  bits                  64
  eps                   30
  aeps                 100

  one              0     0
  zero             0     0
  gap               139998
  ignore_mask 0x0000000000000301
  min_repeat             1
  toggle_bit             0

      begin codes
          KEY_EXIT                 0x288195b700000101 # AppExit
          KEY_POWER                0x289115b700000101 # Power
          KEY_BACKSPACE            0x0200002a00000000 # Backspace
          KEY_UP                   0x2aa515b700000101 # Pad Up
          RightMenu                0x0200006500000000 # Right Menu
          KEY_LEFT                 0x29a515b700000101 # Pad Left
          KEY_ENTER                0x0200002800000000 # ENTER
          KEY_RIGHT                0x2ba515b700000101 # Pad Right
          KEY_VOLUMEUP             0x28a395b700000101 # VOL +
          KEY_DOWN                 0x289515b700000101 # Pad Down
          KEY_CHANNELUP            0x289395b700000101 # CH +
          KEY_VOLUMEDOWN           0x28a595b700000101 # VOL -
          KEY_MUTE                 0x2b9595b700000101 # Mute
          KEY_CHANNELDOWN          0x288795b700000101 # CH -
          KEY_REWIND               0x298315b700000101 # Rewind
          KEY_PLAY                 0x2a8315b700000101 # Play
          KEY_FASTFORWARD          0x2b8315b700000101 # Fast Forward
          Go                       0x2ab195b700000101 # Go
      end codes

end remote

```

~/.lirc/mythtv
```

# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox, John Baab
# Created for use with Mythbuntu
begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = Go
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_PREVIOUS
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_PLAYPAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_FASTFORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_NEXT
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_SELECT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_Premiere
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_EXIT
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_BACKSPACE
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = RightMenu
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = KEY_FASTFORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM100
    prog = mythtv
    button = Go
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_EXIT
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_FASTFORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_PREVIOUS
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_NEXT
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_ESC
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = AppLauncher
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = Go
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = TaskSwitcher
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = Hash
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_BOOKMARKS
    config = C
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = Zoom
    config = W
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = FullScreen
    config = F
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = Subtitle
    config = T
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_BACKSPACE
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_SELECT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = LeftMenu
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = RightMenu
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Antec_Veris_RM200
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 0
    delay = 0
end

```

---

### Post by the_plumber on 2012-03-22
I have a very nearly identical system as yours, the only difference being in the version of Linux (uname -a -> Linux Blake 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686 athlon i386 GNU/Linux). I have the same symptoms as you. Did you get a fix? And if so, what were the steps to implement the fix?

I also have serious sensitivity problems with the RM200 since getting it to work properly. If I run irw, I see individual, well defined key presses with no multiples unless I hold the key down, but on MythTV, one press jumps two choices on the top menu. Since there is an even number of menu choices, I have to resort to the keyboard

I'd welcome any suggestions

---

### Post by regiss on 2012-04-03
Same issue for me is there any other tool similar to irw to detect which buttons are not picked up by default?
Half of my buttons are OK but play pause etc are not detected through irw

---

