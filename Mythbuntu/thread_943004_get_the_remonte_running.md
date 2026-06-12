---
title: "get the remonte running"
date: 2008-10-09
forum: Mythbuntu
---

### Post by skaggapa on 2008-10-09
Hello!

Im running Mythbuntu(Hardy)
Version:
mythtv-common:
  Installerad: 0.21.0+fixes18207-0ubuntu4~hardy1
  Kandidat: 0.21.0+fixes18207-0ubuntu4~hardy1
  Versionstabell:
 *** 0.21.0+fixes18207-0ubuntu4~hardy1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
     0.21.0+fixes16838-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages

Im trying to get my remote to work. Its an windows mce remote got it with my hp laptop. I found a conf for it:
[http://lirc.sourceforge.net/remotes/mceusb/lircd.conf.mceusb](http://lirc.sourceforge.net/remotes/mceusb/lircd.conf.mceusb)

so thats not the problem. I think i have configured every thing right no. I use usb uirt as a reciever:
[http://www.usbuirt.com/](http://www.usbuirt.com/)

when i do cat /dev/ttyUSB0 i get a lot of weird symbols when i press buttons, so something is going thru.

However i cant get mythtv to react when i press buttons.

My conf files
/etc/lircd.conf
```
#
# RC-6 config file
#
# source: http://home.hccnet.nl/m.majoor/projects__remote_control.htm
#         http://home.hccnet.nl/m.majoor/pronto.pdf
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

	Blue	0x00007ba1
	Yellow	0x00007ba2
	Green	0x00007ba3
	Red	0x00007ba4
	Teletext	0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote
```

/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Custom"
REMOTE_MODULES=""
REMOTE_DRIVER="usb_uirt_raw"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/home/anders/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="-d /dev/ttyUSB0"

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



~/mythtv/lircrc
I have just added a few buttons just to see if i can get any movement

```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu

begin
	prog = mythtv
	button = Up
	repeat = 3
	config = Up
end

begin
	prog = mythtv
	button = Down
	repeat = 3
	config = Down
end
begin
	prog = mythtv
	button = Left
	repeat = 3
	config = Left
end
begin
	prog = mythtv
	button = Right
	repeat = 3
	config = Right
end

begin
	prog = mythtv
	button = Ok
	config = Return
end
```

In the frontend log i can se that the lirc init goes well, it even says that it loads .mythtv/lircrc

I have restared the lircdaemon, restarted the computer. But nothing.

Please help!

What have i missed?

cheers
Anders

---

