---
title: "Anyone have a working A415 Hauppauge remote?  I need the lircd.conf and lircrc..."
date: 2009-01-11
forum: Mythbuntu
---

### Post by emmiesix on 2009-01-11
Can someone with a working Hauppauge Remote (the A415 "silver" one that comes with the PVR-150) post their working lircd.conf and lircrc files?  


Technically my conf file is ok as irw command gets reasonable output, but when I load up mythbuntu livetv nothing works.  I have been ALL OVER the net trying to find out how to setup lircrc files, but all I have found are loose guidelines and then some useless advice like "tweak it to get it to work".  None of the "example" lircrc files have worked so far.

The main problem, I suspect, is that the config keywords are incorrect - i.e., The system detects that a button is pushed but doesn't send the command to mythtv.  I know also that there has to be some matching between the lircd.conf files and lircrc but I have not seen that clearly explained.  I can't find the keywoards anywhere online, unfortunately.

Finally, I can't seem to get a straight answer on where the lircrc should really be located or called (.lircrc?)



I know someone out there has to have solved this problem, the remote is so very common.  I am fairly new to linux as far as nuts-and-bolts admin goes and it is much harder than I had realized. :(

---

### Post by uMuppet on 2009-01-12
If it works with irw then it is the same as pressing the keys on the keyboard.  

Are any of the buttons on the remote working in Mythtv?
Does irw return  a result for every button?

---

### Post by dibuntux on 2009-01-12
see next...

---

### Post by dibuntux on 2009-01-12
I there, I have a HVR1110 with the same remote and, yes, it is a mess. In fact I use the one provided with my SkyStar 2.6, also not completely functional but OK.
I tried to follow the instructions on this tread but with no luck - still they provide some sort of explanation

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253085](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253085)

---

### Post by zagor on 2009-01-12
> **emmiesix said:**
> Can someone with a working Hauppauge Remote (the A415 "silver" one that comes with the PVR-150) post their working lircd.conf and lircrc files?  


If I'm not mistaken, I've taken mine from [mythdora]("http://www.wilsonet.com/mythtv/fc6myth.php#lirc"). Check at the end of the PVR-x50 paragraph. Look for the lircrc-haupgrey-g3.txt file.
I'll post the files I use on my mythbuntu 8.04.

---

### Post by BatPenguin on 2009-01-31
Hello everybody,

I have the PVR-150 with the silvery looking remote, i believe it's the same as the one you're discussing here now. I have IR blaster setup and working on it, and the file with 3 different Hauppauge remote configis referred to by my /etc/lirc/lircd.conf. The IR blaster works nicely but the remote does not... I think the issue is with my hardware.conf file and not the lircd.conf codes. What do you guys have in your hardware.conf file? Mine is pretty blank looking actually (attaching it here), considering that the transmitter part works fine, it's pretty amazing really.

I actually had this working fine under Hardy, but now in Intrepid, it's not working anymore. So please let me take a peek in your hardware.conf files and/or please help me troubleshoot this. I've been surfing the boards for an eternity and trying all sorts of things. This whole setup is pretty much based on anohter thread...it seems sound enough, but I think the hardware.conf is what breaks it. Please help. Thanks!

My files:

/etc/lirc/hardware.conf:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES="lirc_dev lirc_pvr150"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="none"
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
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""
```

My /etc/lirc/lircd.conf:```


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
#include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

include /usr/share/lirc/remotes/mycustom.conf
```

And /usr/share/lirc/remotes/mycustom.conf:
```

# My Custom configuration

# my attempt at blaster

begin remote
	name blaster
		bits 32
		flags RAW_CODES
		eps 0
		aeps 0
		plead 0
		gap 333333
		repeat_bit 0
		begin raw_codes
 name 0
    2177761280
    name 1
    2177761281
    name 2
    2177761282
    name 3
    2177761283
    name 4
    2177761284
    name 5
    2177761285
    name 6
    2177761286
    name 7
    2177761287
    name 8
    2177761288
    name 9
    2177761289
    name POWER
    2177761290
    name CH_UP
    2177761295
    name CH_DOWN
    2177761296
    name CH_PREVIOUS
    2177761299
    name AV
    2177761321
   end raw_codes

end remote


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


begin remote
  name            HVR-1100
  bits            16
  eps             30
  aeps            100
  one             0     0
  zero            0     0
  gap             135862
  pre_data_bits   16
  pre_data        0x8001

  begin codes
       Go              0x0161
       power           0x0074
       Tv              0x0179
       Videos          0x0189
       Music           0x0188
       Pictures        0x016F
       Guide           0x016D
       Radio           0x0181
       Up              0x0067
       Down            0x006C
       Left            0x0069
       Right           0x006A
       Ok              0x001C
       Back/edit       0x00AE
       Menu            0x008B
       Vol+            0x0073
       Vol-            0x0072
       PrevChan        0x019C
       Chan+           0x0192
       Chan-           0x0193
       Mute            0x0071
       Record          0x00A7
       Stop            0x0080
       replay          0x00A8
       SKip            0x00D0
       play            0x00CF
       Previous        0x00A5
       Next            0x00A3
       Pause           0x0077
       1               0x0002
       2               0x0003
       3               0x0004
       4               0x0005
       5               0x0006
       6               0x0007
       7               0x0008
       8               0x0009
       9               0x000A
       *               0x0184
       0               0x000B
       #               0x0172
       red             0x018E
       green           0x018F
       yellow          0x0190
       blue            0x0191

  end codes

end remote 
```

---

