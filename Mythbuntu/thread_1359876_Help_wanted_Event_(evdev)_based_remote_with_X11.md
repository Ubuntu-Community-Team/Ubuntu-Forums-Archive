---
title: "Help wanted: Event (evdev) based remote with X11"
date: 2009-12-20
forum: Mythbuntu
---

### Post by Henk Poley on 2009-12-20
Help me figure this out.

TL;DR; :: Infrared saa7134 remote events don't appear in X11 anymore. xorg.conf directs me to  /etc/default/console-setup, but can't set per keyboard settings there.

I updated to Karmic Koala thursday evening to try to fix some cpu frequency scaling related video stuttering with MythTV. I remember my remote still worked after the update. Since then I updated my ext3 system partition to ext4 (didn't improve anything). For that I dropped to the 'emergency' rootshell option in the Grub bootmenu. I suspect that zeroed some configuration caches since the keypresses from my remote don't go to X11 anymore at the moment.

I have two recording devices, saa7134 (DVB-C) saa7146 (analog). Both of which dump button presses as keyboard events into /dev/input{/...}. In 2004 when I started with MythTV I just needed to specify 'evdev' (I believe) as the core keyboard device in XF86Config and it would work. Lateron I had to remove the setting Ubuntu automatically injects that every keyboard is a 105 key US keyboard. More recently I could specify the different devices by their PCI bus id. But with Ubuntu 9.10 that doesn't seem to exist anymore.

Since MythTV doesn't know all the multimedia keypresses I use the input-utils package to remap the keypresses. Keypress remapping in /etc/rc.local:
```
# Find correct event device
stringZ=`lsinput 2>&1 | grep -B5 "Budget-CI" | grep "event" | head -n1`
eventnr=`expr substr $stringZ 17 1`

# Set keymap
input-kbd $eventnr -f /root/remote.saa7146.keymap
```

Re-enabling the lines in xorg.conf preceded by "commented out by update-manager, HAL is now used and auto-detects devices Keyboard settings are now read from /etc/default/console-setup" just makes X11 error out and not start. Also, there doesn't seem to be a per keyboard setting in the mentioned console-setup file.

Anybody knows any documentation around this recent change in Ubuntu ?

---

### Post by Henk Poley on 2009-12-20
Aw, after posting it I fiddled with `input-events`, which dumps any keypresses. And nothing showed up for the remote input device. So I replugged the IR dongle and now it works again.

Solved.

Anyways, lets document my setup a bit further, /root/remote.saa7146.keymap (the remap file I use for myth):
```
#number = keycode   # used to be this keycode
0x0001 = KEY_ESC   # KEY_POWER
0x0002 = 410 # KEY_SHUFFLE
0x0003 = KEY_1
0x0004 = KEY_2
0x0005 = KEY_3
0x0006 = KEY_4
0x0007 = KEY_5
0x0008 = KEY_6
0x0009 = KEY_7
0x000a = KEY_8
0x000b = KEY_9
0x000c = KEY_0
0x000d = KEY_UP
0x000e = KEY_LEFT
0x000f = KEY_ENTER  # KEY_OK
0x0010 = KEY_RIGHT
0x0011 = KEY_DOWN
0x0012 = KEY_INFO
0x0013 = KEY_ESC    # KEY_EXIT
0x0014 = KEY_F2     # KEY_RED
0x0015 = KEY_F3     # KEY_GREEN
0x0016 = KEY_F4     # KEY_YELLOW
0x0017 = KEY_F5     # KEY_BLUE
0x0018 = KEY_F9     # KEY_MIN_INTERESTING
0x0019 = KEY_T      # KEY_TEXT
0x001a = 373  # KEY_MODE
0x0021 = 357  # KEY_OPTION
0x0022 = KEY_M      # KEY_EPG
0x0023 = KEY_UP     # KEY_CHANNELUP
0x0024 = KEY_DOWN   # KEY_CHANNELDOWN
0x0025 = KEY_F11    # KEY_VOLUMEUP
0x0026 = KEY_F10    # KEY_VOLUMEDOWN
0x0027 = 141  # KEY_SETUP
0x003a = KEY_R      # KEY_RECORD
0x003b = KEY_SPACE  # KEY_PLAY
0x003c = KEY_ESC    # KEY_STOP
0x003d = KEY_LEFT   # KEY_REWIND
0x003e = KEY_P      # KEY_PAUSE
0x003f = KEY_RIGHT  # KEY_FORWARD
```

---

