---
title: "Getting remote to work with ir-kbd-i2c"
date: 2011-12-02
forum: Mythbuntu
---

### Post by bleve on 2011-12-02
Hi all.  I am using Mythbuntu 11.04.  I have ir-kbd-i2c mostly working with the remote from my PVR-350 except that back/exit is not working.  I would like to get this button to send escape so I can exit out of the current screen on the frontend.  

> 
root@myth01:/etc/lirc# ir-keytable -d /dev/input/event4 -r
scancode 0x0000 = KEY_0 (0x0b)
scancode 0x0001 = KEY_1 (0x02)
scancode 0x0002 = KEY_2 (0x03)
scancode 0x0003 = KEY_3 (0x04)
scancode 0x0004 = KEY_4 (0x05)
scancode 0x0005 = KEY_5 (0x06)
scancode 0x0006 = KEY_6 (0x07)
scancode 0x0007 = KEY_7 (0x08)
scancode 0x0008 = KEY_8 (0x09)
scancode 0x0009 = KEY_9 (0x0a)
scancode 0x000a = KEY_TEXT (0x184)
scancode 0x000b = KEY_RED (0x18e)
scancode 0x000c = KEY_RADIO (0x181)
scancode 0x000d = KEY_MENU (0x8b)
scancode 0x000e = KEY_SUBTITLE (0x172)
scancode 0x000f = KEY_MUTE (0x71)
scancode 0x0010 = KEY_VOLUMEUP (0x73)
scancode 0x0011 = KEY_VOLUMEDOWN (0x72)
scancode 0x0012 = KEY_PREVIOUS (0x19c)
scancode 0x0014 = KEY_UP (0x67)
scancode 0x0015 = KEY_DOWN (0x6c)
scancode 0x0016 = KEY_LEFT (0x69)
scancode 0x0017 = KEY_RIGHT (0x6a)
scancode 0x0018 = KEY_VIDEO (0x189)
scancode 0x0019 = KEY_AUDIO (0x188)
scancode 0x001a = KEY_MHP (0x16f)
scancode 0x001b = KEY_EPG (0x16d)
scancode 0x001c = KEY_TV (0x179)
scancode 0x001e = KEY_NEXTSONG (0xa3)
scancode 0x001f = KEY_EXIT (0xae)
scancode 0x0020 = KEY_CHANNELUP (0x192)
scancode 0x0021 = KEY_CHANNELDOWN (0x193)
scancode 0x0022 = KEY_CHANNEL (0x16b)
scancode 0x0024 = KEY_PREVIOUSSONG (0xa5)
scancode 0x0025 = KEY_ENTER (0x1c)
scancode 0x0026 = KEY_SLEEP (0x8e)
scancode 0x0029 = KEY_BLUE (0x191)
scancode 0x002e = KEY_GREEN (0x18f)
scancode 0x0030 = KEY_PAUSE (0x77)
scancode 0x0032 = KEY_REWIND (0xa8)
scancode 0x0034 = KEY_FASTFORWARD (0xd0)
scancode 0x0035 = KEY_PLAY (0xcf)
scancode 0x0036 = KEY_STOP (0x80)
scancode 0x0037 = KEY_RECORD (0xa7)
scancode 0x0038 = KEY_YELLOW (0x190)
scancode 0x003b = KEY_SELECT (0x161)
scancode 0x003c = KEY_ZOOM (0x174)
scancode 0x003d = KEY_POWER (0x74)
Enabled protocols: RC-5 JVC SONY 
Using the "-t" option I can see the following when the back/exit key is pressed:

> 
root@myth01:/etc/lirc# ir-keytable -t --sysdev rc3
Testing events. Please, press CTRL-C to abort.
1322883884.548449: event MSC: scancode = 1f
1322883884.648418: event MSC: scancode = 1f
dmesg shows:

> 
[609773.271134] ir-kbd-i2c: ir hauppauge (rc5): s1 r1 t1 dev=30 code=31
[609773.271140] ir-kbd-i2c: ir_key_poll: keycode = 0x001f
So the question is, how do I map 0x001f to be "Escape"?  Does ~/.mythtv/lircrc get used or ~/.lirc/mythtv?  The keymap file that is open by the module is /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge but the values there don't make sense to me.  I am guessing I need to map 0x1f to KEY_ESC or KEY_EXIT but not sure how/where to do that.

Thanks,

bleve

---

### Post by bleve on 2011-12-03
I got this solved by the following command:

> ir-keytable -p LIRC --sysdev rc3After doing this:

> root@myth01:/etc/rc_keymaps# diff haupp haupp2
30c30
< scancode 0x001f = KEY_EXIT (0xae)
---
> scancode 0x001f = KEY_ESC (0x01)


---

