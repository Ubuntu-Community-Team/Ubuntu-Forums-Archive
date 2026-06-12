---
title: "MythBuntu 8.04 Hauppauge PVR-150 blaster - work-around"
date: 2008-07-28
forum: Mythbuntu
---

### Post by zorglups on 2008-07-28
Hi all,

I definitely need the blaster to work and this turned into a nightmare...

I first had troubles because the lirc_pvr150 and the lirc_i2c modules were both loading while this seems not possible.
sysfs: duplicate filename 'i2c ir driver' can not be created

I finally removed anything from the *_MODULES lines in the /etc/lirc/hardware.conf except the lirc_pvr150 on the TRANSMITTER_MODULES line.

After rebooting this was still nok OK.
I have been Googling ans reading many pages but nothing helped me (so far).

The only work-around I found so far was to create a little script launched just before the lircd:
cat /etc/init.d/reset-ir 
#! /bin/sh
echo "Resetting the IR receiver/blaster"
/usr/bin/ivtvctl --reset-ir

cd /etc/rc2.d
sudo chmod 755 /etc/init.d/reset-ir 
sudo ln -s ../init.d/reset-ir S50reset-ir

This little work-around makes my PVR-150 working.

There is probably a more elegant way to do it but I counld not find it yet. In the mean time, I hope this might help some of you.

Pierre.

note: I will try to get my remote control working but ... this will be for another night ...

---

### Post by ed3120 on 2008-07-28
I've been trying to get my PVR150 IR Blaster to work with Mythbuntu for some time.  

So you just selected it and MCC and ran this script and it worked?  Is there anything else that I need to do?

---

### Post by zorglups on 2008-07-28
I really thought this would drive me crazy !!!

Well, I ran MCC and selected only the transmitter (and no remote (yet)). This will somewhat populate some files but we will overwrite them anyway.

I continued in my lirc quest. My target goal was to have working together:
1) A "Medion X10 RF 20014752" remote control.
2) A "Hauppauge PVR-150" IR blaster to pilot a STB.

I previously followed a lot of sites/FAQ/forums/HowTo... :confused:
I hope that I could extract here the needed step and that my previous trials are not having too much side effect (positive in my case :)).

You will at least need to have the PVR-150 firmware at the right place:
```

cd /lib/firmware
sudo mv haup-ir-blaster.bin haup-ir-blaster.bin.ori
sudo wget [http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin](http://www.blushingpenguin.com/mark/lmilk/haup-ir-blaster.bin)

ls -l /lib/firmware
 total 304
drwxr-xr-x 4 root root   2928 2008-07-19 00:17 2.6.24-16-generic 
drwxr-xr-x 4 root root   2888 2008-07-27 22:46 2.6.24-19-386 
drwxr-xr-x 4 root root   2928 2008-07-19 00:22 2.6.24-19-generic
-rw-r--r-- 1 root root 302355 2007-09-27 02:13 haup-ir-blaster.bin

sudo reboot
```Here are the files of interest:
/etc/lirc$ cat /etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Medion 20014752 X10 RF"
REMOTE_MODULES="lirc_dev lirc_atiusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Hauppauge PVR-150 (pci) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
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
```/etc/lirc$ cat /etc/lirc/lircd.conf
note: The blaster part is extracted from   [FONT=&quot][http://www.blushingpenguin.com/mark/lmilk/lircd.conf](http://www.blushingpenguin.com/mark/lmilk/lircd.conf)
note2: The Remote remote part was recorded with irrecord (with lircd stopped) 
[/FONT]```

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

  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
    name 1_696_KEY_0
    2193096704
    name 1_696_KEY_1
    2193096705
    name 1_696_KEY_2
    2193096706
    name 1_696_KEY_3
    2193096707
    name 1_696_KEY_4
    2193096708
    name 1_696_KEY_5
    2193096709
    name 1_696_KEY_6
    2193096710
    name 1_696_KEY_7
    2193096711
    name 1_696_KEY_8
    2193096712
    name 1_696_KEY_9
    2193096713
    name 1_696_KEY_POWER
    2193096714
    name 1_696_KEY_CH_UP
    2193096719
    name 1_696_KEY_CH_DOWN
    2193096720
    name 1_696_KEY_MUTE
    2193096721
    name 1_696_KEY_VOL_DOWN
    2193096722
    name 1_696_KEY_VOL_UP
    2193096724
    name 1_696_KEY_MNSELECT
    2193096727
    name 1_696_KEY_AV
    2193096745
    name 1_696_KEY_MENU
    2193096751
    name 1_696_KEY_MUP
    2193096752
    name 1_696_KEY_MDOWN
    2193096753
    name 1_696_KEY_MLEFT
    2193096754
    name 1_696_KEY_MRIGHT
    2193096755
    name 1_696_KEY_Sleep
    2193096767
    name 1_706_KEY_0
    2193752064
    name 1_706_KEY_1
    2193752065
    name 1_706_KEY_2
    2193752066
    name 1_706_KEY_3
    2193752067
    name 1_706_KEY_4
    2193752068
    name 1_706_KEY_5
    2193752069
    name 1_706_KEY_6
    2193752070
    name 1_706_KEY_7
    2193752071
    name 1_706_KEY_8
    2193752072
    name 1_706_KEY_9
    2193752073
    name 1_706_KEY_POWER
    2193752074
    name 1_706_KEY_CH_UP
    2193752079
    name 1_706_KEY_CH_DOWN
    2193752080
    name 1_706_KEY_MUTE
    2193752081
    name 1_706_KEY_VOL_DOWN
    2193752082
    name 1_706_CH_PREVIOUS
    2193752083
    name 1_706_KEY_VOL_UP
    2193752084
    name 1_706_KEY_MNSELECT
    2193752087
    name 1_706_KEY_EXIT
    2193752088
    name 1_706_KEY_GUIDE
    2193752091
    name 1_706_KEY_MNRETRUN
    2193752096
    name 1_706_KEY_BLUE
    2193752099
    name 1_706_KEY_GREEN
    2193752100
    name 1_706_KEY_RED
    2193752101
    name 1_706_KEY_YELLOW
    2193752102
    name 1_706_KEY_MENU
    2193752111
    name 1_706_KEY_MUP
    2193752112
    name 1_706_KEY_MDOWN
    2193752113
    name 1_706_KEY_MLEFT
    2193752114
    name 1_706_KEY_MRIGHT
    2193752115
    name 1_706_KEY_DSubtitle
    2193752132
    name 1_706_KEY_On
    2193752141
  end raw_codes
end remote

#gap          211998
#min_repeat      6
#toggle_bit_mask 0x310F0000 
begin remote

  name  Medion_20014752
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap           235923
  toggle_bit      0

      begin codes
          TV                       0x012C
          VCR                      0x022D
          DVD                      0xD904
          MUSIC                    0xDB06
          RADIO                    0x032E
          PHOTO                    0xDA05
          TV_PREVIEW               0x042F
          CHANNEL_LIST             0x0530
          SETUP                    0xF01B
          VIDEO_DESKTOP            0x0631
          CHAN+                    0xE00B
          CHAN-                    0xE10C
          VOL+                     0xDE09
          VOL-                     0xDD08
          MUTE                     0xD500
          RED                      0x0732
          GREEN                    0x0833
          YELLOW                   0x0934
          BLUE                     0x0A35
          TXT                      0xEB16
          1                        0xE20D
          2                        0xE30E
          3                        0xE40F
          4                        0xE510
          5                        0xE611
          6                        0xE712
          7                        0xE813
          8                        0xE914
          9                        0xEA15
          0                        0xEC17
          TV_RADIO                 0xF11C
          BACK                     0xF520
          RENAME                   0x0B36
          SNAPSHOT                 0xED18
          UP                       0xEF1A
          DOWN                     0xF722
          LEFT                     0xF21D
          RIGHT                    0xF41F
          OK                       0xF31E
          ACQUIRE_IMAGE            0x0C37
          EDIT_IMAGE               0x0D38
          REWIND                   0xF924
          PLAY                     0xFA25
          FORWARD                  0xFB26
          RECORD                   0xFC27
          STOP                     0xFD28
          PAUSE                    0xFE29
          PREVIOUS                 0xF621
          FULL_SCREEN              0x0E39
          NEXT                     0xF823
          DVD_MENU                 0xEE19
          DVD_AUDIO                0x0F3A
          POWER                    0xD702
      end codes

end remote
```Nothing special in /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

```/etc/init.d/reset-ir 
```

#! /bin/sh
echo "Resetting the IR receiver/blaster"
/usr/bin/ivtvctl --reset-ir

```rc2.d script
```

cd /etc/rc2.d
sudo chmod 755 /etc/init.d/reset-ir 
sudo ln -s ../init.d/reset-ir S50reset-ir

```Complete power off - power on...

Now, my system shows:
```

phil@doit:/etc/lirc$ ls -l /dev/lir*
crw-rw---- 1 root root 61, 0 2008-07-29 00:54 /dev/lirc0
crw-rw---- 1 root root 61, 1 2008-07-29 00:54 /dev/lirc1
srw-rw-rw- 1 root root     0 2008-07-29 00:54 /dev/lircd
srw-rw-rw- 1 root root     0 2008-07-29 00:54 /dev/lircd1
prw-r--r-- 1 root root     0 2008-07-29 00:54 /dev/lircm

phil@doit:/etc/lirc$ ps -ef | grep lirc
root      5224     2  0 00:54 ?        00:00:00 [lirc_pvr150]
root      5267     1  0 00:54 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0 --output=/dev/lircd --listen
root      5274     1  0 00:54 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc1 --output=/dev/lircd1 --connect=localhost 8765 --pidfile=/var/run/lircd1.pid
root      5278     1  0 00:54 ?        00:00:00 /usr/sbin/lircmd

```And I can make the blaster flash:
```

phil@doit:/etc/lirc$ sudo irsend -d /dev/lircd1 SEND_ONCE blaster 1_696_KEY_POWER

```And I can receive codes from my Medion remote:
```

phil@doit:/etc/lirc$ irw
00000014e00b0000 00 CHAN+ Medion_20014752
00000014e00b0000 01 CHAN+ Medion_20014752
00000014e10c0000 00 CHAN- Medion_20014752
00000014e10c0000 01 CHAN- Medion_20014752
00000014dd080000 00 VOL- Medion_20014752
00000014dd080000 01 VOL- Medion_20014752
00000014de090000 00 VOL+ Medion_20014752
00000014de090000 01 VOL+ Medion_20014752

```Is this helping ?

Pierre.

---

### Post by ed3120 on 2008-07-28
Thanks for this.  One quick question before I start....I don't care at all about the IR remote receiver, (I control my MythTV with keyboard emulation) only the IRblaster.

Should I still follow all of your instructions or just part of them?

---

### Post by ed3120 on 2008-07-28
I tried following your steps, but I'm still having trouble.  Any help you can provide is much appreciated.

/etc/lirc$ ls -l /lib/firmware
```

total 312
drwxr-xr-x 4 root root   4096 2008-06-11 18:23 2.6.24-16-generic
drwxr-xr-x 4 root root   4096 2008-06-11 19:05 2.6.24-18-generic
drwxr-xr-x 4 root root   4096 2008-07-28 19:37 2.6.24-19-generic
-rw-r--r-- 1 root root 302355 2007-09-26 20:13 haup-ir-blaster.bin

```

cat /etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Hauppauge PVR-150 (pci) : Motorola Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
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



cat /etc/lirc/lircd.conf
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

#Configuration for the Hauppauge PVR-150 (pci) : Motorola Cable box transmitter:
include /usr/share/lirc/transmitters/motorola/dctxxxx.conf
ed@mythtv:/etc/lirc$ cat /etc/init.d/reset-ir
#! /bin/sh
echo "Resetting the IR receiver/blaster"
/usr/bin/ivtvctl --reset-ir

```

/etc/lirc$ ls -l /dev/lir*
```

crw-rw---- 1 root root 61, 0 2008-07-28 19:57 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-07-28 19:57 /dev/lircd

```

ed@mythtv:/etc/lirc$ sudo irsend -d /dev/lircd SEND_ONCE blaster 1_696_KEY_POWER
irsend: command failed: SEND_ONCE blaster 1_696_KEY_POWER
irsend: unknown remote: "blaster"


/myth/ed$ ./chan_change.sh 302
irsend: command failed: SEND_ONCE blaster 3
irsend: unknown remote: "blaster"
irsend: command failed: SEND_ONCE blaster 0
irsend: unknown remote: "blaster"
irsend: command failed: SEND_ONCE blaster 2
irsend: unknown remote: "blaster"

cat /myth/ed/chan_change.sh
```

#!/bin/sh
REMOTE_NAME=blaster
for digit in $(echo $1 | sed -e 's/./& /g'); do
/usr/bin/irsend SEND_ONCE $REMOTE_NAME $digit
sleep 0.4 # note, you may have to tweak the interdigit delay up a bit, depending on your DISH receiver model
done

```

---

### Post by zorglups on 2008-08-26
> **ed3120 said:**
> Thanks for this.  One quick question before I start....I don't care at all about the IR remote receiver, (I control my MythTV with keyboard emulation) only the IRblaster.

Should I still follow all of your instructions or just part of them?

Yes you should.

---

### Post by zorglups on 2008-08-26
In your post #5, I miss your /usr/share/lirc/transmitters/motorola/dctxxxx.conf


Can you post it ?

Thanks,

Pierre.

Note: Sorry for the late reply. I went on holidays far far from my Linux box.

---

### Post by ed3120 on 2008-08-26
I actually ended up switching back to Knoppmyth because I couldn't get this working.  Maybe I'll switch back to MythBuntu in the future when the kinks are worked out.

---

### Post by mbryner on 2009-02-01
Hello,

Thank you very much for this work-around.  PVR 150 blaster and remote working great for me now!  I searched all over the net until I found this thread.

Here's more detail:

Installed Mythbuntu 8.04 by DVD as usual.
Installed IR receiver module for PVR150 w/ MCC  (remote then works)
Installed ivtv-utils:
	sudo apt-get install ivtv-utils
Install Mark's patch to lirc:
	[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)
Follow your directions at the top of this thread, but...
	Instead of "--reset-ir" in /etc/init.d/reset-ir use "--reset 1"
Edit /etc/lirc/hardware.conf & /etc/lirc/lircd.conf as appropriate (I will post my conf files here shortly)

Some reboots necessary inbetween.
Good read on the concepts:
	[http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC)


Marcus

---

### Post by zorglups on 2009-02-02
Thanks for your details. I gave up with this remote and moved to an MCE one.
It is nevertheless always good to see someone bringing his hown light on an issue.

Pierre

---

### Post by jimmybondo on 2009-10-28
Sorry wrong thread. My apologies if you were subscribed!

---

