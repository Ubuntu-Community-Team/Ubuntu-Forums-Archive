---
title: "LIRC Modes"
date: 2008-07-03
forum: Mythbuntu
---

### Post by Ohs0Ahxi on 2008-07-03
I wanted to replace the built in music player with Amarok I followed a guide I found here [_Integrating MythTV and Amarok_](http://acidzebra.blogspot.com/2007/07/integrating-mythtv-and-amarok_17.html) 

Its working partly, when I click my menu entry Amarok opens and the keys I've defined on the remote do what they should. But the remote is also controlling mythfrontend in the background.

The only other discussion of this problem I could find was [_Switching between Mythtv and Amarok_](http://www.gossamer-threads.com/lists/mythtv/users/337550) That seemed to be that lirc modes was the solution, this is my first play with lirc but with multiple files in ~.lirc/ I think I'm using modes correctly as it is.

These are files I've changed, if anyone can spot something wrong. Other applications mythfrontend starts work fine with only them receiving instructions from the remote e.g mplayer I couldn't find it in the menu's so I'm not sure if EXEC amarok is right or not. 

[quote=/usr/share/mythtv/library.xml]
      <button>
      <type>MUSIC</type>
      <text>Listen to Music</text>
      <action>EXEC amarok</action>
   </button>
[/quote]

[quote=~.lircrc]
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
include ~/.lirc/amarokapp
[/quote]

[quote=~.lirc/amarokapp]
#       BackExit
##      Exit/go back/cancel
begin
prog = irexec
button = BackExit
config = dcop amarok MainApplication-Interface quit
end

#       VolumeUp
##      Volume Up
begin
prog = irexec
button = VolumeUp
repeat = 1
config = dcop amarok player volumeUp
end

#       VolumeDown
##      Volume down
begin
prog = irexec
button = VolumeDown
repeat = 1
config = dcop amarok player volumeDown
end

#       Rewind
begin
prog = irexec
button = Rewind
config = dcop amarok player seekRelative -10
end

#       SkipBack
begin
prog = irexec
button = SkipBack
config = dcop amarok player prev
end

#       Play
begin
prog = irexec
button = Play
config = dcop amarok player play
end

#       Pause
begin
prog = irexec
button = Pause
config = dcop amarok player playPause
end

#       Stop
begin
prog = irexec
button = Stop
config = dcop amarok player stop
end

#       Fwdwind
begin
prog = irexec
button = Fwdwind
config = dcop amarok player seekRelative 10
end

#       SkipFwd
begin
prog = irexec
button = SkipFwd
config = dcop amarok player next
end
[/quote]

---

