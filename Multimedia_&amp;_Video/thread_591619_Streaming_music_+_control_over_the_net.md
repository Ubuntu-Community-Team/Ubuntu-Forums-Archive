---
title: "Streaming music + control over the net"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by ridetheteapot on 2007-10-25
Does anyone have any suggestions on the best stream/control setup for listening to my music collections over the net?

host:ubunutu client:windows

what i am going to do if i can't figure out a slimmer way of going about it is: use mpd with icecast and ssh to control mpd via ncmpc (or gmpc, xming is so cool).

but i am wondering about 2 things... 1 is there a way to mount an ssh filesystem (like sshfs but on a windows machine) so that i dont have to actually copy files to play them?

and also i read on the kde mailing list that you can do something like ssh user@host  cat music.mp3 | mpg123 -
and this will somehow stream the mp3 to the local machine.
when i try this i get only the normal functionality of the mp3 playing on the host machine. the post on kde lists said that cat would basicly act as a server.

i think these last two options might use too much bandwidth to be practical, but im still curious

ps anyone interested in doing this there is also a program called gnump3 that uses a http interface to control the music.
im an mpd addict so im not going this route

---

### Post by mikwig on 2007-12-26
Yes - I found this and am gonna try it

[http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html](http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html)

---

