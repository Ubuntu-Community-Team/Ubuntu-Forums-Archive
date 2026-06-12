---
title: "LIRC - Using META in lircrc for button sequences doesn't work for two programs"
date: 2010-08-09
forum: Mythbuntu
---

### Post by edwardof on 2010-08-09
I've got an Apple TV set up as a frontend, and I'm trying to get LIRC working happily. Thanks to the Apple IR receiver ignoring IR codes that don't contain its prefix, I'm trying to use the Apple remote. It only has 6 buttons, but when used with the last comment on [this](http://code.google.com/p/atv-bootloader/wiki/AppleIR_LIRC) page, you can get 11 functions from the 6 buttons. That's sufficient for me, as anything beyond basic nav and playback I handle on my main frontend. The problem is that I use VLC as my default video player since it handles DVDs as ISOs much better than the internal player. The lircrc that I'm trying to use is here:
```

#
# MythTV key bindings for Apple TV Remote
#
# Note that for the 2-button sequences, the keys have to be pressed in
# sequence, not together.
#

#
# Button(s)       Config
# ---------       ------
# up              Up
# down            Down
# left            Left
# right           Right
# play            P
# menu+up         I
# menu+down       Escape
# menu+left       Q
# menu+right      Z
# menu+play       D 
# menu+menu       M
#

#
# menu+button sequences
#
begin META

  begin
    prog = mythtv
    button = MENU
    config = m
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = mythtv
    button = VOLUP
    config = I
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = mythtv
    button = VOLDOWN
    config = Escape
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = mythtv
    button = PLAY
    config = D
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = mythtv
    button = BACKWARD
    config = Q
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = mythtv
    button = FORWARD
    config = Z
    flags = mode|quit
    repeat = 2
    delay = 0
  end

end META

#
# single-button sequences
#
begin
  prog = mythtv
  button = MENU
  mode = META
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = mythtv
  button = VOLUP
  mode = NORMAL
  config = Up
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = mythtv
  button = PLAY
  config = P
  flags = quit
  repeat = 2
  delay = 0
end

begin 
  prog = mythtv
  button = FORWARD
  config = Right
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = mythtv
  button = BACKWARD
  config = Left
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = mythtv
  button = VOLDOWN
  config = Down
  flags = quit
  repeat = 2
  delay = 0
end


##############################################################################
# VLC key bindings for Apple TV Remote
#
# Note that for the 2-button sequences, the keys have to be pressed in
# sequence, not together.
#

#
# Button(s)       Config
# ---------       ------
# up              Nav Up
# down            Nav Down
# left            Nav Left
# right           Nav Right
# play            Play/Pause
# menu+up         Audio Track
# menu+down       Quit
# menu+left       Chapter Prev
# menu+right      Chapter Next
# menu+play       Nav Activate
# menu+menu       Disk Menu
#

begin META

#### VLC Configuration ####
  begin
    prog = vlc
    button = MENU
    config = key-disc-menu
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = vlc
    button = VOLUP
    config = key-audio-track
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = vlc
    button = VOLDOWN
    config = key-quit
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = vlc
    button = PLAY
    config = key-nav-activate
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = vlc
    button = BACKWARD
    config = key-chapter-prev
    flags = mode|quit
    repeat = 2
    delay = 0
  end

  begin
    prog = vlc
    button = FORWARD
    config = key-chapter-next
    flags = mode|quit
    repeat = 2
    delay = 0
  end
end META

#
# single-button sequences
#
begin
  prog = vlc
  button = MENU
  mode = META
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = vlc
  button = VOLUP
  mode = NORMAL
  config = key-nav-up
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = vlc
  button = PLAY
  config = key-play-pause
  flags = quit
  repeat = 2
  delay = 0
end

begin 
  prog = vlc
  button = FORWARD
  config = key-nav-right
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = vlc
  button = BACKWARD
  config = key-nav-left
  flags = quit
  repeat = 2
  delay = 0
end

begin
  prog = vlc
  button = VOLDOWN
  config = key-nav-down
  flags = quit
  repeat = 2
  delay = 0
end


```

Unfortunately only MythTV responds to this file. If I put the VLC section first, only VLC responds. I've tried putting the VLC and MythTV meta sections inside the same "begin META" / "end META" section and then only the one that's first in the section is used. Is there any way for me to use the meta functionality in two programs?

---

