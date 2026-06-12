---
title: "[SOLVED] PVR-350 remote not working."
date: 2007-10-13
forum: Mythbuntu
---

### Post by MCGrunge on 2007-10-13
Hello, I recently attempted my first Mythbuntu install.  (I used the newest Release Candidate iso.)  Everything went smoothly, except my remote doesn't seem to work.  I chose the "Hauppauge TV card" remote during setup.  I've searched the forums here and noticed that others are having trouble getting this series of cards to work with the remote.  Is there any resolution to this?

---

### Post by stevetv on 2007-10-13
i dont know... but i guess the first thing to do is to ensure lirc is working.

type this into a terminal
```

/usr/bin/irw

```

and then press some buttons on your remote.  you should get some output lines.  for example this is from mine.  (press ctrl c to make it stop)

```

steve@myth:/var/log$ /usr/bin/irw
00000000000028d1 00 LEFT Streamzap_PC_Remote
00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
00000000000028d1 01 LEFT Streamzap_PC_Remote
00000000000028d1 00 LEFT Streamzap_PC_Remote
00000000000028d1 01 LEFT Streamzap_PC_Remote

```

if you don't get anything.. lirc isnt working.. which should be easy fixed.  if it does output as below, please post your lircrc file, its located in /home/mythtv/.mythtv/

and your lirc.conf

---

### Post by MCGrunge on 2007-10-14
Thanks for the reply.  After executing the command, nothing happens until I press CTRL-C, then I get my prompt back.  I tried a simple "sudo apt-get install lirc" and it responds with "lirc is already the newest version."

---

### Post by laga on 2007-10-14
As stated by stevetv:

> if you don't get anything.. lirc isnt working.. which should be easy fixed. if it does output as below, please post your lircrc file, its located in /home/mythtv/.mythtv/

and your lirc.conf

Please post those.

---

### Post by dawson64 on 2007-10-15
I'm having the same problem with the same setup of mythbuntu RC.
irw does not return anything.  I choose Hauppauge TV for a remote during install & during an update that was applied when I updated the system.  

here is /etc/lirc/hardware.conf:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.

DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
LIRCMD_CONF=""

```

here is /etc/lirc/lircd.conf:
```
#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by
#
# brand:                                Hauppauge
# model no. of remote control:
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
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
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


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
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg www.lugv.at
#
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote

```

& here is ~/.mythtv/lircrc
it's reallly long..........  I skipped about 50 entries to get to the bottom
```
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ok
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Channel-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Channel+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = FastRwd
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = FastFwd
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Volume-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Volume+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Ok
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = SkipForward
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Replay/SkipBackward
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Menu/i
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch-
    config = PgDown
    repeat = 0
    delay = 0
end
begin
    remote = Hauppauge_350
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = CH-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = CH+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = VOL-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = VOL+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Ok
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Vol-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Skip
    config = seek +15 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Vol+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Replay
    config = seek -15 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Rewind
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Forward
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Ok
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Volume-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Up
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Volume+
    config = volume +1
    repeat = 0
    delay = 0
end
begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Down
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Right
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = FastRwd
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = FastFwd
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Left
    config = seek -6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = OK
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Vol-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = SkipForward
    config = seek +15 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Up
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Vol+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Down
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Replay/SkipBackward
    config = seek -15 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Right
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Rewind
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Forward
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Left
    config = seek -6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mplayer
    button = MUTE
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mplayer
    button = VOL-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mplayer
    button = VOL+
    config = volume +1
    repeat = 0
    delay = 0
end
begin
    remote = hauppauge_pvr
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Ok
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Vol-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Skip
    config = EventNext
    repeat = 0
    delay = 0
end


begin
    remote = hauppauge_pvr
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Vol+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Replay
    config = EvenPrior
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Rewind
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Forward
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Ok
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Volume-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Up
    config = EventUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Volume+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Down
    config = EventDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Right
    config = EventRight
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = FastRwd
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = FastFwd
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Left
    config = EventLeft
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = OK
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Vol-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = SkipForward
    config = EventNext
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Up
    config = EventUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Vol+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Down
    config = EventDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Replay/SkipBackward
    config = EvenPrior
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Right
    config = EventRight
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Rewind
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Forward
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Left
    config = EventLeft
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = xine
    button = MUTE
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = xine
    button = VOL-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = xine
    button = VOL+
    config = Volume+
    repeat = 0
    delay = 0
end
begin
    remote = hauppauge_pvr
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ok
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Vol-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end
begin
    remote = hauppauge_pvr
    prog = vlc
    button = Vol+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Replay
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ch-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Skip
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ch+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end
begin
    remote = hauppauge_pvr
    prog = vlc
    button = Forward
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Down
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Ok
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Volume-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Up
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Volume+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Channel-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Right
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Channel+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = FastRwd
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = FastFwd
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Left
    config = key-nav-left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Down
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

.....................................................
.....................................................


begin
    remote = Hauppauge_350
    prog = elisa
    button = Forward
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Left
    config = move_left_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = elisa
    button = MUTE
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = elisa
    button = VOL-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = elisa
    button = VOL+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

```

---

### Post by superm1 on 2007-10-16
Okay, so second thing to check here.

```
dmesg | grep lirc
```

Find out whether these modules are even loading.

---

### Post by stevetv on 2007-10-16
ive never had a hauppauge card. .. but i believe they have shipped at least 3 remotes with the pvr350. black, grey and silver.  

superm1, not that this would prevent the modules from loading but is it possible that the lirc.conf file posted by dawson64 contains data for all of the remotes?  and that dawson64 will need to delete everything else from the file except that pertaining to their specific remote?

for example.. dawson64.. if you have the silver remote, maybe try just this (i just deleted everything that wasnt relating to A415-HPG).

if you have a different remote to the silver one, you'd need to cut everything except "something else" .. if that makes sense.


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

also.. you'd certainly need to edit your key's to suit your tastes.

---

### Post by superm1 on 2007-10-16
> **stevetv said:**
> ive never had a hauppauge card. .. but i believe they have shipped at least 3 remotes with the pvr350. black, grey and silver.  

superm1, not that this would prevent the modules from loading but is it possible that the lirc.conf file posted by dawson64 contains data for all of the remotes?  and that dawson64 will need to delete everything else from the file except that pertaining to their specific remote?

for example.. dawson64.. if you have the silver remote, maybe try just this (i just deleted everything that wasnt relating to A415-HPG).

if you have a different remote to the silver one, you'd need to cut everything except "something else" .. if that makes sense.


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

```also.. you'd certainly need to edit your key's to suit your tastes.
Steve,

Actually lirc allows you to define as many remotes as you want in your lircd.conf.  For years I was accumulating more and more remotes in mine as i'd move across to different receivers and remote controls and blasters.

Mythbuntu-lirc-generator (and mythbuntu-control-centre) go through and generate application specific bindings for each remote.  

When using irw, it listens for any remote that is listed in that lircd.conf.

---

### Post by dawson64 on 2007-10-16
> **superm1 said:**
> Okay, so second thing to check here.

```
dmesg | grep lirc
```

Find out whether these modules are even loading.

It looks like it is loading
```
[   60.029954] lirc_dev: IR Remote Control driver registered, at major 61
[   60.226560] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[   60.226996] lirc_dev: lirc_register_plugin: sample_rate: 10

```

---

### Post by superm1 on 2007-10-17
> **dawson64 said:**
> It looks like it is loading
```
[   60.029954] lirc_dev: IR Remote Control driver registered, at major 61
[   60.226560] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[   60.226996] lirc_dev: lirc_register_plugin: sample_rate: 10

```
Well if it's loading for you, does irw work for you?  Have you tried?

---

### Post by dawson64 on 2007-10-18
> **superm1 said:**
> Well if it's loading for you, does irw work for you?  Have you tried?

I just tried again and I'm not getting anything.  I tried a second cable that I have (I think it's got the blaster on it because it lights up?) and that didn't help.

---

### Post by wppaas on 2007-10-18
This might be too obvious but is the lircd daemon running?

Could you post the output of the following commands

ps -eaf | grep lircd
ls -la /dev/lirc0
ls -la /dev/lircd
ls -la /usr/bin/irw
lsmod | grep lirc

---

### Post by dawson64 on 2007-10-18
> **wppaas said:**
> This might be too obvious but is the lircd daemon running?

Could you post the output of the following commands

ps -eaf | grep lircd
ls -la /dev/lirc0
ls -la /dev/lircd
ls -la /usr/bin/irw
lsmod | grep lirc

Here is the output of the commands you asked. I know the remote works because I've trained the buttons to another remote.

```
~$ ps -eaf | grep lircd
root      5320     1  0 Oct15 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0
robb      9011  8992  0 16:52 pts/0    00:00:00 grep lircd

```

```
~$ ls -la /dev/lirc0
crw-rw---- 1 root root 61, 0 2007-10-15 18:25 /dev/lirc0

```

```
~$ ls -la /dev/lircd
srw-rw-rw- 1 root root 0 2007-10-15 18:25 /dev/lircd

```

```
~$ ls -la /usr/bin/irw
-rwxr-xr-x 1 root root 4420 2007-10-13 01:15 /usr/bin/irw

```

```
~$ lsmod | grep lirc
lirc_i2c               11268  2
lirc_dev               15860  1 lirc_i2c
i2c_core               26112  11 cx88xx,bttv,lirc_i2c,msp3400,saa7127,saa7115,tuner,i2c_viapro,ivtv,i2c_algo_bit,tveeprom

```

---

### Post by wppaas on 2007-10-19
@dawson64
That looks ok.

What happens if you run

sudo mode2 -d /dev/lirc0

and try the remote?

---

### Post by dawson64 on 2007-10-19
> **wppaas said:**
> @dawson64
That looks ok.

What happens if you run

mode2 -d /dev/lirc0

and try the remote?

i tried running this while ssh'd into the box
```
@mythtv:~$ sudo mode2 -d /dev/lirc0
mode2: error opening /dev/lirc0
mode2: Device or resource busy

```

---

### Post by apauna on 2007-10-21
What remote do you have? Open the battery cover and reply with the label that is in there. I have a pvr-350 and it has been working fine, so I wonder if we can compare settings if we have the same remote. My model # is A415-HPG.

I may have missed this, but has this remote ever worked in the past? How old are the batteries?

Maybe it is a dead remote since it does not indicate when sending signals. One way to test it is to use a universal learning remote and try and learn a button from the Hauppauge remote. My learning remote tells my via a led when it is getting a signal from the other remote.

Hope this helps!

---

### Post by dawson64 on 2007-10-21
> **apauna said:**
> What remote do you have? Open the battery cover and reply with the label that is in there. I have a pvr-350 and it has been working fine, so I wonder if we can compare settings if we have the same remote. My model # is A415-HPG.

I may have missed this, but has this remote ever worked in the past? How old are the batteries?

Maybe it is a dead remote since it does not indicate when sending signals. One way to test it is to use a universal learning remote and try and learn a button from the Hauppauge remote. My learning remote tells my via a led when it is getting a signal from the other remote.

Hope this helps!

Good questions
I've got the A415-HPG-WE.  I'm not sure what is different. 
I've never got it working, I've contacted hauppauge and they have sent me a new cable (one with an receiver & an LED on another end) so I've got 2 cables now.  That didn't help so they exchanged PVR-350's because it didn't work under windows either.  I haven't tried the new card under windows yet.

The batteries are from when i bought the remote back in December. The batteries both read 1.5V.
I trained a learning remote to use some of the buttons & that showed it was being trained. The learning remote never displays anything either.

Just curious, would the receiver be able to pickup other remote signals, like the tv or stereo?

---

### Post by apauna on 2007-10-21
> **dawson64 said:**
> Good questions
I've got the A415-HPG-WE.  I'm not sure what is different. 
I've never got it working, I've contacted hauppauge and they have sent me a new cable (one with an receiver & an LED on another end) so I've got 2 cables now.  That didn't help so they exchanged PVR-350's because it didn't work under windows either.  I haven't tried the new card under windows yet.

The batteries are from when i bought the remote back in December. The batteries both read 1.5V.
I trained a learning remote to use some of the buttons & that showed it was being trained. The learning remote never displays anything either.

Just curious, would the receiver be able to pickup other remote signals, like the tv or stereo?

On your question about the receiver, it may be able to yes depends on if the frequencies the remotes transmit at are close enough to work or not. Sounds like Hauppauge sent you a special receiver that indicates when it is getting signals from the remote. As long as this is flashing it indicates that the problem is not the remote. I wonder if it has something to do with the WE as well. Maybe lirc has to be trained how to receive the signals from the new remote. I will have to research this further and get back to you.

---

### Post by wppaas on 2007-10-21
> **dawson64 said:**
> i tried running this while ssh'd into the box
```
@mythtv:~$ sudo mode2 -d /dev/lirc0
mode2: error opening /dev/lirc0
mode2: Device or resource busy

```

this is because the lircd daemon is claiming the device. First do

sudo /etc/init.d/lirc stop

and type.

sudo mode2 -d /dev/lirc0

When you press some buttons on the remote you should see some hex codes appear.

good luck, 

cheers
WP

---

### Post by dawson64 on 2007-10-21
> **wppaas said:**
> this is because the lircd daemon is claiming the device. First do

sudo /etc/init.d/lirc stop

and type.

sudo mode2 -d /dev/lirc0

When you press some buttons on the remote you should see some hex codes appear.

good luck, 

cheers
WP

It didn't return anything when i tried it this.  (No errors this time)

@apauna - the LED is always lit, it never blinks when i push buttons.  Looking at it closer it just appears to be red led.

---

### Post by wppaas on 2007-10-22
> **dawson64 said:**
> It didn't return anything when i tried it this.  (No errors this time)


oops, that's not good. This is almost definitely a hardware problem. Are you sure the remote itself is not broken?

---

### Post by dawson64 on 2007-10-22
> **wppaas said:**
> oops, that's not good. This is almost definitely a hardware problem. Are you sure the remote itself is not broken?

I emailed hauppauge back about it yesterday asking if i had the right remote.  I guess it could be broke too.  Maybe I'll push them for a new remote.  That's why i was wondering if it would detect / receive other remote's signals.

I found this but wasn't sure if was related or not [Nova-T Remote Problems]("http://g-ding.tv/?q=node/1301")

Robb

---

### Post by wppaas on 2007-10-22
> **dawson64 said:**
> I emailed hauppauge back about it yesterday asking if i had the right remote.  I guess it could be broke too.  Maybe I'll push them for a new remote.  That's why i was wondering if it would detect / receive other remote's signals.

Yes, you should try a new remote, because the IR unit on the card is correctly detected (see your dmesg output) and mode2 does not detect any incoming infrared signals.

If you want to try another remote, this is from the lirc faq

The Hauppauge remote control uses the RC-5 protocol. You should be able to use any TV remote control that uses this protocol. Common brands that use this protocol are Philips and Marantz.

Cheers
WP

---

### Post by dawson64 on 2007-11-07
I received a new cable & remote.  When I pluged the cable in the remote worked right away!  

Now I'm just tweaking the lircrc to get it to function smoother.

---

### Post by wppaas on 2007-11-10
> **dawson64 said:**
> I received a new cable & remote.  When I pluged the cable in the remote worked right away!  


Good to hear everything worked out :-)

Cheers
WP

---

