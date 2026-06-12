---
title: "Lirc sees remote presses, apps don't"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by Braedley on 2007-07-29
I know that my hardware.conf and lircd.conf files are correct, because I see button presses when I use irw.  However, I've created a lircrc file for XMMS and MPlayer, yet neither respond to button presses.  My lircrc file for examination:
```


begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = MAXI

  repeat = 2

  config = vo_fullscreen

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = CLOSE

  repeat = 2

  config = quit

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = VOL+

  repeat = 2

  config = volume +1

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = VOL-

  repeat = 2

  config = volume -1

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = MUTE

  repeat = 2

  config = mute

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = FIREFLY

  repeat = 2

  config = volume 1

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = CH+

  repeat = 2

  config = audio_delay +0.1

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = CH-

  repeat = 2

  config = audio_delay -0.1

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = OK

  repeat = 2

  config = osd

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = REW

  repeat = 2

  config = seek -10

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = FWD

  repeat = 2

  config = seek +10

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = PREV

  repeat = 2

  config = seek -60

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = PAUSE

  repeat = 2

  config = pause

end





begin

  prog = mplayer

  remote = Snapstream_Firefly

  button = NEXT

  repeat = 2

  config = seek +60

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = CLOSE

  repeat = 2

  config = QUIT

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 1

  repeat = 2

  config = ONE

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 2

  repeat = 2

  config = TWO

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 3

  repeat = 2

  config = THREE

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 4

  repeat = 2

  config = FOUR

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 5

  repeat = 2

  config = FIVE

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 6

  repeat = 2

  config = SIX

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 7

  repeat = 2

  config = SEVEN

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 8

  repeat = 2

  config = EIGHT

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 9

  repeat = 2

  config = NINE

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = 0 

  repeat = 2

  config = ZERO

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = VOL+

  repeat = 2

  config = VOL_UP

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = VOL-

  repeat = 2

  config = VOL_DOWN

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = MUTE

  repeat = 2

  config = MUTE

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = FIREFLY

  repeat = 2

  config = PLAYPAUSE

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = PLAY

  repeat = 2

  config = PLAY

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = STOP

  repeat = 2

  config = STOP

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = REW

  repeat = 2

  config = BWD

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = FWD

  repeat = 2

  config = FWD

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = PREV

  repeat = 2

  config = PREV

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = PAUSE

  repeat = 2

  config = PAUSE

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = NEXT

  repeat = 2

  config = NEXT

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = A

  repeat = 2

  config = REPEAT

end





begin

  prog = xmms

  remote = Snapstream_Firefly

  button = B

  repeat = 2

  config = SHUFFLE

end

```

Thanks in advance.

---

