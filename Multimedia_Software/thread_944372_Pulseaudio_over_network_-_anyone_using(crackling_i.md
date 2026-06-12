---
title: "Pulseaudio over network - anyone using?(crackling issue)"
date: 2008-10-11
forum: Multimedia Software
---

### Post by tensop on 2008-10-11
Hi guys, experimenting with using pulseaudio over the network and have come across the issue of crackly sound in movies. Audio from sources such as amarok,audacious etc are ok, but any attempt at movies results in fast crackling(or what i assume more accurately - is tiny millisecond long gaps in the audio stream)

---

### Post by tereshkosg on 2008-12-26
I have exactly the same problem ... when playing something using mplayer or amarok everything works fine. If try playing something using Totem or Vlc sound comes out interrupted.

Were you able to figure out what causes that?

---

### Post by Topfs on 2008-12-26
I think more information is needed if anyone is gonna solve it. Do you play audio on both mplayer and vlc or video on both or audio on one and video on one? is it localised to applications or is it happening only when trying video?

I´ve looked over the source code on both mplayer and vlc and they interact a bit differently on pulseaudio, VLC do the callback route so pulseaudio says when it needs data and vlc provide. mplayer just pump in as much as it is allowed to do.

The difference here Im guessing is that over network perhaps pulseaudio have a to little buffer and says fill me up to late and the lag is making the data come to late, atleast some of it.

---

### Post by tereshkosg on 2008-12-26
only audio and only one instance of a player.

If I start two mplayer instances I hear audio from one of them for about a second and then audio from the second instance and so on. Any two (or more) instances of players (any) give same result - each of them is given its turn. 

to add ... lets say i have one instance of mplayer playing. Sound is OKAY but then Skype wants to make a noise -  what happens? music is interrupted and skype "squeaks" whatever it needs - then everything comes back to normal.

Probably, it is a matter of a limited bandwidth. Are application's sounds mixed locally or on a sound server? if on the server then it sort of makes sense that the bandwidth is exhausted very fast.

one more thing, when I look at the pulseaudio's Manager, Clients tab, and start only one instance of Totem - I see THREE connections (TWO Totem Movie Player + EsounD client) from Totem and enjoy an interrupted sound. When I start VLC i see only one connection called ALSA plugin (vlc) and as well an interrupted sound. Rythmbox as well created TWO connections to the sound server both called Rythmbox. Mplayer creates one connection called MPlayer and, as described before, good sound.

after having said that ...
it seems like there is some sort of scheduling , some allocation of bandwidth between sound server connections.... and it does not really work right.

---

