---
title: "lirc support mainly for mythtv"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by WhyWontThisWork on 2008-01-12
Hi im trying to use the remote from a hauppauge wintv tuner card and I cannot get the correct buttons to work.  right now I have the remote pictured on: [http://www.realcode.com/Docs/CarPC/Img/Parts/WinTV.jpg](http://www.realcode.com/Docs/CarPC/Img/Parts/WinTV.jpg) and with the default settings from mythbuntu the up down left right and ok in the navigation work as well as the numbers, nothing else works.  my current file in ~/.mythv/lircrc follows:

```


##START EDIT J 6JAN2008
begin
  remote = hauppauge_pvr
  prog = mythtv
  button = Red
  config = Esc
  repeat = 0
  delay = 0
end
begin
  remote = Hauppauge_WinTV_Nexus-S
  prog = mythtv
  button = Blue
  config = Esc
  repeat = 0
  delay = 0
end
begin
  remote = Hauppauge_350
  prog = mythtv
  button = Green
  config = Esc
  repeat = 0
  delay = 0
end
begin
  remote = Hauppauge
  prog = mythtv
  button = Red
  config = Esc
  repeat = 0
  delay = 0
end
##END EDIT J 6JAN2008
#none of the above buttons I added work
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Skip
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Replay
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ch+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Ok
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Channel-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Channel+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = FastRwd
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = FastFwd
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Volume-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Volume+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Ok
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = SkipForward
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Replay/SkipBackward
    config = Q
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Menu/i
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Ch+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Forward
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = MUTE
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = CH-
    config = PgDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = CH+
    config = PgUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = VOL-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = VOL+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Ok
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Vol-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Skip
    config = seek +15 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Vol+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Replay
    config = seek -15 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Rewind
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = mplayer
    button = Forward
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Ok
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Volume-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Up
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Volume+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Down
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Right
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = FastRwd
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = FastFwd
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = mplayer
    button = Left
    config = seek -6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = OK
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Vol-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = SkipForward
    config = seek +15 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Up
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Vol+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Down
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Replay/SkipBackward
    config = seek -15 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Right
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Rewind
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Forward
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = mplayer
    button = Left
    config = seek -6 0
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mplayer
    button = MUTE
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mplayer
    button = VOL-
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = mplayer
    button = VOL+
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Ok
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Vol-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Skip
    config = EventNext
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Vol+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Replay
    config = EvenPrior
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Rewind
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = xine
    button = Forward
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Ok
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Volume-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Up
    config = EventUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Volume+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Down
    config = EventDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Right
    config = EventRight
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = FastRwd
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = FastFwd
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = xine
    button = Left
    config = EventLeft
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Play
    config = Play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Pause
    config = Pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = OK
    config = EventSelect
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Mute
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Vol-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = SkipForward
    config = EventNext
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Stop
    config = Quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Up
    config = EventUp
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Vol+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Down
    config = EventDown
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Replay/SkipBackward
    config = EvenPrior
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Right
    config = EventRight
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Rewind
    config = SeekRelative-15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Forward
    config = SeekRelative+15
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = xine
    button = Left
    config = EventLeft
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = xine
    button = MUTE
    config = Mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = xine
    button = VOL-
    config = Volume-
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = xine
    button = VOL+
    config = Volume+
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ok
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Vol-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Vol+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Replay
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ch-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Skip
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Ch+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = vlc
    button = Forward
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Down
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Ok
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Volume-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Up
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Volume+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Channel-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Right
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Channel+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = FastRwd
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = FastFwd
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = vlc
    button = Left
    config = key-nav-left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Down
    config = key-nav-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = OK
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Vol-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Up
    config = key-nav-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Vol+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Replay/SkipBackward
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Ch-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Right
    config = key-nav-right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = SkipForward
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Ch+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Forward
    config = key-faster
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = vlc
    button = Left
    config = key-nav-left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = MUTE
    config = key-vol-mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = VOL-
    config = key-vol-down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = VOL+
    config = key-vol-up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = CH-
    config = key-prev
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = vlc
    button = CH+
    config = key-next
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Play
    config = play_pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Vol-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Menu
    config = menu
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Vol+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Back/Exit
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Rewind
    config = seek_backward
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = totem
    button = Forward
    config = seek_forward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Play
    config = play_pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Volume-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Menu
    config = menu
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Up
    config = up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Volume+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Down
    config = down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Right
    config = right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = FastRwd
    config = seek_backward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = FastFwd
    config = seek_forward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = totem
    button = Left
    config = left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Play
    config = play_pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Vol-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Menu/i
    config = menu
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Up
    config = up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Vol+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Down
    config = down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Right
    config = right
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Back/Exit
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Rewind
    config = seek_backward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Forward
    config = seek_forward
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = totem
    button = Left
    config = left
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = totem
    button = MUTE
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = totem
    button = VOL-
    config = volume_down
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = totem
    button = VOL+
    config = volume_up
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Ok
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Vol-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Menu
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Rewind
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Vol+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Back/Exit
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Forward
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = hauppauge_pvr
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Right
    config = move_right_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Ok
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Volume-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Menu
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = FastRwd
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Up
    config = move_up_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Volume+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Down
    config = move_down_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = FastFwd
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_WinTV_Nexus-S
    prog = elisa
    button = Left
    config = move_left_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Play
    config = toggle_play_pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Right
    config = move_right_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = OK
    config = activate_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Power
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Mute
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Vol-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Menu/i
    config = toggle_menu_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Rewind
    config = seek_backward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Stop
    config = stop_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Up
    config = move_up_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Vol+
    config = increment_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Down
    config = move_down_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Pause
    config = pause_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Back/Exit
    config = close_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Forward
    config = seek_forward_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Red
    config = toggle_fullscreen_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge_350
    prog = elisa
    button = Left
    config = move_left_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = elisa
    button = MUTE
    config = toggle_mute_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = elisa
    button = VOL-
    config = decrement_volume_key
    repeat = 0
    delay = 0
end

begin
    remote = Hauppauge
    prog = elisa
    button = VOL+
    config = increment_volume_key
    repeat = 0
    delay = 0
end


```
-J

---

### Post by Scorpuk on 2008-01-12
Since your remote is working I am presuming you have the incorrect names associated with the buttons.


To find out what each button is actually called in the system run the following program in a terminal window:

```
irw
```

Once this is running you can press each button you are having problems with and note down what they are called. It should be something like:


> <some sort of code> ChanUp Hauppauge-remote

To ensure you understand what it is saying try one of numeric buttons to provide an example of the output as that should be something like:

> <some sort of code> 1 Hauppauge-remote


Once you have the names for the ones that dont work you need to edit the lircrc file and change the "button=" part for each section that didnt work.


Any probs come back to the forums.


Goodluck.
If you pressed 1 ;)

---

### Post by WhyWontThisWork on 2008-01-12
when i type in irw it says connect: no such file or directory

---

### Post by wolfen69 on 2008-01-12
i found this site [http://lircconfig.commandir.com/](http://lircconfig.commandir.com/) that has pre-configured lircd.conf files. i am going to give it a try. this link [http://lircconfig.commandir.com/lircd.conf/](http://lircconfig.commandir.com/lircd.conf/) will take you directly to the download page.

---

### Post by WhyWontThisWork on 2008-01-12
I tried that with no luck

---

### Post by Scorpuk on 2008-01-13
could you open a terminal window and type the following please:


```
ls -l /dev/lirc*
```


oh yeah and post the results here :D

---

### Post by AlecJ on 2008-01-13
I have the same setup as you.

here is my lircrc file, with works just cut and past, after backing up your old file of course..

begin
    remote = NOVA-T500
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowRight
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = SkipBack
    config = Z
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelDown
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = BackExit
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ChannelUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Fwdwind
    config = >
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeDown
    config = [
    repeat = 3
    delay = 10
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = VolumeUp
    config = ]
    repeat = 3
    delay = 10
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = OK
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowUp
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = ArrowLeft
    config = Left
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = TV
    config = w
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = PrevCh
    config = h
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Power
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Pictures
    config = y
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Go
    config = n
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Radio
    config = b
    repeat = 0
    delay = 0
end

begin
    remote = NOVA-T500
    prog = mythtv
    button = Music
    config = v
    repeat = 0
    delay = 0
end

---

