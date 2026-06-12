---
title: "[SOLVED] Remote not working with mythvideo"
date: 2008-01-18
forum: Mythbuntu
---

### Post by murbanci on 2008-01-18
For some reason my remote (ATI Remote Wonder) is not working myth mythvideo.  It works fine with normal recorded video playback and while watching live TV, however when I try to watch a movie that I have downloaded, it will play and then none of the buttons on the remote will work.  Bellow is my lircrc file.  Any help would be appreciated.

```
#
# MythTV native LIRC config file for
# the ATI-Wonder Remote
# using lirc_atiusb driver
#

begin
prog = mythtv
button = a
config = E
repeat = 2
end

begin
prog = mythtv
button = b
config = O
repeat = 2
end

#begin
#prog = mythtv
#button = tv
#config = Key Alt-T CurrentWindow
#repeat = 2
#end

begin
prog = mythtv
button = stop
config = Esc
repeat = 2
end

begin
prog = mythtv
button = fastforward
config = Right
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = max_window
config = V
repeat = 2
end

begin
prog = mythtv
button = pause
config = P
repeat = 2
end

begin
prog = mythtv
button = play
config = P
repeat = 2
end

begin
prog = mythtv
button = mute
config = F9
repeat = 2
end

begin
prog = mythtv
button = vol-down
config = F10
repeat = 2
end

begin
prog = mythtv
button = vol-up
config = F11
repeat = 2
end

begin
prog = mythtv
button = f
config = PgDown
repeat = 2
end

begin
prog = mythtv
button = d
config = PgUp
repeat = 2
end

begin
prog = mythtv
button = c
config = F4
repeat = 2
end

begin
prog = mythtv
button = e
config = Esc
repeat = 2
end

begin
prog = mythtv
button = cursor-right
config = Right
repeat = 2
end

begin
prog = mythtv
button = cursor-left
config = Left
repeat = 2
end

begin
prog = mythtv
button = cursor-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = cursor-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = chan-up
config = Up
repeat = 2
end

begin
prog = mythtv
button = chan-down
config = Down
repeat = 2
end

begin
prog = mythtv
button = rewind
config = Left
repeat = 2
end

begin
prog = mythtv
button = ok
config = Enter
repeat = 2
end

begin
prog = mythtv
button = 1
config = 1
repeat = 2
end

begin
prog = mythtv
button = 2
config = 2
repeat = 2
end

begin
prog = mythtv
button = 3
config = 3
repeat = 2
end

begin
prog = mythtv
button = 4
config = 4
repeat = 2
end

begin
prog = mythtv
button = 5
config = 5
repeat = 2
end

begin
prog = mythtv
button = 6
config = 6
repeat = 2
end

begin
prog = mythtv
button = 7
config = 7
repeat = 2
end

begin
prog = mythtv
button = 8
config = 8
repeat = 2
end

begin
prog = mythtv
button = 9
config = 9
repeat = 2
end

begin
prog = mythtv
button = 0
config = 0
repeat = 2
end

begin
prog = mythtv
button = record
config = R
repeat = 2
end

begin
prog = mythtv
button = check
config = Enter
repeat = 2
end

### MPlayer lirc setup
#
# Remember to ln -s ./.mythtv/lircrc ../.lircrc for mplayer to work!

# Show OSD
begin
prog = mplayer
button = tv_on_demand
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = pause
repeat = 3
config = pause
end

begin
prog = mplayer
button = play
repeat = 3
config = pause
end

# Stop playback and exit
begin
prog = mplayer
button = stop
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = mute
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = rewind
repeat = 3
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = fastforward
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = e
repeat = 3
config = quit
end

```

---

### Post by racmar on 2008-01-18
This can happen if you have mythvideo set to use a different player other than the internal one.  try changing the player to "Internal".  see the following and search for internal: [http://www.mythtv.org/wiki/index.php?title=MythVideo&printable=yes&printable=yes](http://www.mythtv.org/wiki/index.php?title=MythVideo&printable=yes&printable=yes)

---

### Post by murbanci on 2008-01-18
thanks that worked.

---

