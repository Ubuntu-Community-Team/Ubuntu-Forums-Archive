---
title: "NVidia drivers, TBS tuner card and IR-keytable"
date: 2014-04-07
forum: Mythbuntu
---

### Post by keyesmic on 2014-04-07
Hello,
I am running Mythbuntu 12.04, and recently acquired a TBS tuner card (the 6281 I believe) and set it up with MythTV. Having failed to configure the IR receiver with LIRC, I instead turned to IR-keytable. After some tweaking, I got a very pleasing result. I decided that my Mythbuntu machine needed HDMI output, so I acquired a cheap NVidia GeForce 210 card. I booted it up, set up the driver and got lovely HD video and audio. Now, however, IR-keytable no longer works. Even after reinstalling the tuner card's drivers *three times* (including downloading an updated version from their website), [FONT=courier new]ir-keytable -t[/FONT] shows up absolutely nothing.
I get the feeling that I might be overlooking something simple. Part of me suspects that it might be a physical problem, caused by carelessness in installing the graphics card, but I'm certainly hoping that that's not the case.

This is the keytable I'm using:
```
# table tbs6981, type: NEC
0x9f   KEY_ESC
0x99   KEY_ENTER
0x84   KEY_ESC      #Power
0x94   KEY_MUTE
0x87   KEY_1
0x86   KEY_2
0x85   KEY_3
0x8b   KEY_4
0x8a   KEY_5
0x89   KEY_6
0x8f   KEY_7
0x8e   KEY_8
0x8d   KEY_9
0x92   KEY_0
0x80   KEY_ESC   #Back
0xd4   KEY_DELETE
0x81   KEY_UP
0x88   KEY_DOWN
0x90   KEY_LEFT
0x82   KEY_RIGHT
0x96   KEY_UP   #CHANNELUP
0x91   KEY_DOWN   #CHANNELDOWN
0x93   KEY_RIGHTBRACE   #VOLUMEUP
0x8c   KEY_LEFTBRACE   #VOLUMEDOWN
0xdd   KEY_F10   #TV
0x9d   KEY_F11   #ZOOM
0x95   KEY_FAVORITES
0x9b   KEY_MODE
0x9e   KEY_M   #MENU
0x9c   KEY_S   #EGP
0x97   KEY_T   #SUBTITLE
0x9a   KEY_CAMERA
0x83   KEY_R   #RECORD
0xde   KEY_P   #Play
0x98   KEY_P   #Pause
0xdc   KEY_ESC   #Stop
0xdb   KEY_COMMA   #REWIND
0xda   KEY_DOT   #FASTFORWARD
0xd9   KEY_UP   #PREVIOUS
0xd8   KEY_DOWN   #NEXT
```

Thank you for reading this, and I hope someone can help me figure out what's going on. :)

---

### Post by Dave_Alverson on 2014-04-18
What is the output of ir-keytable (without the -t) and "ls -l /sys/class/rc".  Also, what are your remote settings in /etc/lirc/hardware.conf.

---

### Post by keyesmic on 2014-04-19
Thanks for the reply. :)

ir-keytable doesn't show up anything out of the ordinary, I think:
```
Found /sys/class/rc/rc0/ (/dev/input/event2) with:
    Driver saa716x, table rc-tbs-nec
    Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
    Enabled protocols: NEC RC-5 RC-6 JVC SONY 
    Repeat delay = 500 ms, repeat period = 125 ms
```

There's one file in /sys/class/rc:
```
lrwxrwxrwx 1 root root 0 Apr  1 18:01 rc0 -> ../../devices/pci0000:00/0000:00:1c.3/0000:04:00.0/rc/rc0
```

If I'm using ir-keytable, is /etc/lirc/hardware.conf still relevant? If so, that might be the problem, because it's not set up.
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
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
START_LIRCD="false"

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

---

### Post by Dave_Alverson on 2014-04-19
Sorry, I was thinking you were trying to use lirc.  And lirc is not set to start up?  There's a weird thing in the lirc startup script where it will change the enabled protocols to just 'LIRC' if LOAD_MODULES is true.  So if lirc start script is running, it might be doing that.

---

### Post by keyesmic on 2014-04-19
Looks like LOAD_MODULES is indeed true. I'll change that now and see what happens...

EDIT: Nope, still nothing.

---

### Post by keyesmic on 2014-07-01
Sorry to double-post, but I still haven't been able to solve this.
Today, after taking a long break from the issue (and using the keyboard to control my telly :p) I tried irrecord and got the "gap not found" error. I really think that there's absolutely no input coming from the IR receiver, which means there's either a physical problem or some kind of conflict with my NVIDIA card/driver. I think I tried removing the card before but I ended up booting to command-line for some reason. Maybe I should try again&#8230;
Has anybody got any other suggestions?

EDIT: NVIDIA card out, driver uninstalled, LIRC disabled, but it still doesn't work. Right now, I'm thinking: "Definitely a phyisical problem". The question is, where? Or, better yet, is there any other explanation?

---

### Post by blm-ubunet on 2014-07-01
Maybe the IR remote is broken/flat batts.
Try beaming it at a webcam.

Are you sure you were still using the closed TBS blob the whole time?
You could clarify with output of "dmesg".
AFAIK The TBS install does not use DKMS & so after any kernel update you return back to FOSS "media" driver tree.

There is open source (& in later kernel) support for this tuner card. You still need the blob firmware.
[https://github.com/ljalves/linux_media/wiki/CX24117-firmware](https://github.com/ljalves/linux_media/wiki/CX24117-firmware)
That would help to avoid the kernel update/re-compile drama.
I don't know if the FOSS driver supports IR remotes.

The TBS blob driver (2013/06) added a modprobe option (enable_ir=0) to allow disabling IR Rx. Maybe the logic is wrong or not initialized correctly.
Could try adding a *.conf file to /etc/modprobe.d/:

options tbs62x0fe enable_ir=1

I think the FOSS Linux kernel driver module for TBS6981 are named:
cx23885

---

### Post by keyesmic on 2014-07-01
I did already check that the remote was working indeed!

I reinstalled the TBS driver the last time I updated the kernel so I don't think that's the issue.

And I just tried the modprobe suggestion, but that doesn't seem to work either. :(

It's quite late at night here so I'm not about to go reinstalling drivers or anything like that at the moment, but I'll have another look in a few days' time.

---

