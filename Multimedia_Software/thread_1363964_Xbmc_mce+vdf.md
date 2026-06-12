---
title: "Xbmc mce+vdf"
date: 2009-12-25
forum: Multimedia Software
---

### Post by mofd on 2009-12-25
Hi, i'm currently running XBMC liveCD installed on harddisk.
I have installed LIRC and LCDPROC for my remote and display.
 
(i'm running all the latest editions, installed with apt-get)
 
os: ubuntu karmic 9.11
hardware: antec remote black with display 15c2:0038 
 
lirc+LCDd daemons start succesfull.
I have a extra MCE IR USB receiver plugged in, with a harmony 555 with MCEUSB2 layout.
 
My receiver works fine with the following config:
 
/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remote"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""
#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
#Enable lircd
START_LIRCD="true"
#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"
#Try to load appropriate kernel modules
LOAD_MODULES="true"
# Default configuration files for your hardware if any
LIRCMD_CONF="/etc/lirc/lircd.conf"
#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user inputlircd.conf

```

/etc/lirc/lircd.conf
```

begin remote
name mceusb
bits 16
flags RC6|CONST_LENGTH
eps 30
aeps 100
header 2667 889
one 444 444
zero 444 444
pre_data_bits 21
pre_data 0x37FF0
gap 105000
toggle_bit 22
rc6_mask 0x100000000
&#12288;
begin codes
#unused by HP remote
Blue 0x00007ba1
Yellow 0x00007ba2
Green 0x00007ba3
Red 0x00007ba4
Teletext 0x00007ba5
#ba6 - bae unused 
BA6 0x00007ba6
BA7 0x00007ba7
BA8 0x00007ba8
BA9 0x00007ba9
BAA 0x00007baa
BAB 0x00007bab
BAC 0x00007bac
BAD 0x00007bad
BAE 0x00007bae
Radio 0x00007baf
Print 0x00007bb1
#bb2 - bb4 unused 
BB2 0x00007bb2
BB3 0x00007bb3
BB4 0x00007bb4
Videos 0x00007bb5
Pictures 0x00007bb6
RecTV 0x00007bb7
Music 0x00007bb8
TV 0x00007bb9
#bba - bbf unused 
BBA 0x00007bba
BBB 0x00007bbb
BBC 0x00007bbc
BBD 0x00007bbd
BBE 0x00007bbe
BBF 0x00007bbf
#bc1 - bca unused 
BC1 0x00007bc1
BC2 0x00007bc2
BC3 0x00007bc3
BC4 0x00007bc4
BC5 0x00007bc5
BC6 0x00007bc6
BC7 0x00007bc7
BC8 0x00007bc8
BC9 0x00007bc9
BCA 0x00007bca
Eject 0x00007bcb
SlideShow 0x00007bcc
Visualization 0x00007bcd
#bce - bcf unused 
BCE 0x00007bce
BCF 0x00007bcf
#bd1 - bd7 unused 
BD1 0x00007bd1
BD2 0x00007bd2
BD3 0x00007bd3
BD4 0x00007bd4
BD5 0x00007bd5
BD6 0x00007bd6
BD7 0x00007bd7
Aspect 0x00007bd8
Guide 0x00007bd9
LiveTV 0x00007bda
DVD 0x00007bdb
#NoGap
Back 0x00007bdc
OK 0x00007bdd
Right 0x00007bde
Left 0x00007bdf
Down 0x00007be0
Up 0x00007be1
#NoGap
Star 0x00007be2
Hash 0x00007be3
#NoGap
Replay 0x00007be4
Skip 0x00007be5
Stop 0x00007be6
Pause 0x00007be7
Record 0x00007be8
Play 0x00007be9
Rewind 0x00007bea
Forward 0x00007beb
#NoGap
ChanDown 0x00007bec
ChanUp 0x00007bed
VolDown 0x00007bee
VolUp 0x00007bef
#NoGap
More 0x00007bf0
Mute 0x00007bf1
Home 0x00007bf2
Power 0x00007bf3
#NoGap
Enter 0x00007bf4
Clear 0x00007bf5
#NoGap
Nine 0x00007bf6
Eight 0x00007bf7
Seven 0x00007bf8
Six 0x00007bf9
Five 0x00007bfa
Four 0x00007bfb
Three 0x00007bfc
Two 0x00007bfd
One 0x00007bfe
Zero 0x00007bff
end codes
end remote

```
 
Display is not working. My problem is when i load the kernel modules with modprobe, the LCD starts working, but the remote stops working. Here is my /etc/modules:
 
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
loop
lp
#lirc_imon
lirc_mceusb
lirc_dev
lirc_mceusb2

```
 
--> when I remove the # form lirc_imon, and I reboot the machine, my LCD works fine and remote stop working. When i add # again in front of lirc_imon, the LCD stops working and the remote works again.
What am I doing wrong?
 
Thanks for any help

---

### Post by mofd on 2009-12-25
BTW, I'm using XBMC camelot with:
 
LIRC 0.8.6-0ubuntu2
LCDPROC 0.5.3-0ubuntu1

---

### Post by mofd on 2009-12-27
*bump*

---

