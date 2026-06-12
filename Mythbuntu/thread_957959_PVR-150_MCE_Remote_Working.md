---
title: "PVR-150 MCE Remote Working"
date: 2008-10-24
forum: Mythbuntu
---

### Post by fryed_1 on 2008-10-24
After a week of trial and error and working with the various threads out there, finally got this working so figured I'd post my solution.

This is for the the PVR-150 MCE version with the four My-xxxx buttons at the top, not the colored buttons at the bottom.  Remote is labeled RC6 on the back (says gateway remote, but should be the same as other similar remotes)  The receiver is a USB model that lists as an SMK receiver with **lsusb**.

I was having the hardest time with the different PVR-150 combos out there figuring out which modules to load and get working.

When setting up in the control center, I set it up as a "Hauppauge TV Card" to get the initial files there and below is what was modified.  This is assuming MythTV was installed (I used Mythbuntu install CD 8.04) and your remote/receiver works and is, at least, recognized by **lsusb**.

I don't know if this step is required because I added in during one of the steps, but it doesn't seem to break anything and I don't want to remove it for fear of breaking it again.

/etc/modules.d/aliases:  add anywhere
```
alias char-major-61 lirc_mceusb2
```

These are required:

/etc/lirc/hardware.conf
Change:
```
REMOTE_MODULES="lirc_i2c lirc_dev"
```
To:
```
REMOTE_MODULES="lirc_mceusb2"
```

Change:
```
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
```
To:
```
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
```

/etc/lirc/lircd.conf
Change:
```
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge
```
To:
```
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb
```


Now if you can see the receiver in **lsusb**:
```
Bus 002 Device 002: ID 0609:031d SMK Manufacturing, Inc.
```

You should have IRW working now.

```

root@mce:/etc/lirc# irw
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07bf3 00 Power mceusb
000000037ff07bf3 01 Power mceusb

```



That's good, but MythTV will still not recognize the remote.  here's where I screwed up for about an hour before I found my mistake.  All the online documents say to add the **lircrc** file to **~/.mythtv**.  I assumed, in my late-night half-drunk state that meant the /home/mythtv directory.  Wrong!  Add it to whatever user your PC boots up into MythTV (if it's set to automatically load up MythTV like mine is).  To be safe, add it to any user's home directory you think will login and use MythTV

On my system... [b]/home/[user]/.mythtv/lircrc is a symbolic link to /home/[user]/.lirc/mythtv

/home/[user]/.lirc/mythtv
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
config = S
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
button = ChanUp
repeat = 3
config = Up
end

# Channel Down
begin
prog = mythtv
button = ChanDown
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
config = F9
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
button = Next
repeat = 3
config = End
end

# Skip backward (10 min default)
begin
prog = mythtv
button = Previous
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
button = DVD
repeat = 3
config = M
end

# Scroll up
begin
prog = mythtv
button = VolUp
repeat = 3
config = F11
end

# Scroll down
begin
prog = mythtv
button = VolDown
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
begin
prog = mplayer
button = REW
repeat = 3
config = seek -10
end

# Seek forward 30 seconds
begin
prog = mplayer
button = FFW
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = BACK/EXIT
repeat = 3
config = quit
end

# Seek forward 10 minutes
begin
prog = mplayer
button = SKIP
repeat = 3
config = seek +600
end

# Seek backward 10 minutes
begin
prog = mplayer
button = REPLAY
repeat = 3
config = seek -600
end

# Toggle full-screen
begin
prog = mplayer
button = FULL
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
config = EventLeft
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

Now a note on the above.  Only half my remote works right now.  I haven't completed the mapping for it.  The original file (sorry original owner of the file, I forget where I found it) was someone else's and I've been modifying it to suit my needs.  Here's how that works:

For all the **prog = mythtv** entries, this applies since they are used by the MythTV FrontEnd.  Here's a quick breakdown:

begin *- start of this button*
prog = mythtv *- defines which program the button affects*
button = TV *- corresponds to the button pressed on the remote*
repeat = 3 *- ????  Not sure, I leave this set as is*
config = F5 *- corresponds to the key press on the keyboard*
end *- end of this button*

Ok now... to setup buttons, I use my laptop connected via SSH to the backend.  I run putty, then start up irw on it to monitor remote keys.  Now go to setup in MythTV FrontEnd and edit keys.  Here you will be able to assign any MythTV function available to a key on your keyboard.  With the example above:

The MyTv button on my remote, through IRW shows up as:
```
000000037ff07bb9 00 TV mceusb
```

That's how I knew the **button =** line.

Now in your MythTV keys setup, you'll see that the F5 key starts up LiveTV (or you can assign it so if it isn't already).

Put two and two together and now the My TV button the remote equals F5 on the keyboard.



Repeat this all the way down the line for each button on the remote, assigning each as you wish.


I was so happy to finally get a remote working, that I haven't yet assigned anything below the Guide and LiveTV buttons (basically all the individual number buttons), but with what's above, you should be able to handle that yourself now.


As I work more with the IR blaster, I'll try to update this post with instructions on it as well.

---

### Post by iCkerous on 2009-10-29
I have a couple questions since I'm having the same problem you solved.  I've followed your walkthrough.  I have LIRC working and irw returns correctly.  But for some reason I cannot get the remote to work in Mythtv.  I have edited the Hardware.conf to no avail.  My Lircrc file is correct (per what I can see.)

Any suggestions?

---

