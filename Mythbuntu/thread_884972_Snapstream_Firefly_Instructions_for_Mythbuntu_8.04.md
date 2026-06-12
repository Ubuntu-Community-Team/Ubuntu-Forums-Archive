---
title: "Snapstream Firefly Instructions for Mythbuntu 8.04?"
date: 2008-08-09
forum: Mythbuntu
---

### Post by lightning9 on 2008-08-09
Hello all,

I have been lurking on/learning from this forum for quite some time but haven't felt the need to post...until now.

I've been playing with Mythbuntu 8.04 for a few weeks and the biggest issue I had was getting my Snapstream Firefly RF remote working. I looked at many different posts and tried many different things but nothing ever worked completely. I finally figured it out last week on one of my boxes and verified everything on a new box last night.

While searching and learning, I saw a lot of people were having many of the same problems but I never saw a definitive fix or guide for all things Firefly. So, would anybody be interested in having me post my learnings? I would be happy to put something together if there are enough of you who think it would be useful. Or, maybe the guide is out there and I just didn't enter the right search expression?

Let me know...

Lightning9 

Btw, these forums are awesome! Thanks everybody!

---

### Post by Calmor on 2008-08-20
> **lightning9 said:**
> While searching and learning, I saw a lot of people were having many of the same problems but I never saw a definitive fix or guide for all things Firefly. So, would anybody be interested in having me post my learnings? I would be happy to put something together if there are enough of you who think it would be useful.

I'd be happy to have a guide (or at least a summary of your ideas) on how to get the Firefly working.

I haven't really looked yet - finally got some things sorted out on the frontend side - but when I boot, the LIRC daemon fails to start for some reason.

I'm running Mythbuntu x64 8.10 Alpha 4, but the setup should be mostly the same as 8.04 (as it didn't start on 8.04 either).  lsusb lists the X10 device, and I have Mythbuntu Control Center set to Snapstream X10.

---

### Post by lightning9 on 2008-08-23
Sorry it took so long to respond. Did you get yours working yet?

> **Calmor said:**
> I'd be happy to have a guide (or at least a summary of your ideas) on how to get the Firefly working.

Hope this helps.

> **Calmor said:**
> I haven't really looked yet - finally got some things sorted out on the frontend side - but when I boot, the LIRC daemon fails to start for some reason.

My systems also say the remote control daemons fail to start. I thought this was the whole issue and got sidetracked trying to fix the failure, but it turns out that wasn't the problem. I still get this message on both of my boxes and the remotes work fine.

> **Calmor said:**
> I'm running Mythbuntu x64 8.10 Alpha 4, but the setup should be mostly the same as 8.04 (as it didn't start on 8.04 either).  lsusb lists the X10 device, and I have Mythbuntu Control Center set to Snapstream X10.

I am running Mythbuntu 8.04.1 i386 on an athlon 64 because I have had 64 bit driver problems in the past. YMMV.

---

### Post by lightning9 on 2008-08-23
Remember, this worked for me on two boxes but I can't guarantee it will work for anybody else. It should, but...

I installed Mythbuntu 8.04 and selected the Snapstream X10 RF remote. After rebooting, the remote wouldn't work and when I hit Ctrl-Alt-F8, the screen said:
> Starting remote control daemon(s) : LIRC  [fail]

I thought this was the whole issue and got sidetracked trying to fix the failure, but it turns out that wasn't the problem. I still get this message on both of my boxes yet the remotes work fine.

NOTE: My two receivers log differently in /var/log/syslog and they both work.
> Aug 23 10:38:16 mythpc1 kernel: [   62.273277] lirc_dev: IR Remote Control driver registered, at major 61
Aug 23 10:38:16 mythpc1 kernel: [   62.316844] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
Aug 23 10:38:16 mythpc1 kernel: [   62.316849] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
Aug 23 10:38:16 mythpc1 kernel: [   62.321177] lirc_dev: lirc_register_plugin: sample_rate: 0
Aug 23 10:38:16 mythpc1 kernel: [   62.341079] lirc_atiusb[4]: X10 Wireless Technology Inc USB Receiver on usb1:4
Aug 23 10:38:16 mythpc1 kernel: [   62.357092] usbcore: registered new interface driver lirc_atiusb

> Aug 23 09:09:15 mythpc0 kernel: [   43.460551] lirc_dev: IR Remote Control driver registered, at major 61
Aug 23 09:09:15 mythpc0 kernel: [   43.533541] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
Aug 23 09:09:15 mythpc0 kernel: [   43.533545] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
Aug 23 09:09:15 mythpc0 kernel: [   43.550860] lirc_dev: lirc_register_plugin: sample_rate: 0
Aug 23 09:09:15 mythpc0 kernel: [   43.555565] lirc_atiusb[3]: X10 WTI RF receiver on usb1:3
Aug 23 09:09:15 mythpc0 kernel: [   43.570527] usbcore: registered new interface driver lirc_atiusb


This is how I got them working. Hope it helps...

/etc/lircd.conf
[INDENT]You can delete this file (OK, rename it). The file is installed by default, but it isn't used and only added to my confusion. /etc/lirc/lircd.conf is the file that is used.[/INDENT]
/etc/lirc/hardware.conf
[INDENT]I use the default file and it works.
[/INDENT]
/etc/lirc/lircd.conf
[INDENT]The default file includes /usr/share/lirc/remotes/atiusb/lircd.conf.atiusb, and if you look at the file, it has a whole boat load of other remotes that I will never use. Therefore, I replaced it with a Snapstream only file. 
	
[B]The important field in this file is the name which can't contain spaces and must match the remote field in the application specific button mapping files under ~/.lirc.

NOTE: Must be root to edit/overwrite this file.[/B]
[/INDENT]

```
# /etc/lirc/lircd.conf
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(any) on Fri Mar 11 08:51:45 2005
#
# contributed by
#
# brand: Snapstream Firefly Remote
# model no. of remote control:
# devices being controlled by this remote:
#

begin remote

  name Snapstream_X10_RF
    bits 40
    eps 30
    aeps 100
    one 0 0
    zero 0 0
    gap 219964
    toggle_bit 0

    begin codes
      MAXI 0x0000001481AC0000
      MAXI 0x00000014012C0000
      CLOSE 0x00000014D7020000
      CLOSE 0x0000001457820000
      1 0x00000014628D0000
      1 0x00000014E20D0000
      2 0x00000014E30E0000
      2 0x00000014638E0000
      3 0x00000014648F0000
      3 0x00000014E40F0000
      4 0x00000014E5100000
      4 0x0000001465900000
      5 0x0000001466910000
      5 0x00000014E6110000
      6 0x00000014E7120000
      6 0x0000001467920000
      7 0x0000001468930000
      7 0x00000014E8130000
      8 0x00000014E9140000
      8 0x0000001469940000
      9 0x000000146A950000
      9 0x00000014EA150000
      0 0x00000014EC170000
      0 0x000000146C970000
      BACK 0x000000146B960000
      BACK 0x00000014EB160000
      ENT 0x00000014ED180000
      ENT 0x000000146D980000
      VOL+ 0x000000145E890000
      VOL+ 0x00000014DE090000
      VOL- 0x000000145D880000
      VOL- 0x00000014DD080000
      MUTE 0x000000145F8A0000
      MUTE 0x00000014DF0A0000
      FIREFLY 0x0000001455800000
      FIREFLY 0x00000014D5000000
      CH+ 0x00000014608B0000
      CH+ 0x00000014E00B0000
      CH- 0x00000014618C0000
      CH- 0x00000014E10C0000
      INFO 0x0000001483AE0000
      INFO 0x00000014032E0000
      OPTION 0x0000001484AF0000
      OPTION 0x00000014042F0000
      UP 0x000000146F9A0000
      UP 0x00000014EF1A0000
      LEFT 0x00000014729D0000
      LEFT 0x00000014F21D0000
      DOWN 0x0000001477A20000
      DOWN 0x00000014F7220000
      RIGHT 0x00000014749F0000
      RIGHT 0x00000014F41F0000
      OK 0x00000014739E0000
      OK 0x00000014F31E0000
      MENU 0x00000014719C0000
      MENU 0x00000014F11C0000
      EXIT 0x0000001475A00000
      EXIT 0x00000014F5200000
      REC 0x00000014FC270000
      REC 0x000000147CA70000
      PLAY 0x00000014FA250000
      PLAY 0x000000147AA50000
      STOP 0x00000014FD280000
      STOP 0x000000147DA80000
      REW 0x00000014F9240000
      REW 0x0000001479A40000
      FWD 0x00000014FB260000
      FWD 0x000000147BA60000
      PREV 0x00000014002B0000
      PREV 0x0000001480AB0000
      PAUSE 0x00000014FE290000
      PAUSE 0x000000147EA90000
      NEXT 0x00000014FF2A0000
      NEXT 0x000000147FAA0000
      MUSIC 0x00000014DB060000
      MUSIC 0x000000145B860000
      PHOTOS 0x00000014DA050000
      PHOTOS 0x000000145A850000
      DVD 0x00000014D9040000
      DVD 0x0000001459840000
      TV 0x00000014D8030000
      TV 0x0000001458830000
      VIDEO 0x00000014DC070000
      VIDEO 0x000000145C870000
      HELP 0x00000014D6010000
      HELP 0x0000001456810000
      MOUSE 0x00000014022D0000
      MOUSE 0x0000001482AD0000
      A 0x00000014EE190000
      A 0x000000146E990000
      B 0x00000014F01B0000
      B 0x00000014709B0000
      C 0x00000014F6210000
      C 0x0000001476A10000
      D 0x00000014F8230000
      D 0x0000001478A30000

  end codes

end remote

```

~/.mythtv/lircrc
[INDENT]By default, this is a symbolic link to ~/.lirc/mythtv. I think that is a mistake because it only includes the remote mappings for mythtv. Instead, I re-linked the file to ~/.lircrc which is installed by default and includes all the mapping files in ~/.lirc.[/INDENT]

```
cd ~/.mythtv
unlink lircrc
ln -s ../.lircrc lircrc
```

I thought the default button mappings for mythtv, mplayer and xine were a bit lacking and inconsistent so, once I got the remote working, I modified them quite a bit for my tastes and am still in the process of fine tuning.

Again, the default files contain the remote button mappings for all the different supported remotes so I pared my copies down to Snapstream only files. 

**The important thing here is the remote field which exactly matches the name field in /etc/lirc/lircd.conf.** 

```
# ~/.lirc/mythtv
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu


begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = RIGHT
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = DOWN
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = PAUSE
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = MENU
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = CH-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = CLOSE
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = CH+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = FWD
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = PLAY
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = VOL-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = STOP
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = VOL+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = INFO
    config = I
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = ENT
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = UP
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = REC
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = ENT
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = LEFT
    config = Left
    repeat = 0
    delay = 0
end

# OK/Select
begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = OK
    config = Enter
    repeat = 0
    delay = 0
end

# Power Off/Exit
begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = CLOSE
    config = Esc
    repeat = 0
    delay = 0
end

# Escape/Exit/Back
begin
    remote = Snapstream_X10_RF
    prog = mythtv
    button = EXIT
    config = Esc
    repeat = 0
    delay = 0
end

```

```
#~/.lirc/mplayer
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = CLOSE
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = EXIT
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = INFO
    config = osd
    repeat = 0
    delay = 0
end

begin
  prog = mplayer
  remote = Snapstream_X10_RF
  button = MUTE
  repeat = 2
  config = mute
end

begin
  prog = mplayer
  remote = Snapstream_X10_RF
  button = CH+
  repeat = 2
  config = audio_delay +0.1
end


begin
  prog = mplayer
  remote = Snapstream_X10_RF
  button = CH-
  repeat = 2
  config = audio_delay -0.1
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = PLAY
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = PAUSE
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = ENT
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = MUTE
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = VOL-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = ENT
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = STOP
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = UP
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = VOL+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = DOWN
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = RIGHT
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = FWD
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = LEFT
    config = seek -6 0
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = mplayer
    button = REW
    config = seek -30 0
    repeat = 0
    delay = 0
end

```

```
#~/.lirc/xine
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox
# Created for use with Mythbuntu
begin
    remote = Snapstream_X10_RF
    prog = xine
    button = INFO
    config = OSDStreamInfos
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = PLAY
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = PAUSE
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = ENT
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = MUTE
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = VOL-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = ENT
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = STOP
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = UP
    config = EventUp
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = VOL+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = DOWN
    config = EventDown
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = RIGHT
    config = EventRight
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = FWD
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = DVD
    config = RootMenu
    repeat = 0
    delay = 0
end

begin
    remote = Snapstream_X10_RF
    prog = xine
    button = LEFT
    config = EventLeft
    repeat = 0
    delay = 0
end

```

I don't use any of the other files in ~/.lirc so you are on your own there.



If all has gone well (and this guide is correct), reboot now and your remote should work. <fingers crossed>

 

I own two of the Snapstream Firefly remotes and, once I got them working, I had a problem with the remote in my bedroom controlling the box in the living room and vice versa! I used [these instructions]("http://ubuntuforums.org/showthread.php?t=639123") to get lirc to listen on specific channels, however, it sure was a pain re-recording all the button codes for both remotes.

I am not sure if you can use the same codes but here are the /etc/lirc/lircd.conf files I use for channels 2 and 9. If they work for you, great! Otherwise, happy recording!
```

#/etc/lirc/lircd2.conf

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Aug  9 00:22:09 2008
#
# contributed by 
#
# brand:                       lircd2.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name Snapstream_X10_RF
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x1000
  gap          219960
  min_repeat      1
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0x91AC
          CLOSE                    0xE702
          1                        0x728D
          2                        0xF30E
          3                        0x748F
          4                        0xF510
          5                        0x7691
          6                        0xF712
          7                        0xF813
          8                        0x7994
          9                        0xFA15
          0                        0x7C97

          BACK                     0xFB16
          ENT                      0x7D98
          VOL+                     0xEE09
          VOL-                     0xED08
          MUTE                     0x6F8A
          FIREFLY                  0xE500
          CH+                      0x708B
          CH-                      0xF10C
          INFO                     0x93AE
          OPTION                   0x142F
          UP                       0x7F9A
          LEFT                     0x021D
          DOWN                     0x87A2
          RIGHT                    0x041F
          OK                       0x839E
          MENU                     0x011C
          EXIT                     0x85A0
          REC                      0x0C27
          PLAY                     0x8AA5
          STOP                     0x0D28
          REW                      0x89A4
          FWD                      0x0B26
          PREV                     0x90AB
          PAUSE                    0x0E29
          NEXT                     0x8FAA
          MUSIC                    0xEB06
          PHOTOS                   0x6A85
          DVD                      0xE904
          TV                       0x6883
          VIDEO                    0xEC07
          HELP                     0x6681
          MOUSE                    0x122D
          A                        0x7E99
          B                        0x001B
          C                        0x86A1
          D                        0x0823
      end codes

end remote

```

```
#/etc/lirc/lircd9.conf

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Aug  9 00:48:55 2008
#
# contributed by 
#
# brand:                       /etc/lirc/lircd9.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name Snapstream_X10_RF
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x8000
  gap          219920
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0x812C
          CLOSE                    0xD782
          1                        0x620D
          2                        0xE38E
          3                        0x640F
          4                        0x6510
          5                        0xE691
          6                        0x6712
          7                        0xE893
          8                        0x6914
          9                        0xEA95
          0                        0x6C17
          BACK                     0xEB96
          ENT                      0x6D18
          VOL+                     0xDE89
          VOL-                     0xDD88
          MUTE                     0x5F0A
          FIREFLY                  0xD580
          CH+                      0xE08B
          CH-                      0x610C
          INFO                     0x03AE
          OPTION                   0x842F
          UP                       0xEF9A
          LEFT                     0x721D
          DOWN                     0xF7A2
          RIGHT                    0x741F
          OK                       0xF39E
          MENU                     0x711C
          EXIT                     0xF5A0
          REC                      0x7C27
          PLAY                     0xFAA5
          STOP                     0x7D28
          REW                      0xF9A4
          FWD                      0x7B26
          PREV                     0x00AB
          PAUSE                    0x7E29
          NEXT                     0xFFAA
          MUSIC                    0x5B06
          PHOTOS                   0xDA85
          DVD                      0x5904
          TV                       0xD883
          VIDEO                    0x5C07
          HELP                     0x5601
          MOUSE                    0x02AD
          A                        0x6E19
          B                        0xF09B
          C                        0x7621
          D                        0xF8A3
      end codes

end remote

```
Don't forget to symbolically link /etc/lirc/lircd.conf to the correct file **(as root, of course)**.

Good luck!
lightning9

---

### Post by Calmor on 2008-08-24
> **lightning9 said:**
> Sorry it took so long to respond. Did you get yours working yet?

Not yet.  I did some playing around with information from other sites - specifically making a firefly.conf file instead of using the whole atiusb.conf file, since as you said, there is a ton of stuff I'll never use.

I'm away from the box for a couple of days, but I'm anxious to try this out and see if I can get the firefly to finally work.  I'll let you know how it goes.

> My systems also say the remote control daemons fail to start. I thought this was the whole issue and got sidetracked trying to fix the failure, but it turns out that wasn't the problem. I still get this message on both of my boxes and the remotes work fine.

Interesting that it still says that lirc fails to start.  I manually restarted lirc in the terminal and it seemed to start just fine, so I could find no reason for the failure.  Log files didn't seem to provide any clue as to the reason for failure either.

> I am running Mythbuntu 8.04.1 i386 on an athlon 64 because I have had 64 bit driver problems in the past. YMMV.

I tried running that same setup, but I had severe video problems (my onboard card is ATI, and the only other card I have is also ATI).  Oddly, I don't have the issues with 8.10 A4.  I think something was fixed in MythTV, because with the ATI drivers installed in 8.04.1, the QT painter would scramble everything terribly, although after I exited Myth, the screen looked normal.  I don't have that issue in 8.10 A4.  

How do you determine which channel your firefly is set to?  I haven't changed mine since I got it, but I got it from someone else who may have.

Thanks again for the info - I'll definitely give it a go and keep you posted.

---

### Post by lightning9 on 2008-08-24
> **Calmor said:**
> How do you determine which channel your firefly is set to?  I haven't changed mine since I got it, but I got it from someone else who may have.
I used to have a link with very clear instructions but I can't find it right now. 

To determine the channel: 
Press and hold the Firefly button until the red light goes out, then let go of the button. The red light will flash a number of times and go solid. The number of flashes is the currently programmed channel. If you don't want to change the channel, press the Firefly button again or don't press any buttons until the red light goes out.

To change the channel: 
Press and hold the Firefly button until the red light goes out, then let go of the button. After the flashes but while the red light is solid, select the desired channel by pressing the number keys and then the Firefly button. It will flash the new channel number as a confirmation.

---

### Post by Calmor on 2008-08-28
> **lightning9 said:**
> Remember, this worked for me on two boxes but I can't guarantee it will work for anybody else. It should, but...

I followed your setup to the letter, and finally I receive something in irw when pressing buttons on the firefly.  So, I can confirm that this also works in Intrepid Alpha 4.

Unfortunately, an upgrade hosed my mysql server, so I've lost all backend and frontend functionality until I can get that fixed.  I think I'll need to record my own keycodes, but at least now I can.

Thank you for the howto!  This should go somewhere - perhaps to the development team to enable it by default.

---

### Post by lightning9 on 2008-09-01
> **Calmor said:**
> I think I'll need to record my own keycodes, but at least now I can.
You shouldn't need to record your keycodes. The setup you have working with my Snapstream only /etc/lirc/lircd.conf should be all you need. Lirc is configured to accept all channels by default.

---

### Post by Calmor on 2008-09-02
> **lightning9 said:**
> You shouldn't need to record your keycodes. The setup you have working with my Snapstream only /etc/lirc/lircd.conf should be all you need. Lirc is configured to accept all channels by default.

I haven't looked at it in a few days.  Last I checked, the Firefly is on channel 9 and I (think I) used the channel 9 conf file above.  I'd get action in irw so I know the remote was working and lirc was seeing it, but there was no reaction by Myth or any of the other media players.

I'm planning to reinstall anyway - I got a couple new hard drives and want to do a clean install.  I'll try again and let you know how it works.

Thanks again for all your help!

---

### Post by Calmor on 2008-09-27
So I *finally* got around to getting an NVidia card and going with a standard 8.04.1 x64 install.

I got the Firefly up and running, but I have a couple questions.

Do you get slowdowns when you hit keys?  On the keyboard, I can turn the volume up and down with no issues, but hitting the volume button on the Firefly causes the video to get choppy.  The OSD doesn't seem to be the issue.  It's not just the volume, but I used that as an example.

The other is - do you have it working with repeating keys?  At this point it just registers once no matter how long I hold it down.  I think there's a separate code for the repeat - I'll have to check it out and see if there is something I can use.

Thanks again for all your help.  This afternoon I put up a temporary remote diskless server (successfully, with the help of dd-wrt), and the HD HTPC is closer to reality.  I still have a few firewire issues with my SD4250HDC, but it's almost ready for household consumption.

---

### Post by lightning9 on 2008-10-07
> **Calmor said:**
> So I *finally* got around to getting an NVidia card and going with a standard 8.04.1 x64 install.

I got the Firefly up and running, but I have a couple questions.

Do you get slowdowns when you hit keys?  On the keyboard, I can turn the volume up and down with no issues, but hitting the volume button on the Firefly causes the video to get choppy.  The OSD doesn't seem to be the issue.  It's not just the volume, but I used that as an example.

The other is - do you have it working with repeating keys?  At this point it just registers once no matter how long I hold it down.  I think there's a separate code for the repeat - I'll have to check it out and see if there is something I can use.

Thanks again for all your help.  This afternoon I put up a temporary remote diskless server (successfully, with the help of dd-wrt), and the HD HTPC is closer to reality.  I still have a few firewire issues with my SD4250HDC, but it's almost ready for household consumption.

Sorry, I haven't been working on the Firefly because I have other Myth issues that are really bugging me. Playing DVDs is now so choppy, I can't watch them. I now have to burn them and play them on a settop box. And this isn't a problem with my hardware because I have Myth 7.?? installed on another partition in the same box and it plays DVDs just fine! I also have all the latest updates, video drivers, etc. I even tried replacing nvidia-glx-new with nvidia-glx-envy and it still sucks. Anyhoo, sorry about the rant...

Slowdowns: No, I don't get slowdowns on the keys. I can use all of them without issue. 

Repeating keys: No, haven't figure that one out. It's something I would also appreciate but don't plan to work on it until I can watch a DVD without feeling like I am on hallucinogenics.

And just to be clear, I am not trying to be short with you but I am pretty frustrated with Myth right now.

Good luck and let me know if you get any of those items figured out.

---

### Post by bigabe75 on 2009-02-18
Your directions worked great for me.  Mythbuntu 8.10.  However, I did find that the default files use a different Snapstream device name.  It is now Snapstream_Firefly_R1000, instead of Snapstream_X10_RF.  Once I got it working, I did a quick Search/Replace on your custom files and all is good.

Thanks!

---

