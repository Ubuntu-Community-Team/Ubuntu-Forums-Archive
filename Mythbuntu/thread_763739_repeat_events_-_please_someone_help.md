---
title: "repeat events - please someone help"
date: 2008-04-23
forum: Mythbuntu
---

### Post by gator on 2008-04-23
Ive got a Twinhan AlphaDTV USB receiver with inbuilt remote receiver - ive gotten most things sorted, i get the correct codes from irw when i press the buttons...but there's two events for every button press.... ive read countless posts on this but cannot get it to work, ive adjusted the repeat and delay in lircrc (1,2,3) but my mythtv still jumps over the menu's - pressing down moves the menu down twice...

steve@media-server:~$ irw
0000000000010193 00 CHANNELDOWN Twinhan_MagicBox
0000000000010193 00 CHANNELDOWN Twinhan_MagicBox
0000000000010192 00 CHANNELUP Twinhan_MagicBox
0000000000010192 00 CHANNELUP Twinhan_MagicBox

Has anyone got this to work? It seems a common problem without an easy answer. This is all i have to do to complete my media center..
One more thing.. how can i be sure i'm transcoding my recordings to xvid4 and not xvid1,2,3 ?.. is this easy to change?
Thanks in advance

---

### Post by Tom Mann on 2008-04-23
I'm currently suffering this - and I've seen a hack to stop it happening (it applies to lircrc) I'll keep trying to find the webpage!

Tom

---

### Post by superm1 on 2008-04-23
If you are using a generated lircrc, you can adjust what ends up in it.

Run mythbuntu-lirc-generator --help

You'll see there are these two items:

--repeat <number>
         Default is "0". Modifies the repeat= directive in .lircrc.
         Quote from LIRC documentation:
         "tells the program what shall happen if a key is repeated. 
         A value of zero tells the program to ignore repeated keys.
         Any other positive value 'n' tells the program to pass the
         config string every 'n'-th time to the according
         application, when a key is repeated. 
         The default for repeat is zero." 
--delay <number>
        Default is "0". Modifies the delay= directive in .lircrc.
        Quote from LIRC documentation:
        "tells the program to ignore the specified number of key
        repeats before using the "repeat" configuration directive
        above. This is used to prevent double triggers of events 
        when using a fast repeat rate. A value of zero, which also 
        is the default, will disable the delay function. "

---

### Post by Tom Mann on 2008-04-23
Here we go - this is what I've done to fix it for me:

[http://ubuntuforums.org/showpost.php?p=4253678&postcount=6]("http://ubuntuforums.org/showpost.php?p=4253678&postcount=6")
It involves adding a line to each button, prior to the config line already assigned for the button, with the following:

config = echo '' > /dev/null


So you'll end up with something like:

remote = Hauppauge_New
prog = mythtv
button = 7
config = echo '' > /dev/null
config = 7
repeat = 0
delay = 0

which somehow (I don't know how, it's a dirty hack) fixes the problem.

Superm1, I've tried all sorts of delays and repeats, nothing seemed to make a difference - I found the link to the above from someone having the exact same trouble as me. ([http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Remote_control]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Remote_control"))

---

### Post by gator on 2008-04-23
THANK YOU TOM, you are a LEGEND, everything works very cool, by the looks of it, it sends the first event to /dev/null and uses the next one... now i'm happy :guitar::popcorn:

---

### Post by Tom Mann on 2008-04-24
Good to hear it's working :)

SuperM is this worth a mention in the Mythbuntu manual?

---

### Post by gator on 2008-04-25
You get my vote TOM
Thanks SuperM for your input, you would think by the instructions that repeat and delay would fix it but this is not the case.
 Ubuntu and Mythbuntu grow stronger with the help of people like you, together we can get to where were going.
 TOM, my wife says thanks ?:lolflag:

---

### Post by laga on 2008-04-25
Just wondering - do you have any duplicate definitions in your /etc/lirc/lircd.conf? Maybe you can post it here..

---

### Post by Tom Mann on 2008-04-28
FYI

lircd.conf
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

#Configuration for the Custom remote:
include /etc/lirc/lircd.conf.Hauppauge_New
```

lircd.conf.Hauppauge_New
```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(devinput) on Wed Apr 23 14:06:20 2008
#
# contributed by 
#
# brand:                       /home/sysadmin/testremote
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name           HauppaugeNovaTStick
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x1
  gap          251917
  toggle_bit_mask 0x80000000

      begin codes
          Go                       0x0162
          Power                    0x0074
          TV                       0x0179
          Videos                   0x0189
          Music                    0x0188
          Pictures                 0x00E2
          Guide                    0x016D
          Radio                    0x0181
          Up                       0x0067
          Left                     0x0069
          Right                    0x006A
          Down                     0x006C
          OK                       0x0160
          Back/Exit                0x009E
          Menu/i                   0x008B
          PrevCh                   0x016B
          Mute                     0x0071
          Vol+                     0x0073
          Vol-                     0x0072
          Ch+                      0x0192
          Ch-                      0x0193
          Record                   0x00A7
          Stop                     0x0080
          Rewind                   0x00A8
          Forward                  0x00D0
          Play                     0x00CF
          Replay/SkipBackward      0x0195
          SkipForward              0x0197
          Pause                    0x0077
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x000A
          0                        0x000B
          *                        0x0037
          #                        0x0029
          Red                      0x018E
          Green                    0x018F
          Yellow                   0x0190
          Blue                     0x0191
      end codes

end remote

```

lircrc
```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 7
    config = echo '' > /dev/null
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Right
    config = echo '' > /dev/null
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Mute
    config = echo '' > /dev/null
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = SkipForward
    config = echo '' > /dev/null
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 1
    config = echo '' > /dev/null
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Down
    config = echo '' > /dev/null
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 0
    config = echo '' > /dev/null
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Replay/SkipBackward
    config = echo '' > /dev/null
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Pause
    config = echo '' > /dev/null
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Menu/i
    config = echo '' > /dev/null
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 6
    config = echo '' > /dev/null
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 2
    config = echo '' > /dev/null
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Ch-
    config = echo '' > /dev/null
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Back/Exit
    config = echo '' > /dev/null
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Ch+
    config = echo '' > /dev/null
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Rewind
    config = echo '' > /dev/null
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Forward
    config = echo '' > /dev/null
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Play
    config = echo '' > /dev/null
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Vol-
    config = echo '' > /dev/null
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Stop
    config = echo '' > /dev/null
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Vol+
    config = echo '' > /dev/null
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 5
    config = echo '' > /dev/null
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 4
    config = echo '' > /dev/null
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = OK
    config = echo '' > /dev/null
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Up
    config = echo '' > /dev/null
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Record
    config = echo '' > /dev/null
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 9
    config = echo '' > /dev/null
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 3
    config = echo '' > /dev/null
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = 8
    config = echo '' > /dev/null
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Guide
    config = echo '' > /dev/null
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = HauppaugeNovaTStick
    prog = mythtv
    button = Left
    config = echo '' > /dev/null
    config = Left
    repeat = 0
    delay = 0
end

```

---

