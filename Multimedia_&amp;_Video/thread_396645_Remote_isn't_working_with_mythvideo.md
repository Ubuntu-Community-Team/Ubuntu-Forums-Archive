---
title: "Remote isn't working with mythvideo"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by hansoffate on 2007-03-29
Hi guys,

    I have been trying to get my remote to work with either xine or mplayer.  I checked my lircrc and it seems like everything is configured correctly.  I'll post the relevant info.

LIRCRC
```
# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the new grey Hauppauge remote
#
# Modified from Jarod Wilson's which came from Jeff Campbell's
# By Brad Templeton


# Here we have the jump point commands.  They only work if you have
# defined function keys for these jump points.  For me the most
# common command is the menu of recordings, so I put that on "videos"
# even though that's counter-intuitive

begin
prog = mythtv
button = TV
repeat = 3
config = F5
end

begin
prog = mythtv
button = Videos
repeat = 3
config = F2
end

# Not yet defined
begin
prog = mythtv
button = Music
repeat = 3
config = Up
end

# Given another function for now, I don't use mythgallery
begin
prog = mythtv
button = Pictures
repeat = 3
config = F
end

begin
prog = mythtv
button = Guide
repeat = 3
config = F3
end

# I stuck the "todo" list on here as Myth has no radio function
begin
prog = mythtv
button = Radio
repeat = 3
config = F4
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
button = Ok
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
button = Back/Exit
config = Esc
end

# Power Off/Exit
begin
prog = mythtv
button = Power
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
button = Rewind
repeat = 3
config = <
end

# Rewind (10 sec default)
begin
prog = mythtv
button = Forward
repeat = 3
config = >
end

# Skip forward (10 min default)
begin
prog = mythtv
button = SkipForward
repeat = 3
config = End
end

# Skip backward (10 min default)
begin
prog = mythtv
button = Replay/SkipBackward
repeat = 3
config = Home
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
button = Red
repeat = 3
config = D
end

# Decrease play speed
begin
prog = mythtv
button = Green
repeat = 3
config = J
end

# Display EPG while in live TV,
# View selected show while in EPG
begin
prog = mythtv
button = Menu/i
repeat = 3
config = m
end

# Scroll up
begin
prog = mythtv
button = Volume-UP
repeat = 3
config = F11
end

# Scroll down
begin
prog = mythtv
button = Volume-DOWN
repeat = 3
config = F10
end

# Bring up OSD info
begin
prog = mythtv
button = Go
repeat = 3
config = I
end

# Change display aspect ratio
begin
prog = mythtv
button = Prev-Channel
repeat = 3
config = W
end

# double speed watch
begin
prog = mythtv
button = Yellow
repeat = 3
config = J
end

# change tuners
begin
prog = mythtv
button = hash
repeat = 3
config = Y
end

# Bring up Time stretch
begin
prog = mythtv
button = Blue
repeat = 3
config = A
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
button = MENU/i
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
button = STOP
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
#begin
#prog = mplayer
#button = Rewind
#repeat = 3
#config = seek -10
#end

# Seek forward 30 seconds
#begin
#prog = mplayer
#button = Forward
#repeat = 3
#config = seek +30
#end

# Quit
begin
prog = mplayer
button = BACK/EXIT
repeat = 3
config = quit
end

# Seek forward 10 minutes
#begin
#prog = mplayer
#button = SkipForward
#repeat = 3
#config = seek +600
#end

# Seek backward 10 minutes
#begin
#prog = mplayer
#button = Replay/SkipBackward
#repeat = 3
#config = seek -600
#end

# Toggle full-screen
begin
prog = mplayer
button = FULL
repeat = 3
config = vo_fullscreen
end

begin
     button = VOL+
     prog = mplayer
     config = volume 1
     repeat = 1
end

begin
     button = VOL-
     prog = mplayer
     config = volume -1
     repeat = 1
end

begin
     button = 1
     prog = mplayer
     config = seek -10
end
begin
     button = 4
     prog = mplayer
     config = seek -60
end
begin
     button = 3
     prog = mplayer
     config = seek 10
end
begin
     button = 6
     prog = mplayer
     config = seek 60
end
begin
     button = 7
     prog = mplayer
     config = audio_delay +0.1
end
begin
     button = 9
     prog = mplayer
     config = audio_delay -0.1
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
button = OFF
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
button = CH+
repeat = 3
config = EventUp
end

begin
prog = xine
button = CH-
repeat = 3
config = EventDown
end

begin
prog = xine
button = VOL-
repeat = 3
config = EventLeftshortcut list
end

begin
prog = xine
button = VOL+
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
button = BACK/EXIT
repeat = 3
config = Menu
end

begin
prog = xine
button = Yellow
repeat = 3
config = SpeedFaster
#config = SeekRelative+60
end

begin
prog = xine
button = Green
repeat = 3
config = SpeedSlower
#config = SeekRelative-60
end

begin
prog = xine
button = FULL
repeat = 3
config = Volume+
end

begin
prog = xine
button = BLANK
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
button = SKIP
repeat = 3
config = EventNext
end

begin
prog = xine
button = REPLAY
repeat = 3
config = EventPrior
end

begin
prog = xine
button = GO
repeat = 3
config = OSDStreamInfos
end

begin
prog = xine
button = RED
repeat = 3
config = Quit
end

begin
prog = xine
button = RED
repeat = 3
config = Quit
end

```

lircd
```
begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
#  gap		200000
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes
end remote

```

I think i configured mplayer correctly.  

Thanks for the help,
Hans

---

### Post by majoridiot on 2007-03-31
hey hans-

the button names are *case sensitive*... the definitions in lircrc must match exactly with your lircd.

e.g.  Play not PLAY

glad to see you still chipping away at it... :)

---

### Post by hansoffate on 2007-03-31
Heh, Thanks for the help.

-Hans

---

