---
title: "Is command line DVB-T channel selection possible with VLC ?"
date: 2018-12-30
forum: Multimedia Software
---

### Post by JohnCraick on 2018-12-30
Short version - see subject above

Long version ...
I'm currently running VLC 3.04 on Ubuntu 18.04 plus various other linux  & MS Windows versions, all running off a Winfast "Gold" USB tuner  stick. It works fine & I have a useful working DVB-T system. BUT I'd  really like to select and play a specific TV channel from the command  line. Can this be done ?

I'm based in Melbourne, Australia and to play ABC TV (our national broadcaster, commonly known as Channel 2) I can do
> vlc dvb-t:// frequency=226500000:bandwidth=7
and vlc displays the ABC "News" channel. Now "frequency" above correctly  sets the ABC transponder frequency but based on that there are several  other ABC TV "channels", or programs. Each of these has its own program  number in the range 560 - 565. Some info on the net suggests I should  able to specify a particular program on the command line, for example

> vlc dvb-t:// frequency=226500000:bandwidth=7: program=563

Bad luck ! - as before I just get the first channel in the transponder set. So ...

1. Is that supposed to work ?
2. Have I made some silly syntax error in there ?
3. Is there some other command line method of doing this ?

I can get to the channel I want through the VLC GUI - (Right click in TV  screen -> Playback -> Program -> choose from list) but that's  not what I want to do.
On the net I've found some convoluted methods involving playlists but at  the moment I can't make them work and in any case they don't really do  what I want either.
One good article on all that is at [https://davidzou.com/articles/streaming](https://davidzou.com/articles/streaming) ... t-with-vlc

So, as I said, does anyone have a command line recipe for this task ?

- JohnC,
                                                                                                                                     [Top]("https://forum.videolan.org/viewtopic.php?f=13&t=147622#wrap")

---

### Post by vidtek on 2018-12-30
> **JohnCraick said:**
> Short version - see subject above

Long version ...
I'm currently running VLC 3.04 on Ubuntu 18.04 plus various other linux  & MS Windows versions, all running off a Winfast "Gold" USB tuner  stick. It works fine & I have a useful working DVB-T system. BUT I'd  really like to select and play a specific TV channel from the command  line. Can this be done ?

I'm based in Melbourne, Australia and to play ABC TV (our national broadcaster, commonly known as Channel 2) I can do
> vlc dvb-t:// frequency=226500000:bandwidth=7
and vlc displays the ABC "News" channel. Now "frequency" above correctly  sets the ABC transponder frequency but based on that there are several  other ABC TV "channels", or programs. Each of these has its own program  number in the range 560 - 565. Some info on the net suggests I should  able to specify a particular program on the command line, for example

> vlc dvb-t:// frequency=226500000:bandwidth=7: program=563

Bad luck ! - as before I just get the first channel in the transponder set. So ...

1. Is that supposed to work ?
2. Have I made some silly syntax error in there ?
3. Is there some other command line method of doing this ?

I can get to the channel I want through the VLC GUI - (Right click in TV  screen -> Playback -> Program -> choose from list) but that's  not what I want to do.
On the net I've found some convoluted methods involving playlists but at  the moment I can't make them work and in any case they don't really do  what I want either.
One good article on all that is at [https://davidzou.com/articles/streaming](https://davidzou.com/articles/streaming) ... t-with-vlc

So, as I said, does anyone have a command line recipe for this task ?

- JohnC,
                                                                                                                                     [Top]("https://forum.videolan.org/viewtopic.php?f=13&t=147622#wrap")

John-
VLC can do some pretty incredible stuff, I used to use it when I lived in Perth, doing just what you said from the local Wanneroo transmitter, so I know it is possible.  After moving back to the UK, I now use Mythtv more and have let VLC slip.  VLC is so much faster at channel changing, especially on the command-line Mythtv is painfully slow to change channels comparitively.  Bad news, I had a script I used to run VLC on the command-line but I lost it in the move, and my old brain can't remember the correct syntax, sorry.:(

Tony.

---

### Post by JohnCraick on 2018-12-30
SOLVED
Yes, silly syntax error as per 2 above. Correct syntax is

> vlc dvb-t://frequency=226500000:bandwidth=7 :program=563

i.e  :program= must be preceded by a space. OTOH, :bandwidth=7 must NOT 

and NO space in -t://frequency=

(How is a mere amateur supposed to know that ! ? )

Thanks to Rémi Denis-Courmont on the Videolan forums for this info.

---

