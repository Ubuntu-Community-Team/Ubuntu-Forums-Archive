---
title: "Video problem with tvants"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by User-007 on 2007-09-08
Hi all, 

I managed to install and run tvants with wine. Everything seems to be OK, but when opening a channel, the program reports about an error "Failed to open channel [http://localhost:16900/1.asf](http://localhost:16900/1.asf). Do you agree to open it by windows' default player?" 

Any experiences?

Thanks
User JB

---

### Post by trippinnik on 2007-09-29
I just tried this out today.  I had the same problem as you, but because of my experience using Sopcast i decided to try and have mplayer open it.  
in the terminal type:
mplayer [http://localhost:16900/1.asf](http://localhost:16900/1.asf)
or whatever it says in the error message.  You'll only need the tvant program to connect to the streams.

---

### Post by chinasteve2000 on 2007-12-17
Hey Trippin,
Thanks for your note. That helps me, though I don't know if JB used it or not. Thanks either way!

I have a follow-up question, though. After getting TVants working, then using your suggestion plus installing MPlayer, this works fine. I noticed that sometimes I have to change the number, for example, exchanging:
mplayer [http://localhost:16900/1.asf](http://localhost:16900/1.asf)
with
mplayer [http://localhost:16900/5.asf](http://localhost:16900/5.asf)
if it is the 5th feed instead of the first.

Does anyone know if there is a way to make TVants automatically do this magic via a click instead of going to Terminal that you know of?

Thanks!
Steve

---

