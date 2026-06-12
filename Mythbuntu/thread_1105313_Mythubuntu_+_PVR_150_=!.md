---
title: "Mythubuntu + PVR 150 =!"
date: 2009-03-24
forum: Mythbuntu
---

### Post by swraman on 2009-03-24
Hi,

I am using a Hauppauge PVR150 with the remote that came with it.

The remote doesn't work.

Under IR settings, I tried using the "Haupauge TV Tuner" remote option.  It doesn't work.

Any ideas?

Thanks

(and I know ive sen plenty of forum posts on this, but i have tried them to no avail.)

---

### Post by David Grigor on 2009-03-24
If your trying to use the IR receiver port that's built onto the card it likely isn't going to work.  There are no linux drivers for it. Well, for sure doesn't work with the Hauppauge 1250, I just assuming same situation.  

The remote control itself is compatible but you will need to get another IR receiver/transceiver.  I picked one up from ebay where a guy has hundreds of them from gateway for $17 w/free shipping. It works fine along with the lrc remote "Haupauge TV Tuner" selection.

---

### Post by swraman on 2009-03-24
I am attempting to use the built in IR port.

is this true, is there really no linux support for this device?

:(

Back to Windows then...

---

### Post by boof1988 on 2009-03-24
> **David Grigor said:**
> If your trying to use the IR receiver port that's built onto the card it likely isn't going to work.  There are no linux drivers for it. Well, for sure doesn't work with the Hauppauge 1250, I just assuming same situation.

Maybe these links can shed some light...

[http://www.mythtv.org/wiki/PVR150_Remote](http://www.mythtv.org/wiki/PVR150_Remote)

[http://www.mythtv.org/wiki/Hauppauge_PVR-150](http://www.mythtv.org/wiki/Hauppauge_PVR-150)

---

### Post by swraman on 2009-03-25
I ran through the instructions there, still not working.

The remote does have drivers for Linux, when I ran "cat /dev/lirc0" the computer recognized keypresses from the remote in console.

Then I tried to finish the rest of the tutorial, used the lircd.conf supplied there, and the lircrc linked there.  But it doesnt work still.

Also, when I run the "irw" command, nothing happens, it just brings up the prompt again.

Any advice?

Thanks

---

### Post by zagor on 2009-03-25
I have a mythbuntu 8.04 box with PVR-150 as well.
I had to get the right lirc.conf and lircrc for my remote.
You might be aware that there are different reotes coming bundled with PVR-150.
Be sure you are using the right files. In my remote, behind the batteries, there's a sticker with the remote name: A415-HPG.
The settings coming with mythbuntu does not work for this remote, but at least the irw command should show something, I guess.

The settings in knoppmyth, instead, work perfectly.
So in the past I just grabbed the files in knoppmyth and copied into my mythbuntu 7.10. When upgraded to 8.04 everything was still fine.

Following, my .lircrc, .lirc/mythtv and lircd.conf:

.lircrc
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 

```

.lirc/mythtv
```
# MythTV LIRC config file for the gray Hauppauge remote
# Sticker on the inside of battery compartment
#     A415-HPG
#     1004  032400
#
# /home/mythtv/.mythtv/lircrc
#
#
### RESET THE MYTH BOX or REBOOT IT
# 1 click is reset front end, 2 clicks is reboot
#
begin
   prog = irexec
   button = Power
   config = /home/mythtv/scripts/mypower.sh &
end
#
### MYTHTV SETTINGS FOR IT'S CONTROL
#
# Program Guide
begin
   remote = grayHauppauge
   prog = mythtv
   button = Guide
   config = F2
end
#
# TV Recording Playback
begin
   remote = grayHauppauge
   prog = mythtv
   button = Videos
   config = Shift+Ctrl+F3
end
#
# Live TV
begin
   remote = grayHauppauge
   prog = mythtv
   button = TV
   config = Shift+Ctrl+F2
end
#
# MythWainMenu
begin
   remote = grayHauppauge
   prog = mythtv
   button = Go
   config = Shift+Ctrl+F7
end
#
# MythGallery
begin
   remote = grayHauppauge
   prog = mythtv
   button = Pictures
   config = Shift+Ctrl+F5
end
#
# MythMusic
begin
   remote = grayHauppauge
   prog = mythtv
   button = Music
   config = Shift+Ctrl+F4
end
#
# MythVideo
begin
   remote = grayHauppauge
   prog = mythtv
   button = Radio
   config = Shift+Ctrl+F6
end











#
# Previous Channel
begin
   remote = grayHauppauge
   prog = mythtv
   button = Prev-Channel
   config = H
end
#
# Channel Up
begin
   remote = grayHauppauge
   prog = mythtv
   button = Channel-UP
   repeat = 3
   config = Up
end

# Channel Down
begin
 prog = mythtv
 button = Channel-DOWN
 repeat = 3
 config = Down
end

# OK/Select
begin
 prog = mythtv
 button = OK
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
config = Esc
end

# Escape/Exit/Back
begin
prog = mythtv
button = Back-Exit
config = Esc
end

# Power Off/Exit
# begin
# prog = mythtv
# button = Power
# config = Esc
# end

# Red means stop!
#begin
#prog = mythtv
#button = red
#config = Esc
#end

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
config = F9
end

begin
prog = mythtv
button = UP
repeat = 3
config = Up
end

begin
prog = mythtv
button = RIGHT
repeat = 3
config = Right
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




# Fast forward (while viewing)
begin
prog = mythtv
button = Forward
repeat = 3
config = >
end

# Rewind (while viewing)
begin
prog = mythtv
button = Rewind
repeat = 3
config = <
end

# Skip forward (10 min default)
begin
prog = mythtv
button = Next
repeat = 3
config = PgDown
end

# Skip backward (10 min default)
begin
prog = mythtv
button = Previous
repeat = 3
config = PgUp
end

# Record
begin
prog = mythtv
button = Record
repeat = 3
config = R
end

# Delete
begin
prog = mythtv
button = red
repeat = 3
config = D
end

# OSD browse

begin
prog = mythtv
button = Menu
repeat = 3
config = O
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
button = Guide
repeat = 3
config = M
end

# Volume-Up
begin
prog = mythtv
button = Volume-UP
repeat = 3
config = ]
end

# Volume-Down
begin
prog = mythtv
button = Volume-DOWN
repeat = 3
config = [
end

# Bring up OSD info
begin
prog = mythtv
button = Go
repeat = 3
config = I
end

# Change display aspect ratio
#begin
#prog = mythtv
#button = FULL
#repeat = 3
#config = W
#end

# Seek to previous commercial cut point
begin
prog = mythtv
button = yellow
repeat = 3
config = Q
end

# Seek to next commercial cut point
begin
prog = mythtv
button = blue
repeat = 3
config = Z
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

#
### MPlayer lirc setup
#
# Show OSD
begin
prog = mplayer
button = Menu
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = Pause
repeat = 3
config = pause
end

# Skip ahead a minute if playing
# If paused, resume playing
begin
prog = mplayer
button = Play
repeat = 3
config = seek +1
end

# Stop playback and exit
begin
prog = mplayer
button = Stop
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = Mute
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = Rewind
repeat = 3
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = Forward
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = Back-Exit
repeat = 3
config = quit
end

# Seek forward 10 minutes
begin
prog = mplayer
button = Next
repeat = 3
config = seek +600
end

# Seek backward 10 minutes
begin
prog = mplayer
button = Previous
repeat = 3
config = seek -600
end

# Toggle full-screen
#begin
#prog = mplayer
#button = FULL
#repeat = 3
#config = vo_fullscreen
#end
#
#
### XINE CONFIGURATION
#
##
# xine key bindings.
# Automatically generated by xine-ui version 0.99.2.
##

# start playback
begin
   button = Play
   prog   = xine
   repeat = 3
   config = Play
end

# playback pause toggle
begin
   button = Pause
   prog   = xine
   repeat = 3
   config = Pause
end

# stop playback
begin
   button = Stop
   prog   = xine
   repeat = 3
   config = Stop
end

# take a snapshot
begin
   button = Record
   prog   = xine
   repeat = 3
   config = Snapshot
end

# eject the current medium
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = Eject
end

# set position to -60 seconds in current stream
begin
   button = Previous
   prog   = xine
   repeat = 3
   config = SeekRelative-60
end

# set position to +60 seconds in current stream
begin
   button = Next
   prog   = xine
   repeat = 3
   config = SeekRelative+60
end

# set position to -30 seconds in current stream
begin
   button = Rewind
   prog   = xine
   repeat = 3
   config = SeekRelative-30
end

# set position to +30 seconds in current stream
begin
   button = Forward
   prog   = xine
   repeat = 3
   config = SeekRelative+30
end

# set position to +7 and -7 seconds in current stream
begin
   button = 1
   prog   = xine
   repeat = 3
   config = SeekRelative-7
end

begin
   button = 2
   prog   = xine
   repeat = 3
   config = SeekRelative+7
end

begin
   button = 4
   prog   = xine
        repeat = 3
   config = SetPosition40%
end

begin
   button = 5
   prog   = xine
   repeat = 3
   config = SetPosition70%
end

begin
   button = xxxx
   prog   = xine
   repeat = 3
   config = SpeedFaster
end

begin
   button = DOWN
   prog   = xine
   repeat = 3
   config = SpeedSlower
end

begin
   button = OK
   prog   = xine
   repeat = 3
   config = SpeedReset
end

# increment audio volume
begin
   button = Volume-UP
   prog   = xine
   repeat = 3
   config = Volume+
end

# decrement audio volume
begin
   button = Volume-DOWN
   prog   = xine
   repeat = 3
   config = Volume-
end

# audio muting toggle
begin
   button = Mute
   prog   = xine
   repeat = 3
   config = Mute
end

# set video output window to 100%
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = Window100
end

# set video output window to 200%
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = Window200
end

# zoom in
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = ZoomIn
end

# zoom out
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = ZoomOut
end

# fullscreen toggle
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = ToggleFullscreen
end

# Xinerama fullscreen toggle
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = ToggleXineramaFullscr
end

# jump to Title Menu
begin
   button = Go
   prog   = xine
   repeat = 3
   config = TitleMenu
end

# jump to Root Menu
begin
   remote = xxxxx
   button = xxxxx
   prog   = xine
   repeat = 3
   config = RootMenu
end

# menu navigate up
begin
   button = UP
   prog   = xine
   repeat = 3
   config = EventUp
end

# menu navigate down
begin
   button = DOWN
   prog   = xine
   repeat = 3
   config = EventDown
end

# menu navigate left
begin
   button = LEFT
   prog   = xine
   repeat = 3
   config = EventLeft
end

# menu navigate right
begin
   button = RIGHT
   prog   = xine
   repeat = 3
   config = EventRight
end

# menu navigate select
begin
   button = yellow
   prog   = xine
   repeat = 3
   config = Eventselect
end

# visibility toggle of stream info window
begin
   button = Guide
   prog   = xine
   repeat = 3
   config = StreamInfosShow
end

# display stream information using OSD
begin
   button = Menu
   prog   = xine
   repeat = 3
   config = OSDStreamInfos
end



# increase brightness by 10
begin
   button = Channel-UP
   prog   = xine
   repeat = 3
   config = BrightnessControl+
end

# decrease brightness by 10
begin
   button = Channel-DOWN
   prog   = xine
   repeat = 3
   config = BrightnessControl-
end

# quit the program
begin
   button = Back-Exit
   prog   = xine
   repeat = 3
   config = Quit
end

##
# End of xine key bindings.
## 

begin
    remote = grayHauppauge
    prog = vlc
    button = DOWN
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Pause
    config = key-play-pause
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = OK
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Volume-UP
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Volume-DOWN
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = UP
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Channel-UP
    config = key-jump+short
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Channel-DOWN
    config = key-jump-short
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = RIGHT
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Forward
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = LEFT
    config = key-nav-left
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Next
    config = key-chapter-next
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Previous
    config = key-chapter-prev
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Menu
    config = key-disc-menu
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Music
    config = key-audio-track
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Pictures
    config = key-subtitle-track
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = TV
    config = key-aspect-ratio
    repeat = 0
    delay = 0
end

begin
    remote = grayHauppauge
    prog = vlc
    button = Videos
    config = key-deinterlace
    repeat = 0
    delay = 0
end
```

lircd.conf
```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.7.0(hauppauge) on Thu Jan 13 17:31:41 2005
#
# contributed by Per Jonsson (per at pjd dot nu)
#
# brand:                       Hauppauge
# model no. of remote control: PVR150
# devices being controlled by this remote: PVR150
#

begin remote

  name  hauppauge_pvr150
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           0    0
  zero          0    0
  gap          200000
  min_repeat      4
  toggle_bit      2

      begin codes
          POWER                    0x00000000000017BD
          GO                       0x00000000000017BB
          TV                       0x000000000000179C
          VIDEOS                   0x0000000000001798
          MUSIC                    0x0000000000001799
          PICTURES                 0x000000000000179A
          GUIDE                    0x000000000000179B
          RADIO                    0x000000000000178C
          OK                       0x00000000000017A5
          UP                       0x0000000000001794
          LEFT                     0x0000000000001796
          RIGHT                    0x0000000000001797
          DOWN                     0x0000000000001795
          BACK/EXIT                0x000000000000179F
          MENU                     0x000000000000178D
          PREVCH                   0x0000000000001792
          MUTE                     0x000000000000178F
          VOL+                     0x0000000000001790
          VOL-                     0x0000000000001791
          CH+                      0x00000000000017A0
          CH-                      0x00000000000017A1
          RECORD                   0x00000000000017B7
          STOP                     0x00000000000017B6
          PLAY                     0x00000000000017B5
          REW                      0x00000000000017B2
          FFW                      0x00000000000017B4
          REPLAY                   0x00000000000017A4
          PAUSE                    0x00000000000017B0
          SKIP                     0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          *                        0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          RED                      0x000000000000178B
          GREEN                    0x00000000000017AE
          YELLOW                   0x00000000000017B8
          BLUE                     0x00000000000017A9
      end codes

end remote

```

but since I'm not that sure that this is ctually the lircd.conf I'm using (I'm not on the box, now), I'll post also the other lircd.conf I have available. Try both.

lircd.conf
```

begin remote
  name            grayHauppauge
  bits            13
  flags           RC5
  eps             30
  aeps            100
  one             0 0
  zero            0 0
  gap             200966

  begin codes
       blue            0x00000000000017A9
       yellow          0x0000000000001FB8
       green           0x00000000000017AE
       red             0x0000000000001F8B
       hash            0x000000000000178E
       star            0x0000000000001F8A
       0               0x0000000000001780
       9               0x0000000000001F89
       8               0x0000000000001788
       7               0x0000000000001F87
       6               0x0000000000001786
       5               0x0000000000001F85
       4               0x0000000000001784
       3               0x0000000000001F83
       2               0x0000000000001782
       1               0x0000000000001F81
       Pause           0x00000000000017B0
       Next            0x0000000000001F9E
       Previous        0x00000000000017A4
       Play            0x0000000000001FB5
       Forward         0x00000000000017B4
       Rewind          0x0000000000001FB2
       Stop            0x00000000000017B6
       Record          0x0000000000001FB7
       Channel-DOWN    0x00000000000017A1
       Channel-UP      0x0000000000001FA0
       Volume-DOWN     0x0000000000001791
       Volume-UP       0x0000000000001F90
       Mute            0x000000000000178F
       Prev-Channel    0x0000000000001F92
       Menu            0x000000000000178D
       Back-Exit       0x0000000000001F9F
       OK              0x00000000000017A5
       DOWN            0x0000000000001F95
       RIGHT           0x0000000000001797
       LEFT            0x0000000000001F96
       UP              0x0000000000001794
       Radio           0x0000000000001F8C
       Guide           0x000000000000179B
       Pictures        0x0000000000001F9A
       Music           0x0000000000001799
       Videos          0x0000000000001F98
       TV              0x000000000000179C
       Go              0x0000000000001FBB
       Power           0x00000000000017BD

  end codes

end remote
```

Hope it helps

---

### Post by swraman on 2009-03-25
Hi,

I have teh same remote as you do, hwever I tried both of the configurations you have and it still didnt work.

Do you know if you ran any other commands to ge the thing to work?

and does Knopmyth work easily with this remote?  If so I may just end up doing a HD installation of that...

Thanks

Raman

---

### Post by zagor on 2009-03-25
I haven't done anything more than copying the files from knoppmyth to mythbuntu. Than I did just some tuning of the remote keys, to get exactly the behaviour I needed.

But since the begninning my remote WAS working with mythbuntu 7.10, only most keys where doing nothing and others where not doing what they where meant to.
Therfore, once changed to the right codes and the right lircrc, everything was fine.

My guess here is that you have a broken IR receiver (or that you have connected to the wrong socket...). Could be?

Try a Knoppmyth live version on your system and check if the remote is working. If not, it's probably an HW issue on the IR receiver. 
In my case, the knoppmyth R5F27 was working perfectly with my remote, out of the box.

---

### Post by boof1988 on 2009-03-25
This is just a wild guess...  But what is the quality of the batteries in the remote?  If they're old or almost discharged, that could cause bad behavior.

Here's another wild idea...

Mythbuntu-lirc-generator may be of use to you or someone else in this situation.

[http://packages.ubuntu.com/gutsy/mythbuntu-lirc-generator](http://packages.ubuntu.com/gutsy/mythbuntu-lirc-generator)

---

### Post by David Grigor on 2009-03-25
if you can see key presses but nothing with irw then your not using the right lircd.conf

What I did to find which one I really needed was to run the irrecord command and follow the prompts. Then looked at the beginning of that file that had the bits, flags etc similiar to this part of the earlier example:

begin remote

  name  hauppauge_pvr150
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           0    0
  zero          0    0
  gap          200000
  min_repeat      4
  toggle_bit      2


and found an existing lirc.conf that had the closest match to my output and loaded that one. Then irw would show the keys pressed.

---

### Post by swraman on 2009-03-25
I do not think the device is broken/low batteries, and I do think it is getting recognized.  I used to use this device on a Windows machine with GB-PVR and it worked fine.

If I run "cat /dev/lirc0" Terminal pauses, and I get an output anytime i press a button on the remote.

But, when I run "irw" (after running "lircd"), nothing happens.  My understanding is that it is suposed to pause, and I am suposed to be able to see an output on the screen anytime I press a button in my remote.  But after running "irw", nothing happens, and I am returned to the prompt.

I tried using "irrecord", but there was a problem with that as well.
Initialy, it said to press any button mon the remote, that went fine.
Then it said to press another button, but before I could it asked me for the button's name.  I type it in, an again it repeats (briefly says to press a button, and before I do it moves on to ask me what the name of the button is).

Any other ideas?

Thanks again for all your guys' help.

---

### Post by scooter29 on 2009-03-27
If you're just trying to use the remote, not the irblaster change settings in Mythbuntu Control Centre. Select Hauppauge Tv Card, make buttons, unselect irblaster options and apply. It should work when you reboot computer. Make sure plug pushed all the way in back of card (fully seated)! If you want to use the remote and blaster follow these directions.

[http://ubuntuforums.org/showthread.php?t=1094558]("http://ubuntuforums.org/showthread.php?t=1094558"):)

---

### Post by bblboy54 on 2009-03-28
Are you using the 32-bit version or the 64-bit version?  There are issues with LIRC in general on 64-bit kernels and this especially affects the PVR-150's.

---

### Post by bblboy54 on 2009-03-28
> **David Grigor said:**
> If your trying to use the IR receiver port that's built onto the card it likely isn't going to work.  There are no linux drivers for it. Well, for sure doesn't work with the Hauppauge 1250, I just assuming same situation.  


Not the case.  The IR blaster and receiver on the PVR-150 (Retail) works fine on 32-bit kernels.  This is NOT true for the MCE version.  The Hauppauge 1250 is also a different animal and I can't say whether it works or not.

---

### Post by swraman on 2009-03-29
> **scooter29 said:**
> If you're just trying to use the remote, not the irblaster change settings in Mythbuntu Control Centre. Select Hauppauge Tv Card, make buttons, unselect irblaster options and apply. It should work when you reboot computer. Make sure plug pushed all the way in back of card (fully seated)! If you want to use the remote and blaster follow these directions.

[http://ubuntuforums.org/showthread.php?t=1094558]("http://ubuntuforums.org/showthread.php?t=1094558"):)

Tried it.  Didn't work.  Could be that i messed with my lirc files earlier...should I just format it and start over?

---

### Post by zagor on 2009-03-30
Have you tried with knoppmyth, yet?
Just to understand if it's a "general" issue (i.e. mythtv or hardware) or if it is more related to mythbuntu itself (i.e. config files).
When you run knoppmyth, you'll have an option of running it as a frontend.
It should give you a live environment and your remote should work.
I guess.

---

