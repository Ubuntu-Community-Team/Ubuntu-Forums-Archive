---
title: "Prev.Ch on pvr-350 remote"
date: 2008-02-12
forum: Mythbuntu
---

### Post by incubi on 2008-02-12
Hello everyone, 

I’m having a little trouble with mythtv and the pvr-350 remote with colored buttons at the bottom. I have looked for help but no luck. 

My myth system is a new install and is working well the only issue is when I try to get the Prev.Ch to work with the H key for last ch. irw sees the button just fine but myth can’t. Here is the entry.

begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Prev.Ch
    config = H
    repeat = 0
    delay = 0
end


Everything else is working great its just this and I can’t understand what I have missed. Can you help?

Thank you

---

### Post by incubi on 2008-02-18
No replies wow! Well, found the answer thanks anyway.

---

### Post by Tom Mann on 2008-04-21
I found this ~/.mythtv/lircrc which supposedly works - I'm going to try it now...

You need to:

1. Open up a terminal and type
```
cd ~/.mythtv
mv lircrc lircrc.backup
nano lircrc
```

2. Copy the text below and paste it into nano
```
# ~/.mythtv/lircrc
#
# MythTV native LIRC config file for
# the grey Hauppauge remote
#

# Power Off/Exit
begin
prog = mythtv
button = POWER
config = Esc
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

begin
prog = mythtv
button = VOL+
repeat = 3
config = Right
end

begin
prog = mythtv
button = VOL-
repeat = 3
config = Left
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
button = PLAY
config = P
end

# Stop
begin
prog = mythtv
button = STOP
config = Esc
end

# Pause
begin
prog = mythtv
button = PAUSE
repeat = 3
config = P
end

# fast reverse
begin
prog = mythtv
button = MUTE
repeat = 3
config = <
end

# fast forward
begin
prog = mythtv
button = FULL
repeat = 3
config = >
end

# Skip backward (10 min default)
begin
prog = mythtv
button = REWIND
repeat = 3
config = PgUp
end

# Skip forward (10 min default)
begin
prog = mythtv
button = FORWARD
repeat = 3
config = PgDown
end

# Fast forward (30 sec default)
begin
prog = mythtv
button = SKIP
repeat = 3
config = Right
end

# Rewind (10 sec default)
begin
prog = mythtv
button = REPLAY
repeat = 3
config = Left
end

# Record
begin
prog = mythtv
button = RECORD
repeat = 3
config = R
end

begin
prog = mythtv
button = BLANK
repeat = 3
config = Enter
end

begin
prog = mythtv
button = BACK/EXIT
repeat = 3
config = H
end

begin
prog = mythtv
button = RED
repeat = 3
config = H
end

begin
prog = mythtv
button = YELLOW
repeat = 3
config = H
end

begin
prog = mythtv
button = GREEN
repeat = 3
config = /
end

begin
prog = mythtv
button = BLUE
repeat = 3
config = ?
end

begin
prog = mythtv
button = MENU
repeat = 3
config = O
end

# Bring up OSD info
begin
prog = mythtv
button = GO
repeat = 3
config = I
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


```

3. Press CTRL and X, then press Y to save.

I don't have a PVR350 but I do have the same remote, and dug this up from a LUG (I can't remember which :()

Hope this helps.

Tom

---

### Post by incubi on 2008-04-21
Hey thanks for the reply! :) 

I was able to get it to work but it was a code issue

Prev.Ch                  0x0000000000001792

in profile  Hauppauge_350

I'm not sure if this is the code that worked or if I had to change it. I don't have my myth box running right now and I don't remember. I did get info here 

[http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

---

### Post by Tom Mann on 2008-04-21
Nice one - it turns out Hauppauge are releasing the same look remote with different keycodes so it doesn't look like I could have helped :( but I've managed to fix mine now too so all is good :)

---

