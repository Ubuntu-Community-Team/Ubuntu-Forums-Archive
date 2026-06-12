---
title: "Antec RM200 remote not talking to MythTV"
date: 2010-02-13
forum: Mythbuntu
---

### Post by enzymes on 2010-02-13
Hi,

I'm having trouble getting my Veris RM200 remote to work with MythTV.

Don't ask me how, but I've got the Ubuntu to read the IR keys using the irw command (see the dump below)

I can't figure out though how to get Myth to read these LIRC signals. 

I'm running MythTV on Koala 64bit - I didn't install MythBuntu but followed Garry Parker's great installation guide at [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

My case is the [Antec Fusion Remote Black 430]("http://www.antec.com/Believe_it/product.php?Type=Mg==&id=NTA=") and the remote is the [Veris RM200 remote]("http://www.antec.com/images/400/RM200_400.jpg") that came with the case.

Any suggestions? Hopefully it is something pretty obvious!

Thanks! The relevant stuff is below.


Michael

irw

```

289115b700000201 00 KEY_POWER Antec_Veris_RM200
2881d5b700000201 00 KEY_EXIT Antec_Veris_RM200
298115b700000201 00 KEY_RECORD Antec_Veris_RM200
2a8115b700000201 00 KEY_PLAY Antec_Veris_RM200
29b195b700000201 00 KEY_OPEN Antec_Veris_RM200
2a8195b700000201 00 KEY_REWIND Antec_Veris_RM200
2a9115b700000201 00 KEY_PAUSE Antec_Veris_RM200
2b8115b700000201 00 KEY_FASTFORWARD Antec_Veris_RM200
2b9115b700000201 00 KEY_PREVIOUS Antec_Veris_RM200
2b9715b700000201 00 KEY_STOP Antec_Veris_RM200
298195b700000201 00 KEY_NEXT Antec_Veris_RM200
01007f0000000201 00 KEY_DOWN Antec_Veris_RM200
0100007f00000201 00 KEY_RIGHT Antec_Veris_RM200
0200002a00000201 00 KEY_BACKSPACE Antec_Veris_RM200
0200002c00000201 00 KEY_SELECT Antec_Veris_RM200
0200006500000201 00 RightMenu Antec_Veris_RM200
0102000000000201 00 BTN_RIGHT Antec_Veris_RM200
0200002800000201 00 KEY_ENTER Antec_Veris_RM200
0101000000000201 00 BTN_LEFT Antec_Veris_RM200
0280000000000201 00 LeftMenu Antec_Veris_RM200
0200002900000201 00 KEY_ESC Antec_Veris_RM200
299395b700000201 00 KEY_EJECTCD Antec_Veris_RM200
29b715b700000201 00 AppLauncher Antec_Veris_RM200
2a9395b700000201 00 TaskSwitcher Antec_Veris_RM200
2ab195b700000201 00 Go Antec_Veris_RM200
28a395b700000201 00 KEY_VOLUMEUP Antec_Veris_RM200
28a595b700000201 00 KEY_VOLUMEDOWN Antec_Veris_RM200
289395b700000201 00 KEY_CHANNELUP Antec_Veris_RM200
288795b700000201 00 KEY_CHANNELDOWN Antec_Veris_RM200
2b9595b700000201 00 KEY_MUTE Antec_Veris_RM200
2b8395b700000201 00 Timer Antec_Veris_RM200
0200001e00000201 00 KEY_1 Antec_Veris_RM200
0200001f00000201 00 KEY_2 Antec_Veris_RM200
0200002000000201 00 KEY_3 Antec_Veris_RM200
0200002100000201 00 KEY_4 Antec_Veris_RM200
0200002200000201 00 KEY_5 Antec_Veris_RM200
0200002300000201 00 KEY_6 Antec_Veris_RM200
0200002400000201 00 KEY_7 Antec_Veris_RM200
0200002500000201 00 KEY_8 Antec_Veris_RM200
0200002600000201 00 KEY_9 Antec_Veris_RM200
0220002500000201 00 Star Antec_Veris_RM200
0200002700000201 00 KEY_0 Antec_Veris_RM200
0220002000000201 00 Hash Antec_Veris_RM200
2b8515b700000201 00 KEY_VIDEO Antec_Veris_RM200
299195b700000201 00 KEY_AUDIO Antec_Veris_RM200
2ba115b700000201 00 KEY_PHOTO Antec_Veris_RM200
28a515b700000201 00 KEY_TV Antec_Veris_RM200
288515b700000201 00 KEY_BOOKMARKS Antec_Veris_RM200
2ab715b700000201 00 Thumbnail Antec_Veris_RM200
29a595b700000201 00 Zoom Antec_Veris_RM200
2aa395b700000201 00 FullScreen Antec_Veris_RM200
29a395b700000201 00 KEY_DVD Antec_Veris_RM200
2ba395b700000201 00 KEY_MENU Antec_Veris_RM200
298595b700000201 00 Subtitle Antec_Veris_RM200
2b8595b700000201 00 KEY_LANGUAGE Antec_Veris_RM200

```

My LIRC related files look like this:

/etc/lirc/hardware.conf

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON Antec Veris"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="imon/lircd.conf.imon-antec-veris"
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
include "/usr/share/lirc/remotes/imon/lircd.conf.imon-antec-knob"

```


/etc/lirc/lircmd.conf

```

#UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
# 
#	/usr/share/doc/lirc/README.Debian


```

---

### Post by Jæd on 2010-02-14
I have the Antec Fusion Silver case, with the same remote. This is what solved it for me:

1)

Went to the LIRC config screen in mythfrontend and changed the LIRC Daemon socket to /dev/lircd. 

(I started up mythfrontend in a terminal. When it was starting up I saw that it could not connect to /dev/lirc0 .)

2)

```

sudo apt-get install mythbuntu-lirc-generator
mythbuntu-lircrc-generator

```This generates the file .lircrc . It also added config files for mplayer, totem, etc in ~/.lirc/

I then started mythfrontend and my Remote works, as does my big Knob. ( :) )

Let me know how you get on...

---

