---
title: "Mythbuntu 10.10 Snapstream Firefly"
date: 2010-10-16
forum: Mythbuntu
---

### Post by jlipoth on 2010-10-16
I recently upgraded from Mythbunto 9.10 to 10.10 and it appears the Snapstream Firefly is no longer supported.  This usually also works with the ATI X10 setup as well, but I can't even get signs of life from doing an "irw" command in terminal.  What's going on?

---

### Post by rantic on 2010-10-18
Had the same problem but was able to get mine working.  It looks like the lircd.conf and the lircrc files are not correct.

Choose the "ATI/NVidia/X10 I & II RF Remote" (might say something about userspace, not in front of my machine at the moment).

I overwrote /etc/lirc/lircd.conf to:

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4a(atilibusb) on Mon Nov 24 14:58:45 2008
#
# contributed by 
#
# brand:                       lircd.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  lircd.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          147992
  min_repeat      5
  toggle_bit_mask 0x80800000

      begin codes
          MAXI                     0x812C
          MAXI                     0x01AC
          CLOSE                    0x5702
          CLOSE                    0xD782
          1                        0x620D
          1                        0xE28D
          2                        0x630E
          2                        0xE38E
          3                        0x640F
          3                        0xE48F
          4                        0x6510
          4                        0xE590
          5                        0x6611
          5                        0xE691
          6                        0x6712
          6                        0xE792
          7                        0x6813
          7                        0xE893
          8                        0x6914
          8                        0xE994
          9                        0x6A15
          9                        0xEA95
          0                        0x6C17
          0                        0xEC97
          BACK                     0x6B16
          BACK                     0xEB96
          ENT                      0x6D18
          ENT                      0xED98
          VOL+                     0x5E09
          VOL+                     0xDE89
          VOL-                     0x5D08
          VOL-                     0xDD88
          MUTE                     0x5F0A
          MUTE                     0xDF8A
          FIREFLY                  0x5500
          FIREFLY                  0xD580
          CH+                      0x600B
         CH+                      0xE08B
          CH-                      0x610C
          CH-                      0xE18C
          INFO                     0x832E
          INFO                     0x03AE
          OPTION                   0x842F
          OPTION                   0x04AF
          UP                       0x6F1A
          UP                       0xEF9A
          LEFT                     0x721D
          LEFT                     0xF29D
          DOWN                     0x7722
          DOWN                     0xF7A2
          RIGHT                    0x741F
          RIGHT                    0xF49F
          OK                       0x731E
          OK                       0xF39E
          MENU                     0x711C
          MENU                     0xF19C
          EXIT                     0x7520
          EXIT                     0xF5A0
          REC                      0x7C27
          REC                      0xFCA7
          PLAY                     0x7A25
          PLAY                     0xFAA5
          STOP                     0x7D28
          STOP                     0xFDA8
          REW                      0x7924
          REW                      0xF9A4
          FWD                      0x7B26
          FWD                      0xFBA6
          PREV                     0x802B
          PREV                     0x00AB
          PAUSE                    0x7E29
          PAUSE                    0xFEA9
          NEXT                     0x7F2A
          NEXT                     0xFFAA
          MUSIC                    0x5B06
          MUSIC                    0xDB86
          PHOTOS                   0x5A05
          PHOTOS                   0xDA85
          DVD                      0x5904
          DVD                      0xD984
          TV                       0x5803
          TV                       0xD883
          VIDEO                    0x5C07
          VIDEO                    0xDC87
          HELP                     0x5601
          HELP                     0xD681
          MOUSE                    0x822D
          MOUSE                    0x02AD
          A                        0x6E19
          A                        0xEE99
          B                        0x701B
          B                        0xF09B
          C                        0x7621
          C                        0xF6A1
          D                        0x7823
          D                        0xF8A3
      end codes

end remote
```

and then overwrote ~/.mythtv/lircrc to:

```
# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the new grey Hauppauge remote
#
# Modified from Jarod Wilson's which came from Jeff Campbell's
# By Brad Templeton
#
# Modified again to use the Firefly remotes unique buttons by Ryan Schmitz
#
#
# Here we have the jump point commands.  They only work if you have
# defined function keys for these jump points.
#
# You can set the jump point commands in Mythweb under Settings > Key Bindings as follows:
# F8 Main Menu
# F3 Program Guide
# F5 TV Recording Playback
# F7 Play DVD
# F6 MythGallary
# F4 Play Music
# F2 MythVideo


begin
prog = mythtv
button = FIREFLY
repeat = 3
config = F8
end

begin
prog = mythtv
button = TV
repeat = 3
config = F5
end

begin
prog = mythtv
button = VIDEO
repeat = 3
config = F2
end

begin
prog = mythtv
button = MUSIC
repeat = 3
config = F4
end

begin
prog = mythtv
button = PHOTOS
repeat = 3
config = F
end

begin
prog = mythtv
button = DVD
repeat = 3
config = F7
end

begin
prog = mythtv
button = HELP
repeat = 3
config = F1
end

begin
prog = mythtv
button = UP
repeat = 3
config = Up
end

begin
prog = mythtv
button = DOWN
repeat = 3
config = Down
end

begin
prog = mythtv
button = LEFT
repeat = 3
config = Left
end

begin
prog = mythtv
button = RIGHT
repeat = 3
config = Right
end

# Channel Up
begin
prog = mythtv
button = CH+
repeat = 3
config = Up
end

# Channel Down
begin
prog = mythtv
button = CH-
repeat = 3
config = Down
end

# OK/Select
begin
prog = mythtv
button = OK
config = Space
end

# OK/Select
begin
prog = mythtv
button = ENT
config = Space
end

# Play
begin
prog = mythtv
button = Play
config = Return
end

# Stop
begin
prog = mythtv
button = Stop
config = I
end

# Escape/Exit/Back
begin
prog = mythtv
button = BACK
config = Esc
end

# Power Off/Exit
begin
prog = mythtv
button = CLOSE
config = Esc
end

# Escape/Exit/Back
begin
prog = mythtv
button = EXIT
config = Esc
end

# Pause
begin
prog = mythtv
button = Pause
repeat = 3
config = P
end

# Mute
begin
prog = mythtv
button = Mute
repeat = 3
config = |
end

# Fast forward (30 sec default)
begin
prog = mythtv
button = REW
repeat = 3
config = PgUp
end

# Rewind (10 sec default)
begin
prog = mythtv
button = FWD
repeat = 3
config = PgDown
end

# Skip forward (10 min default)
begin
prog = mythtv
button = NEXT
repeat = 3
config = End
end

# Skip backward (10 min default)
begin
prog = mythtv
button = PREV
repeat = 3
config = Home
end

# Record
begin
prog = mythtv
button = REC
repeat = 3
config = R
end

# Delete
begin
prog = mythtv
button = A
repeat = 3
config = D
end

# Decrease play speed
begin
prog = mythtv
button = B
repeat = 3
config = J
end

# double speed watch
begin
prog = mythtv
button = C
repeat = 3
config = J
end

# Bring up Time stretch
begin
prog = mythtv
button = D
repeat = 3
config = Y
end

change tuners
begin
prog = mythtv
button = OPTION
repeat = 3
config = Y
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
button = MENU
repeat = 3
config = M
end

# Scroll up
begin
prog = mythtv
button = VOL+
repeat = 3
config = F11
end

# Scroll down
begin
prog = mythtv
button = VOL-
repeat = 3
config = F10
end

# Bring up OSD info
begin
prog = mythtv
button = INFO
repeat = 3
config = I
end

# Change display aspect ratio
begin
prog = mythtv
button = CH-
repeat = 3
config = W
end

# Numbers 0-9

begin
prog = mythtv
button = 0
repeat = 3
config = 0
end

begin
prog = mythtv
button = 1
repeat = 3
config = 1
end

begin
prog = mythtv
button = 2
repeat = 3
config = 2
end

begin
prog = mythtv
button = 3
repeat = 3
config = 3
end

begin
prog = mythtv
button = 4
repeat = 3
config = 4
end

begin
prog = mythtv
button = 5
repeat = 3
config = 5
end

begin
prog = mythtv
button = 6
repeat = 3
config = 6
end

begin
prog = mythtv
button = 7
repeat = 3
config = 7
end

begin
prog = mythtv
button = 8
repeat = 3
config = 8
end

begin
prog = mythtv
button = 9
repeat = 3
config = 9
end
### MPlayer lirc setup

# Show OSD
begin
prog = mplayer
button = MENU
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = PAUSE
repeat = 3
config = pause
end

# Skip ahead a minute if playing
# If paused, resume playing
begin
prog = mplayer
button = PLAY
repeat = 3
config = seek +1
end

# Stop playback and exit
begin
prog = mplayer
button = Back
repeat = 3
config = quit
end

# Stop playback and exit
begin
prog = mplayer
button = EXIT
repeat = 3
config = quit
end

# Stop playback and exit
begin
prog = mplayer
button = CLOSE
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = MUTE
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = LEFT
repeat = 3
config = seek -7
end

# Seek forward 30 seconds
begin
prog = mplayer
button = RIGHT
repeat = 3
config = seek +30
end

# Seek forward 10 minutes
begin
prog = mplayer
button = NEXT
repeat = 3
config = seek +600
end

# Seek backward 10 minutes
begin
prog = mplayer
button = PREV
repeat = 3
config = seek -600
end

# Toggle full-screen
begin
prog = mplayer
button = OPTION
repeat = 3
config = vo_fullscreen
end

# Toggle full-screen
begin
prog = mplayer
button = MAXI
repeat = 3
config = vo_fullscreen
end

### Xine lirc setup

begin
prog = xine
button = PLAY
repeat = 3
config = Play
end

begin
prog = xine
button = STOP
repeat = 3
config = Stop
end

begin
prog = xine
button = BACK
repeat = 3
config = Quit
end

begin
prog = xine
button = EXIT
repeat = 3
config = Quit
end

begin
prog = xine
button = CLOSE
repeat = 3
config = Quit
end

begin
prog = xine
button = PAUSE
repeat = 3
config = Pause
end

begin
prog = xine
button = UP
repeat = 3
config = EventUp
end

begin
prog = xine
button = DOWN
repeat = 3
config = EventDown
end

begin
prog = xine
button = LEFT
repeat = 3
config = EventLeft
end

begin
prog = xine
button = RIGHT
repeat = 3
config = EventRight
end

begin
prog = xine
button = OK
repeat = 3
config = EventSelect
end

begin
prog = xine
button = ENT
repeat = 3
config = EventSelect
end

begin
prog = xine
button = OPTION
repeat = 3
config = Menu
end

begin
prog = xine
button = FFW
repeat = 3
#config = SpeedFaster
config = SeekRelative+60
end

begin
prog = xine
button = REW
repeat = 3
#config = SpeedSlower
config = SeekRelative-60
end

begin
prog = xine
button = VOL+
repeat = 3
config = Volume+
end

begin
prog = xine
button = VOL-
repeat = 3
config = Volume-
end

begin
prog = xine
button = MUTE
repeat = 3
config = Mute
end

begin
prog = xine
button = MENU
repeat = 3
config = RootMenu
end

begin
prog = xine
button = NEXT
repeat = 3
config = EventNext
end

begin
prog = xine
button = PREV
repeat = 3
config = EventPrior
end

begin
prog = xine
button = INFO
repeat = 3
config = OSDStreamInfos
end
```

Probably not the best way, but it works as a quick and dirty fix. Found information helpful information [here]("http://www.mythtv.org/wiki/Snapstream_Firefly")

---

### Post by williammanda on 2010-10-27
FYI
Use the lircd.conf that was supplied by Rantic or newer. I tried mine which was version 0.8.2 and it didn't work.

---

### Post by phroman on 2010-10-28
I'm using a snapstream firefly also, I can give you my config files if you need em'.

---

### Post by bigfish24 on 2010-12-14
Having the same issues. My Snapstream Firefly has no response even after updating the 2 files mentioned earlier. Any ideas? I'm losing my hair on this one!!
 
Running Mythbuntu 10.10

---

### Post by rantic on 2010-12-14
Have you tried stopping and starting lirc, after updating the new files?

---

### Post by bigfish24 on 2010-12-14
// SOLVED //
A full reboot of the machine does not actually restart/re-read LIRC.  For me, running "irw" from console showed no activity from the remote.
 
1. To restart LIRC after making the changes noted above, type "sudo /etc/init.d/lirc restart" into console. This restarts LIRC and rereads the configs.
2. Run "irw" from the console again .... you should see some activity by now.
3. For some reason, the remote still didn't work for me in MythTV frontend.  Probably from all the changing of config files I had done.  Any way, running the MythBuntu package "mythbuntu-lirc-generator" fixed my problem and got the remote to function within MythTv.
4. My last issue I had was with the buttons advancing too much (pressing up would move the selection up 2 places instead of 1).  Also, menus would flicker instead of staying open (actually it was displaying the menu and the immediately closing it again)  This was easily fixed by modifying the values "repeat = 3"  to "repeat = 5" within the ~/.mythtv/lircrc file.  A qick find/replace and I was good to go.  The remote works like a champ and I love the RF ability.  Probably one of the best remotes out there in my opinion (if you don't mind the occasional hack).
 
THANKS RANTIC for pointing me in the right direction.  Hope this helps anybody else out there.  In short, Yes ... you can use the Snapstream Firefly RF remote on MythBuntu 10.10.  Cheers!

---

### Post by williammanda on 2010-12-17
What command is everyone using to generate the lircd.conf? I tried:

irrecord -d /dev/lircd lircd.conf

and I got this error (in bold):

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

This program will record the signals from your remote control
and create a config file for lircd.


A proper config file for lircd is maybe the most vital part of this
package, so you should invest some time to create a working config
file. Although I put a good deal of effort in this program it is often
not possible to automatically recognize all features of a remote
control. Often short-comings of the receiver hardware make it nearly
impossible. If you have problems to create a config file READ THE
DOCUMENTATION of this package, especially section "Adding new remote
controls" for how to get help.

If there already is a remote control of the same brand available at
[http://www.lirc.org/remotes/](http://www.lirc.org/remotes/) you might also want to try using such a
remote as a template. The config files already contain all
parameters of the protocol used by remotes of a certain brand and
knowing these parameters makes the job of this program much
easier. There are also template files for the most common protocols
available in the remotes/generic/ directory of the source
distribution of this package. You can use a template files by
providing the path of the file as command line parameter.

Please send the finished config files to <lirc@bartelmus.de> so that I
can make them available to others. Don't forget to put all information
that you can get about the remote control in the header of the file.

Press RETURN to continue.


Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.
[B]irrecord: error reading from /dev/lircd
irrecord: No such file or directory
Segmentation fault[/B]

---

### Post by daninca on 2011-04-02
I just upgraded to 10.10 and am having problems getting my Snapstream Firefly to work again.  I'm not sure if I have the right device and driver for the new stuff.

Could someone post their /etc/lirc/hardware.conf for the Firefly under 10.10?

Thanks,
-Dan

---

### Post by williammanda on 2011-04-02
> **daninca said:**
> I just upgraded to 10.10 and am having problems getting my Snapstream Firefly to work again.  I'm not sure if I have the right device and driver for the new stuff.

Could someone post their /etc/lirc/hardware.conf for the Firefly under 10.10?

Thanks,
-Dan

Look at the 2nd post for your answer.

---

### Post by daninca on 2011-04-02
I see lircd.conf and lircrc, but no hardware.conf.
-Dan

---

### Post by williammanda on 2011-04-02
> **daninca said:**
> I see lircd.conf and lircrc, but no hardware.conf.
-Dan

This was in the 2nd post:

Choose the "ATI/NVidia/X10 I & II RF Remote" (might say something about userspace, not in front of my machine at the moment).

---

### Post by daninca on 2011-04-02
I think you're mistaken.  I see lircd.conf and lircrc in that post, but no hardware.conf.
-Dan

---

### Post by williammanda on 2011-04-02
> **daninca said:**
> I think you're mistaken.  I see lircd.conf and lircrc in that post, but no hardware.conf.
-Dan

There isn't a hardware conf but this tells you which one to pick. After you do that you will have what everyone else has as their hardware conf. Please choose the following selection in Mythbuntu remote setup:

"ATI/NVidia/X10 I & II RF Remote"

---

### Post by daninca on 2011-04-02
I tried that, but I just did it again.  What I found out is that the mythbuntu infrared configuration will edit what is there, not replace it.

I uninstalled lirc (and mythbuntu-lirc-generator), remove /etc/lirc/*.conf, re-installed the above, and then ran the mythbuntu-control-center and configured infrared to be "ATI/NVidia/X10 RF Remote (userspace)".

I've attached the file that I got after all that.  It still doesn't work for me.  irw shows nothing. myth ignores the remote.  Rebooting (with power cycle) didn't help.

Any ideas on how to get this working?

Here is the system info:
# uname -a
Linux vonbraun 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

Here are the IR modules that are loaded:
# lsmod | grep ir
ir_lirc_codec           3888  0 
lirc_dev               11209  1 ir_lirc_codec
ir_sony_decoder         2381  0 
ir_jvc_decoder          2442  0 
ir_rc6_decoder          3018  0 
ir_rc5_decoder          2474  0 
ir_nec_decoder          2442  0 
ir_common               6155  1 cx88xx
ir_core                16906  11 rc_hauppauge_new,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx,ir_common

Here is how the device shows up on USB:
# lsusb | grep X10
Bus 002 Device 002: ID 0bc7:0008 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)

-Dan

---

### Post by daninca on 2011-04-02
I got this working using the lirc_atiusb driver module.  Maybe there is a problem with the atilibusb stuff under x64?

I installed the lirc-modules-source package, reverted the files listed below to my 10.04 versions, and rebooted (for some reason you have to reboot before the modules build by lirc-modules-source will load).  I now get output from irw and myth works properly.

I had to configure these files (attached):
/etc/lirc/hardware.conf
/etc/lirc/lircd.conf
/etc/modprobe.d/lirc-blacklist.conf (originally named lirc-blacklist, but modprobe complains if it name *.conf)
~/.lirc/mythtv (which is linked to ~/.mythtv/lircrc)

Thanks!
-Dan

---

### Post by forkd on 2011-05-05
My remote is working but the repeat option is messed up.  No matter what I change repeat to it seems to repeat 4 times for each press.

Any ideas???

I resolved this via the lircd.conf file ...


add suppress_repeat x to the lircd.conf

Since each keypress was registering 5 responses I added suppress_repeat 4 to the paramaters and it works fine.

---

