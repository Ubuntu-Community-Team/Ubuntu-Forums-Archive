---
title: "ffmpeg Streaming UDP Problem"
date: 2017-03-10
forum: Multimedia Software
---

### Post by gianca91 on 2017-03-10
Hello everybody, I' m new in the ffmpeg world.
I have to do a streaming udp of my internal webcam.
in Windows bt Zeranoe, i used this instructions:

ffmpeg -re -f dshow -i video="Chicony USB 2.0 Camera" -an -preset ultrafast -tune zerolatency -f mpeg [udp://127.0.0.1:8080](udp://127.0.0.1:8080)
ffplay -fflags nobuffer -flags low_delay -framedrop -strict experimental [udp://127.0.0.1:8080](udp://127.0.0.1:8080)

and everyting work. But the problem is that i have to work with ubuntu, so i tried to used the same instruction (of course edited):

ffmpeg -re -f dshow -i /dev/video0 -an -preset ultrafast -tune zerolatency -f mpeg [udp://127.0.0.1:8080](udp://127.0.0.1:8080)
ffplay -fflags nobuffer -flags low_delay -framedrop -strict experimental [udp://127.0.0.1:8080](udp://127.0.0.1:8080)

but the ffplay give me this error:
[NULL @ 0x7f9a200008c0] [Eval @ 0x7f9a26730970] Undefined constant or missing '(' in 'nobuffer'
[NULL @ 0x7f9a200008c0] Unable to parse option value "nobuffer"
[NULL @ 0x7f9a200008c0] Error setting option fflags to value nobuffer.
[udp://127.0.0.1:8080](udp://127.0.0.1:8080): Invalid argument

and the ffmpeg this one:

Unrecognized option 'tune'.
Error splitting the argument list: Option not found OR 
Unknown input format: 'dshow'

and if i try to delete from the instruction tune and dshow, it work, but with a delay of 20 or more sec =(

How I can fix it? What i can use instead or tune or dshow to have a streaming in real tim

---

### Post by TheFu on 2017-03-10
Don't know much about streaming or cameras.

Probably can't help, but ffmpeg versions change options all the time. There are lots and lots of examples with many different versions all over the internet.  Review the **--help** and manpage for the exact version of ffmpeg installed on the system for any options issues.

May want to prefer mpeg-ts video. That's what TV channels use to broadcast.

That's all I got. Sorry it isn't more.

---

