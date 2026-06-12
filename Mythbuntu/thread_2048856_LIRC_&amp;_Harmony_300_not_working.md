---
title: "LIRC &amp; Harmony 300 not working"
date: 2012-08-27
forum: Mythbuntu
---

### Post by tez1982 on 2012-08-27
I have a i3 Laptop with a nano stick 290e DVB-T2 and Mythbuntu 12.04.

I've had everything working for a while but the remote with the 209e is pathetic and only has a few buttons. 

[IMG]http://photos.expertreviews.co.uk/images/front_picture_library_Expert_Reviews/dir_276/er_photo_138238_50.jpg[/IMG]. 

I brought a Harmony 300 universal remote so I could use all the buttons, and set it up as a Nova_T500

irrecord worked fine and generated a new harmony3.conf
```
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name  /home/media/harmony3.conf
  bits           56
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x0
  gap          99994
  toggle_bit_mask 0x0

      begin codes
          KEY_1                    0x04000400001E01 0x00000000000000
          KEY_2                    0x04000400001E02 0x00000000000000
          KEY_3                    0x04000400001E03 0x00000000000000
          KEY_4                    0x04000400001E04 0x00000000000000
          KEY_5                    0x04000400001E05 0x00000000000000
          KEY_6                    0x04000400001E06 0x00000000000000
          KEY_7                    0x04000400001E07 0x00000000000000
          KEY_8                    0x04000400001E08 0x00000000000000
          KEY_9                    0x04000400001E09 0x00000000000000
          KEY_0                    0x04000400001E00 0x00000000000000
          KEY_PLAY                 0x04000400001E35 0x00000000000000
          KEY_PAUSE                0x04000400001E30 0x00000000000000
          KEY_REWIND               0x04000400001E32 0x00000000000000
          KEY_FASTFORWARD          0x04000400001E34 0x00000000000000
          KEY_STOP                 0x04000400001E36 0x00000000000000
          KEY_RECORD               0x04000400001E37 0x00000000000000
          KEY_UP                   0x04000400001E14 0x00000000000000
          KEY_DOWN                 0x04000400001E15 0x00000000000000
          KEY_LEFT                 0x04000400001E16 0x00000000000000
          KEY_RIGHT                0x04000400001E17 0x00000000000000
          KEY_OK                   0x04000400001E25 0x00000000000000
          KEY_BACK                 0x04000400001E12 0x00000000000000
          KEY_CHANNELUP            0x04000400001E20 0x00000000000000
          KEY_CHANNELDOWN          0x04000400001E21 0x00000000000000
          KEY_VOLUMEUP             0x04000400001E10 0x00000000000000
          KEY_VOLUMEDOWN           0x04000400001E11 0x00000000000000
          KEY_RED                  0x04000400001E0B 0x00000000000000
          KEY_GREEN                0x04000400001E2E 0x00000000000000
          KEY_YELLOW               0x04000400001E38 0x00000000000000
          KEY_BLUE                 0x04000400001E29 0x00000000000000
          KEY_ESC                  0x04000400001E1F 0x00000000000000
          KEY_MENU                 0x04000400001E0D 0x00000000000000
          KEY_INFO                 0x04000400001E0A 0x00000000000000
          KEY_EPG                  0x04000400001E1B 0x00000000000000
      end codes

end remote

```

However - when I set LIRC to use this nothing happens and IRW gives me no response.

These files are my working configuration using the old remote.

/etc/lirc/hardware.conf
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="pctvusb"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
```

~/.lircrc
```
include ~/.lirc/mythtv
include ~/.lirc/mplayer
include ~/.lirc/xine
include ~/.lirc/vlc
include ~/.lirc/xmame
include ~/.lirc/xmess
include ~/.lirc/totem
include ~/.lirc/elisa
```

~/.mythtv/lircrc
```
begin
remote = pctvusb
prog = mythtv
button = KEY_MUTE
config = |
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_MENU
config = M
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_UP
config = Up
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_DOWN
config = Down
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_LEFT
config = Left
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_RIGHT
config = Right
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_OK
config = Return
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_ESC
config = Escape
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_RECORD
config = R
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_PLAY
config = P
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_FASTFORWARD
config = >
repeat = 0
delay = 0
end

begin
remote = pctvusb
prog = mythtv
button = KEY_REWIND
config = <
repeat = 0
delay = 0
end
```

/etc/lirc/lircd.conf
```
begin remote

name pctvusb
bits 56
eps 30
aeps 100

one 0 0
zero 0 0
pre_data_bits 8
pre_data 0x0
gap 251812
toggle_bit_mask 0x0

begin codes
BTN_0 0x04000400000727 0x01000B00000001
BTN_1 0x0400040000070F 0x01000200000001
BTN_2 0x04000400000715 0x01000300000001
BTN_3 0x04000400000710 0x01000400000001
BTN_4 0x04000400000718 0x01000500000001
BTN_5 0x0400040000071B 0x01000600000001
BTN_6 0x0400040000071E 0x01000700000001
BTN_7 0x04000400000711 0x01000800000001
BTN_8 0x04000400000721 0x01000900000001
BTN_9 0x04000400000712 0x01000A00000001
KEY_MUTE 0x04000400000700 0x01007100000001
KEY_MENU 0x04000400000701 0x01008B00000001
KEY_POWER 0x04000400000739 0x01007400000001
KEY_UP 0x04000400000706 0x01019200000001
KEY_DOWN 0x0400040000070C 0x01019300000001
KEY_LEFT 0x04000400000709 0x01007200000001
KEY_RIGHT 0x04000400000703 0x01007300000001
KEY_OK 0x04000400000705 0x01016000000001
KEY_ESC 0x0400040000073C 0x01008000000001
KEY_EPG 0x0400040000073F 0x01008A00000001
KEY_RECORD 0x04000400000736 0x0100A700000001
KEY_PLAY 0x04000400000730 0x0100A400000001
KEY_FASTFORWARD 0x04000400000733 0x0100D000000001
KEY_REWIND 0x0400040000072D 0x0100A800000001
end codes

end remote
```

I can get the old remote working by changing all the files above back to as shown and then running mythbuntu-lirc-generator. But every time I include the new remote it stops working. Can anyone point me in the right direction?

Thanks!

---

### Post by Lester_Burnham on 2012-08-27
Hi,

I don't think this is the full answer, but you are using devinput, so your ~/.mythtv/lircrc will need to have remote = devinput for each entry.

However, irw should still produce something, as lircrc is the next step.

Install ir-keytable if not already installed, stop lirc and run ```
sudo ir-keytable -t
``` and compare codes.

Lester

---

### Post by tez1982 on 2012-08-30
Thanks, I tried IR keytable and the results are below.

Button 1 pressed on old remote:
```
1346345443.681044: event MSC: scancode = 70f
1346345443.681050: event key down: KEY_1 (0x0002)
1346345443.681050: event sync
1346345443.781074: event MSC: scancode = 70f
1346345443.781075: event sync
1346345444.032884: event key up: KEY_1 (0x0002)
1346345444.032884: event sync

```

Button 1 pressed on new remote
```
1346345543.681047: event MSC: scancode = 1e01
1346345543.681049: event sync
1346345543.781041: event MSC: scancode = 1e01
1346345543.781042: event sync
1346345543.880981: event MSC: scancode = 1e01
1346345543.880982: event sync
1346345544.081022: event MSC: scancode = 1e01
1346345544.081024: event sync

```

So I'm getting an input from both remotes - any ideas where to go from there?

Thanks

---

### Post by tez1982 on 2012-08-30
> **Lester_Burnham said:**
> Hi,

Install ir-keytable if not already installed, stop lirc and run ```
sudo ir-keytable -t
``` and compare codes.

Lester

Thanks, bit of googling came up with this

[http://ubuntuforums.org/showthread.php?t=1754719]("http://ubuntuforums.org/showthread.php?t=1754719")

I've got the remote working using this, however, every time I press a key on the remote, the laptop processes 2-3 kep presses. Any ideas on this?

---

### Post by Lester_Burnham on 2012-08-31
Hi,

It all depends on the receiver. You need to show the output of 
```
sudo ir-keytable
```
Then possibly load a config for the nova T that you have the harmony configured for.
If its RC-6 compatible, you can maybe load MCE for both harmony and ir-keytable.

That's why the harmony didn't show any key codes in the post above.

As for multiple key presses, the harmony can cause this and I think there is settings in the harmony software for it. Probably setting in the kernel driver also, but not sure where. Get it showing key codes first :)

Lester

---

### Post by tez1982 on 2012-09-01
Think I've got somewhere.

The Harmony is set to Nova-T 500
I've loaded the modules for it using ir-keytable (not RC6 compatible)

Had to email harmony and get them to change the remote so it didn't send multiple key presses.

Short version for anyone else

ir-keytable load Hauppauge Modules
Harmony set to Nova T 500
Reconfigure LIRC to use Nova T 500

Thanks for the help everyone!

---

