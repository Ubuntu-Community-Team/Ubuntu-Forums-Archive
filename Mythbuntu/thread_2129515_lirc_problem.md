---
title: "lirc problem"
date: 2013-03-26
forum: Mythbuntu
---

### Post by 3Slyfpolf on 2013-03-26
Hi All,

My first post here... please be gentle with me :)

I finally finished upgrading my MythTV box (an old KnoppMyth) to Mythbuntu (including moving the old database from schema 1214 to 1299. That was fun!). I have everything working **except** lirc.

I have an Hauppauge WinTV PVR-350 and the kernel modules are loaded, ir-keytable reports it as:
```
Found /sys/class/rc/rc0/ (/dev/input/event14) with:
        Driver ir-kbd-i2c, table rc-hauppauge
        Supported protocols: RC-5 
        Enabled protocols: RC-5 
        Repeat delay = 500 ms, repeat period = 125 ms
```

The problem is that, in the myth frontend, every key press is doubled. This seems to be a problem between lircd and the myth frontend. "irw" reports single key presses, but "ircat mythtv" reports double!
```
$ sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1364309819.168097: event MSC: scancode = 1f01
1364309819.168102: event key down: KEY_1 (0x0002)
1364309819.168104: event sync
1364309819.419224: event key up: KEY_1 (0x0002)
1364309819.419225: event sync
1364309819.968098: event MSC: scancode = 1f02
1364309819.968103: event key down: KEY_2 (0x0003)
1364309819.968104: event sync
1364309820.219226: event key up: KEY_2 (0x0003)
1364309820.219227: event sync
1364309820.868098: event MSC: scancode = 1f03
1364309820.868103: event key down: KEY_3 (0x0004)
1364309820.868104: event sync
1364309821.119224: event key up: KEY_3 (0x0004)
1364309821.119225: event sync
1364309821.668092: event MSC: scancode = 1f04
1364309821.668097: event key down: KEY_4 (0x0005)
1364309821.668099: event sync
1364309821.868088: event MSC: scancode = 1f04
1364309821.868089: event sync
1364309822.119230: event key up: KEY_4 (0x0005)
1364309822.119231: event sync
1364309822.468090: event MSC: scancode = 1f05
1364309822.468093: event key down: KEY_5 (0x0006)
1364309822.468095: event sync
1364309822.719229: event key up: KEY_5 (0x0006)
1364309822.719230: event sync
1364309823.268090: event MSC: scancode = 1f06
1364309823.268093: event key down: KEY_6 (0x0007)
1364309823.268095: event sync
1364309823.368101: event MSC: scancode = 1f06
1364309823.368102: event sync
1364309823.619225: event key up: KEY_6 (0x0007)
1364309823.619226: event sync
1364309823.968096: event MSC: scancode = 1f07
1364309823.968101: event key down: KEY_7 (0x0008)
1364309823.968102: event sync
1364309824.219224: event key up: KEY_7 (0x0008)
1364309824.219225: event sync
1364309824.568101: event MSC: scancode = 1f08
1364309824.568106: event key down: KEY_8 (0x0009)
1364309824.568107: event sync
1364309824.819227: event key up: KEY_8 (0x0009)
1364309824.819228: event sync
1364309825.368096: event MSC: scancode = 1f09
1364309825.368101: event key down: KEY_9 (0x000a)
1364309825.368102: event sync
1364309825.468093: event MSC: scancode = 1f09
1364309825.468095: event sync
1364309825.719231: event key up: KEY_9 (0x000a)
1364309825.719233: event sync
^C$
```
You can see that ir-keytable sees a few double scancodes, but definitely not all of them.

```
$ irw
0001000200000001 00 KEY_1 devinput
0001000300000001 00 KEY_2 devinput
0001000400000001 00 KEY_3 devinput
0001000500000001 00 KEY_4 devinput
0001000600000001 00 KEY_5 devinput
0001000700000001 00 KEY_6 devinput
0001000800000001 00 KEY_7 devinput
0001000900000001 00 KEY_8 devinput
0001000a00000001 00 KEY_9 devinput
^C
$
```
irw sees only single key presses (so the ir-keymap stuff is filtering the occasional double scan code as it should).

```
$ ircat mythtv
1
1
2
2
3
3
4
4
5
5
6
6
7
7
8
8
9
9
^C
$
```
But for reasons I can not figure out, every press is seen double by ircat (and the myth frontend).

Any suggestions? The little bit of hair I have left is in danger of being ripped out!

---

### Post by donb21 on 2013-03-26
Not sure what the problem is, but here's some data-points for comparison.  I'm using the MCE-usb remote, but I would think it would be similar. 

[COLOR=#000000]- ir-keytable is not on my mythbuntu box, so no help there.
- Here's the result from irw, notice the double-hit on Hash.  I had to press buttons very quickly to not get double-hits on every button.


[/COLOR]don@zedo:~$ irw
000000037ff07bfe 00 KEY_1 mceusb
000000037ff07bfd 00 KEY_2 mceusb
000000037ff07bfc 00 KEY_3 mceusb
000000037ff07bfb 00 KEY_4 mceusb
000000037ff07bfa 00 KEY_5 mceusb
000000037ff07bf9 00 KEY_6 mceusb
000000037ff07bf8 00 KEY_7 mceusb
000000037ff07bf7 00 KEY_8 mceusb
000000037ff07bf6 00 KEY_9 mceusb
000000037ff07be2 00 Star mceusb
000000037ff07bff 00 KEY_0 mceusb
000000037ff07be3 00 Hash mceusb
000000037ff07be3 01 Hash mceusb
000000037ff07bf5 00 KEY_CLEAR mceusb
000000037ff07bf4 00 KEY_ENTER mceusb

Here's ircat mythtv.  Didn't matter if I hit buttons quickly or not (or held it down), always got a single-hit.

don@zedo:~$ ircat mythtv
1
2
3
4
5
6
7
8
9
0
D
Return
Left
Up
Right
Down
Return
]
[
Up
Down


This reminds me of some edits that I made on my lircrc (/home/don/.mythty/lircrc - symlinked to /home/.lirc/mythtv) settings.  I wanted some buttons to repeat (up, down, right, left, vol-up, vol-down, etc.).  I inadvertently put the repeat on everything and it bounced like crazy.  Here's the contents of my lircrc (pretty much default stuff, except for a few repeat adjustments).

begin
    remote = mceusb
    prog = mythtv
    button = PlayPause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = RecTV
#    config = R
#    config = PgUp
    config = Q
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_DVD
#    config = PgDown
    config = Z
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_BACK
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_RIGHT
    config = Right
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_LEFT
    config = Left
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_DOWN
    config = Down
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_UP
    config = Up
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = Hash
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_AGAIN
#    config = Q
    config = PgUp
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_NEXT
#    config = Z
    config = PgDown
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_REWIND
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_FORWARD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = Down
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_CHANNELUP
    config = Up
    repeat = 3
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_VOLUMEDOWN
    config = [
    repeat = 2
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_VOLUMEUP
    config = ]
    repeat = 2
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = More
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_HOME
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_ENTER
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_0
    config = 0
    repeat = 0
    delay = 0
end

---

### Post by one30nav on 2013-03-27
From another forum, a great poster helped me with this solution. He noted that the multiple remotes listed in Mythbuntu's lircd.conf.hauppauge causes this error (with Mythtv 0.25).

So, delete all remotes in lircd.conf.hauppauge with the exception of the "Hauppauge_350" codes. Worked for me.

---

### Post by 3Slyfpolf on 2013-03-31
> **one30nav said:**
> From another forum, a great poster helped me with this solution. He noted that the multiple remotes listed in Mythbuntu's lircd.conf.hauppauge causes this error (with Mythtv 0.25).

So, delete all remotes in lircd.conf.hauppauge with the exception of the "Hauppauge_350" codes. Worked for me.

I had already came across that suggestion in my searching... unfortunately no joy. That is what is driving my buggy, I have found a few possible solutions, but none of them seem to help my problem.

---

### Post by one30nav on 2013-04-01
Apologies. Didn't thoroughly read your post. I use the PVR-350 remote with a USB-UIRT Receiver. But it sounds like you are using the stock IR dongle.

I can imagine that you came across the following post: [http://www.mythtv.org/wiki/LIRC#Double_presses_for_certain_buttons](http://www.mythtv.org/wiki/LIRC#Double_presses_for_certain_buttons)

If not, I hope it helps.

P.S. I also use another remote with a Tira IR Receiver and could never get it to "behave" until I generated a unique lircd.conf with irrecord.

---

