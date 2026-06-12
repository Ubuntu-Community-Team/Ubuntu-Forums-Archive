---
title: "[SOLVED] PVR-350 Remote worked after first install--but not since"
date: 2007-11-22
forum: Mythbuntu
---

### Post by wilberfan on 2007-11-22
I got a Hauppauge PVR-350 a few days ago, based on the recommendation of someone in a Linux IRC room...  We couldn't get MythTV running under Sidux (my other favorte distro), so we thought Mythbuntu would be a good idea.

I installed  Mythbuntu 7.10 a couple of days ago.   For the first install, I accepted the "standard" settings (or whatever they're called--the non-advanced option.)

I was very impressed when it ran "right out of the box..and was even MORE impressed when the remote worked!

This morning, I got it into my head that I might be able to get TV-out working, if I reinstalled Mythbuntu with the s-video cable connected to my video c ard, and the TV _on_ during the install.  (My thinking was that maybe the install procedure would detect the TV?)
It DID!    TV-out is working (from my nVidia GeForce 5200).  :)

However, the remote no longer works.

For the second install I selected the "advanced" option, but still selected the same "Hauppauge TV Card" option as I had in the first install.

The remote is the A415-HPG-A model. (Silver)

I'm pretty sure the remote itself is working.  I tested the batteries (fine), and I noticed that the little green light on the front of my Philips Magnavox TV flickers whenever I press any buttons on the Hauppauge remote.

Any suggestions for this MythNewbie?

---

### Post by foxbuntu on 2007-11-22
Please post a couple of things:

1) your lircd.conf
2) your .lircrc

We will need to look at these files to make sure all is well and then go from there.

---

### Post by wilberfan on 2007-11-23
> **foxbuntu said:**
> Please post a couple of things:

1) your lircd.conf
2) your .lircrc

We will need to look at these files to make sure all is well and then go from there.

Here's the lircd.conf:

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
# brand: 				Hauppauge
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

And here is the .lircrc

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

begin
    remote = Hauppauge_350
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = OK
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Vol-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Up
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Vol+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Replay/SkipBackward
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Ch-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Right
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = SkipForward
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Ch+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Forward
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Left
    config = key-nav-left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = MUTE
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = VOL-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = VOL+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = CH-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = CH+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Play
    config = play_pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Vol-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Menu
    config = menu
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Vol+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Back/Exit
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Rewind
    config = seek_backward
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Forward
    config = seek_forward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Play
    config = play_pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Volume-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Menu
    config = menu
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Up
    config = up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Volume+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Down
    config = down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Right
    config = right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = FastRwd
    config = seek_backward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = FastFwd
    config = seek_forward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Left
    config = left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Play
    config = play_pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Vol-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Menu/i
    config = menu
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Up
    config = up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Vol+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Down
    config = down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Right
    config = right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Back/Exit
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Rewind
    config = seek_backward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Forward
    config = seek_forward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Left
    config = left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = totem
    button = MUTE
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = totem
    button = VOL-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = totem
    button = VOL+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Ok
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Vol-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Menu
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Rewind
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Vol+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Back/Exit
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Forward
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Right
    config = move_right_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Ok
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Volume-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Menu
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = FastRwd
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Up
    config = move_up_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Volume+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Down
    config = move_down_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = FastFwd
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Left
    config = move_left_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Right
    config = move_right_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = OK
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Vol-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Menu/i
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Rewind
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Up
    config = move_up_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Vol+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Down
    config = move_down_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Back/Exit
    config = close_key
    repeat = 0
    delay = 0
end

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

Thanks for your help!  :)

---

### Post by axelsvag on 2007-11-23
Does the irw command give any response?

---

### Post by wilberfan on 2007-11-23
> **axelsvag said:**
> Does the irw command give any response?

It does if you crawl under the desk and ***re-seat the sensor!***

](*,)   #-o

An old friend used to say [something]("http://en.wikipedia.org/wiki/Never_mind") in situations like this.

My next task is to learn how to fine-tune the functionality of all those keys!  :=P~

---

### Post by superm1 on 2007-11-23
Please file a bug with your resultant lircrc against mythbuntu-lirc-generator after you have tuned, so we can adjust it to produce output closer to what is ideal.

---

### Post by axelsvag on 2007-11-24
> **wilberfan said:**
> It does if you crawl under the desk and ***re-seat the sensor!***

](*,)   #-o

An old friend used to say [something]("http://en.wikipedia.org/wiki/Never_mind") in situations like this.

My next task is to learn how to fine-tune the functionality of all those keys!  :=P~


Do you mean that my suggestion was to simple? 
What I meant was if you use the terminal and put the irw command in what answer do you get?

---

### Post by wilberfan on 2007-11-24
> **axelsvag said:**
> Do you mean that my suggestion was to simple? 
What I meant was if you use the terminal and put the irw command in what answer do you get?

No, I tried your suggestion--but got NO response in the 'irw' command.  That's what made me think, "Hmmm...the remote is working--but signals aren't getting to the computer...".   *That's* what made me think it might not be seating properly...

So your suggestion triggered the solution...  Thank you!  :)

---

### Post by axelsvag on 2007-11-24
I and a few more have had problem with the recognition of the remote. The solution for me was to change a line in lirc/hardware.conf from lirc 0 to lirc1. But the solution don´t seem to be persistent. Sometimes after a reboot the remote is recognized as lirc0 and sometimes as lirc1 so I have change this maybe 15 times.

---

### Post by wilberfan on 2007-11-24
The problem that prompted this post was that the remote wouldn't do ANYTHING--when it had on the previous install (just the day before).   That's another reason I checked the sensor...

My problem now is that some of the buttons work correctly, but others don't perform the proper function...  I have no idea where to start on THAT one!    (Other than to replace the lircd.conf with one that has the proper numbers for the PVR-350 remote...)

---

