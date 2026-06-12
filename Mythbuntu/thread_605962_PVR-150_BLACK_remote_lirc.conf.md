---
title: "PVR-150 BLACK remote lirc.conf"
date: 2007-11-07
forum: Mythbuntu
---

### Post by bcr821 on 2007-11-07
So i've got MythTV working on Gutsy and i'm pretty sure that live tv works fine (i'm assuming since i don't have cable and it's not for me.)

My problem lies in that i cannot get the remote to work.  When i setup LIRC i select the correct Hauppauge option and everything seems to work.  However when i run irw and push buttons on the remote, nothing happens.  I know that the remote works and the computer is receiving the IR signals because when i run "cat /dev/lirc0" i get a bunch of jibberish when i push buttons.

I've also been researching to find out that there are apparently 3 different versions of the remote that shipped with the PVR-150 kit, a grey one, a silver one, and a black one.  I found a llirc.conf for the "silver" remote [here]("http://www.pjd.nu/lirc/lircd_pvr150.conf") but it doesn't work with my remote.  How would i go about making my own lirc.conf or finding a working one for my remote?

---

### Post by superm1 on 2007-11-07
The important thing to do is to try

```
irw
```

And see if those button presses are seen.  If they are, then you need to regenerate/modify your ~/.lircrc and ~/.mythtv/lircrc.

If there is an issue with not seeing stuff from irw, you'll need to find a functional lircd.conf to replace /etc/lirc/lircd.conf with.  Please file a bug against lirc then and include as many details as you can about the remote.

If the issue is the lircrc, then please file a bug against mythbuntu-lirc-generator with the lircrc that you end up using.

---

### Post by bcr821 on 2007-11-08
> **superm1 said:**
> The important thing to do is to try

```
irw
```

And see if those button presses are seen.  If they are, then you need to regenerate/modify your ~/.lircrc and ~/.mythtv/lircrc.

If there is an issue with not seeing stuff from irw, you'll need to find a functional lircd.conf to replace /etc/lirc/lircd.conf with.  Please file a bug against lirc then and include as many details as you can about the remote.

If the issue is the lircrc, then please file a bug against mythbuntu-lirc-generator with the lircrc that you end up using.

that's what i'm saying.  My lirc.conf doesn't work.  Nothing shows up when i do "irw"

how do i go about getting a working lirc.conf

---

### Post by superm1 on 2007-11-08
> **bcr821 said:**
> that's what i'm saying.  My lirc.conf doesn't work.  Nothing shows up when i do "irw"

how do i go about getting a working lirc.conf

There is no such file lirc.conf.  There is an /etc/lirc/lircd.conf that stores remote information.  You are welcome to replace it with another lircd.conf that you can find online.  If you can't find one, then you can record a new one (and submit it back to benefit others).

---

### Post by bcr821 on 2007-11-08
> **superm1 said:**
> There is no such file lirc.conf.  There is an /etc/lirc/lircd.conf that stores remote information.  You are welcome to replace it with another lircd.conf that you can find online.  If you can't find one, then you can record a new one (and submit it back to benefit others).

where can i find those conf files?

also, my conf file is located at /etc/lircd.conf as suggested [here]("http://www.lirc.org/html/configure.html") and [here]("http://www.mythtv.org/wiki/index.php/PVR150_Remote").  Am i doing something wrong?  Does the llircd.conf not go there?

---

### Post by superm1 on 2007-11-08
> **bcr821 said:**
> where can i find those conf files?

also, my conf file is located at /etc/lircd.conf as suggested [here]("http://www.lirc.org/html/configure.html") and [here]("http://www.mythtv.org/wiki/index.php/PVR150_Remote").  Am i doing something wrong?  Does the llircd.conf not go there?
Ubuntu and debian **don't** store the file in **/etc/lircd.conf.**

A preshipped **/etc/lirc/lircd.conf** comes with the system.  If it doesn't work, then feel free to try another one.

---

### Post by bcr821 on 2007-11-08
So i'm starting to get very frustrated with this remote setup thing.  I can't seem to find a working lircd.conf to configure the remote so i tried to record my own.  This seems to fail too.
```

sudo irrecord -d /dev/lirc0 lircd.conf
```

only leaves me with:

```
Please enter the name for the next button (press <ENTER> to finish recording)
Up

Now hold down button "Up".
Something went wrong. Please try again. (9 retries left)

```

i have no idea what i'm doing wrong.  Although i have seemed to notice that when other people run

 ```
cat /dev/lirc0
```

they tend to get a result of some sort of hex value which in turn is what irrecord "binds" to an action.  However, the output when i run it tends to look something like:

```
home@patrick-dvr:/etc/lirc$ sudo cat /dev/lirc0
&#65533;&#65533;&#65533;
R&#65533;&#65533;&#65533;&#65533;&#65533;R&#65533;RxR&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;R&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;R&#65533;


```

i want to throw this thing out of my window lol

---

### Post by bcr821 on 2007-11-08
oh yeah

here is /etc/lirc/hardware.conf

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
DEVICE="/dev/lirc0"
MODULES="lirc_dev lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
LIRCMD_CONF=""
```


here is /etc/lircd/lircd.conf:

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

and finally here is ~/.mythtv/lircrc:

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

```

---

### Post by bcr821 on 2007-11-08
Anyone have any suggestions?

---

### Post by axelsvag on 2007-11-08
Have you tried to change 
```
DEVICE="/dev/lirc0"
MODULES="lirc_dev lirc_i2c"

```
to 
```
DEVICE="/dev/lirc1"
MODULES="lirc_dev lirc_i2c"

``` ?

---

### Post by bcr821 on 2007-11-09
> **axelsvag said:**
> Have you tried to change 
```
DEVICE="/dev/lirc0"
MODULES="lirc_dev lirc_i2c"

```
to 
```
DEVICE="/dev/lirc1"
MODULES="lirc_dev lirc_i2c"

``` ?

no becuase i know that my remote is "/dev/lirc0" because of when i run cat /dev/lirc0

---

