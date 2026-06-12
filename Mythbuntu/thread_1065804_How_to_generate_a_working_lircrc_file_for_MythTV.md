---
title: "How to generate a working lircrc file for MythTV?"
date: 2009-02-10
forum: Mythbuntu
---

### Post by nicoloks on 2009-02-10
I have a RM200 remote which I am pretty sure is just a re-badged iMon PAD and I need a bit of help getting a working lircrc file for mythtv (or anything for that matter). 

My remote is not supported in lirc 0.8.3, so I had to uninstall it and manually upgrade to lirc 0.8.4a. Using irw I can see that every key is correctly mapped in lirc.conf, however as mythbuntu-lirc-generator is dependent on lirc it was uninstalled when I removed lirc.

Does anyone have a working lirrc file for MythTV (and Mplayer, xine & VLC) for the iMon PAD remote? Or better yet the RM200 remote? If not, how can I generate this file automatically, or must it be done manually? If manually, how do I do this?

---

### Post by mathog on 2009-02-10
> **nicoloks said:**
> 
My remote is not supported in lirc 0.8.3, so I had to uninstall it and manually upgrade to lirc 0.8.4a. Using irw I can see that every key is correctly mapped in lirc.conf, however as mythbuntu-lirc-generator is dependent on lirc it was uninstalled when I removed lirc.

I had a similar issue, perhaps this will help:

[http://ubuntuforums.org/showthread.php?t=1046371](http://ubuntuforums.org/showthread.php?t=1046371)

---

### Post by OffAxis on 2009-02-10
The lircrc file just maps the key presses in the lircd.conf file to a keypress that an application understands.
It's a fairly straightforward thing to do manually.
This should give you an idea of what it should look like:
```
#############################################
#######          DVR SWITCH 1            ####
#############################################

# begin
# prog = mythtv
# button = VOL+
# repeat = 3
# config = F11
# end

# begin
# prog = mythtv
# button = VOL-
# repeat = 3
# config = F10
# end

# begin
# prog = mythtv
# button = MUTE
# repeat = 3
# config = F9
# end

begin
prog = mythtv
button = ENTER/LAST
repeat = 3
config = H
end

begin
prog = mythtv 
button = TV_POWER
repeat = 3
config = Esc,Esc
end

# begin
# prog = mythtv
# button = TV_INPUT
# repeat = 3
# config = F
# end

begin
prog = mythtv
button = CH/PAGE_UP
repeat = 3
config = Up
end

begin
prog = mythtv
button = CH/PAGE_DOWN
repeat = 3
config = Down
end

begin
prog = mythtv
button = TH_UP
repeat = 3
config = PgDown
end

begin
prog = mythtv
button = TH_DOWN
repeat = 3
config = PgUp
end

begin
prog = mythtv
button = TIVO
repeat = 3
config = Esc
end

begin
prog = mythtv
button = WINDOW
repeat = 3
config = F2
end

begin
prog = mythtv
button = LIVE_TV
repeat = 3
config = F1
end

begin
prog = mythtv
button = RECORD
repeat = 3
config = R
end

begin
prog = mythtv
button = CLEAR
repeat = 3
config = D
end

begin
prog = mythtv
button = GUIDE
repeat = 3
config = M
end

begin
prog = mythtv
button = INFO
repeat = 3
config = I
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
button = FORWARD
repeat = 3
config = >,>,>
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
button = REWIND
repeat = 3
config = <,<,<
end

begin
prog = mythtv
button = PLAY
repeat = 3
config = Return
end

begin
prog = mythtv
button = PAUSE
repeat = 3
config = P
end

begin
prog = mythtv
button = SLOW
repeat = 3
config = F3
end

begin
prog = mythtv
button = JUMP
repeat = 3
config = Z
end

begin
prog = mythtv
button = REPLAY
repeat = 3
config = Left
end

begin
prog = mythtv
button = SELECT
repeat = 3
config = Space
end


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

It's from my tivo remote but is similar to what yours should look like.
The file should be called **lircrc **and live in your user's **~.mythtv/** folder. I'm not sure if it's necessary, but I've also got a link in my home folder from **.lircrc** to that file. Anyway, the format is 

**prog **= the program that you will use it with
**button **= the button as defined in your lircd.conf file
**repeat **= the number of signals to accept as one
**config **= the keypress that mythtv (or vlc, etc) is looking for

For example, if you wanted to define the #1 button for vlc then you would have:
```
begin
prog = vlc
button = 1
repeat = 3
config = 1
end 
```

which would map the #1 key that lirc receives from your remote and feed it into vlc as the #1 key. I could map it to whatever I wanted by changing up the **config **line; H, J, ESC, etc.

It gets a little more complicated if you have multiple remotes defined (each block would need to specify which remote to reference by adding a remote line to each key-block):
```
begin
remote = tivo
prog = vlc
button = 1
repeat = 3
config = 1
end 
```

where 
**remote **= the name of the remote as defined in lircd.conf

There's a few more options that you can add to each block; check out the lirc website for more info on all those options.

---

### Post by nicoloks on 2009-02-10
Thanks for the detailed reply OffAxis. Sounds like I wasn't too far off the mark, however I still must be missing something. The remote just doesn't function when using the MythTV frontend. Perhaps it something to do with the repeats?

This is what my lircrc file looks like in the .mythtv folder in my home directory;
```

# Record
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_RECORD
  repeat = 2
  config = R
end

# Skip Backwards
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_REWIND
  repeat = 2
  config = PgUp
end

# Pause
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_PAUSE
  repeat = 2
  config = P
end

# Skip Forward
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_FASTFORWARD
  repeat = 2
  config = PgDown
end

# Previous Commercial Cut
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_PREVIOUS
  repeat = 2
  config = Q
end

# Stop
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_STOP
  repeat = 2
  config = T
end

# Next Commercial Cut Forward
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_NEXT
  repeat = 2
  config = Z
end

# Cancel / Back
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_ESC
  repeat = 2
  config = Esc
end

# Show OSD
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = Go
  repeat = 2
  config = I
end

# Mute
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_MUTE
  repeat = 2
  config = F9
end

# Volume Up
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_VOLUMEUP
  repeat = 2
  config = F11
end

# Volume Down
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_VOLUMEDOWN
  repeat = 2
  config = F10
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_1
  repeat = 2
  config = 1
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_2
  repeat = 2
  config = 2
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_3
  repeat = 2
  config = 3
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_4
  repeat = 2
  config = 4
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_5
  repeat = 2
  config = 5
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_6
  repeat = 2
  config = 6
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_7
  repeat = 2
  config = 7
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_8
  repeat = 2
  config = 8
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_9
  repeat = 2
  config = 9
end

# Number Zero
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_0
  repeat = 2
  config = 0
end

# Change Aspect Ratio
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = Zoom
  repeat = 2
  config = W
end

# Swap PIP Windows
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_MENU
  repeat = 2
  config = N
end

# Delete
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_BACKSPACE
  repeat = 2
  config = D
end

# Select
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_SELECT
  repeat = 2
  config = Return
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_SELECT
  repeat = 2
  config = Space
end

# PiP On-Off Toggle
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = RightMenu
  repeat = 2
  config = V
end

# Menu
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = BTN_LEFT
  repeat = 2
  config = M
end

# Change PiP Focus
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = BTN_LEFT
  repeat = 2
  config = B
end

# OSD browse
begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_ENTER
  repeat = 2
  config = O
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_UP
  repeat = 2
  config = Up
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_DOWN
  repeat = 2
  config = Down
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_LEFT
  repeat = 2
  config = Left
end


begin
  prog = mythtv
  remote = Antec_Veris_RM200
  button = KEY_RIGHT
  repeat = 2
  config = Right
end

```

This file is actually just a sym link to ~.lirc/mythtv, as it the ~.lircrc file. This wouldn't cause any issues would it?

---

### Post by mathog on 2009-02-10
> 

This file is actually just a sym link to ~.lirc/mythtv, as it the ~.lircrc file. This wouldn't cause any issues would it?

Only if there were protection issues, use "ls -al" to check.

Check /var/log/mythtv/* for messages as you press the buttons on your remote.  The lircrc is very picky about the names (case sensitive, for one).

The key presses do show up in irw, right?

---

### Post by nicoloks on 2009-02-10
.lircrc and .lirc/mythtv both have -rw-r--r-- permissions and are owned by my user. Had a look at the mythtv logs, and I can't see anything regarding IR input (or keyboard input).

Everything checks out in irw. Every single button on my remote results in a code being displayed. I've double checked that the remote name is the same as specified in lircd.conf.

I might move on and see if I have any issues with creating a lircrc file for Mplayer. If that works then I know it is MythTV, if not, it is something bigger.

Any other pointers you can give me on things to check would be appreciated. Doesn't matter how simple you think it might be there is a fair chance I may have missed it as I'm only new to linux, and this is my very first time using lirc and remotes with linux.

---

### Post by nicoloks on 2009-02-12
Figured it out. I was using [http://lircconfig.commandir.com](http://lircconfig.commandir.com) to generate my conf files. Files were fine, it was just using DOS format instead of Unix. Used the dos2unix util and all is working, though it will need a little fine tuning.

---

