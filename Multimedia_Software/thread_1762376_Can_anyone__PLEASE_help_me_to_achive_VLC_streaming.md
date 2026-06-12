---
title: "Can anyone  PLEASE help me to achive VLC streaming?"
date: 2011-05-19
forum: Multimedia Software
---

### Post by macey on 2011-05-19
According to this:- [http://paul-sanders.info/?p=50]("http://paul-sanders.info/?p=50")
{ps, just checked this website, it looks like he forgot to pay the bill!}
The following should work:-

vlc -vvv ~/Music/my_test_file.mp3 --sout '#transcode{acodec=mp3,ab=64,channels=2}:std{access=mmsh,mux=asfh,dst=8080}'

But it doesn't work.  Looking at the VLC 'Media Information > Statistics' I can see the 'Audio Decoded' and 'Input read' counts increasing but the
'Output written' counts stubbornly remain at zero.
All ports on PC firewall and router have been set up correctly.

I would dearly LOVE to get vlc streaming working. I have looked through the documentation and found it little help for me. The videolan forum is most unhelpful. The typical reply is of the "read the documentation dumbo" nature.
Here's hoping the Ubuntu forum will be more friendly & helpful.
Obviously, I can post  the vlc log if requested.

I have noticed this:-

0x92911dc] signals interface error: signal 17 overriden (0x19774c0)
[0x92911dc] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
In the log.
Running Ubuntu 11.04

Thanks in anticipation
Richard.  ps, just noticed the spelling mistake in the heading, obviously, should read 'achieve'.

---

### Post by nothingspecial on 2011-05-19
Try specifying your ip address aswell as port. ie

```
dst=<ipaddress>:8080
```

---

### Post by macey on 2011-05-19
> **nothingspecial said:**
> Try specifying your ip address aswell as port. ie

```
dst=<ipaddress>:8080
```

According to that website, you can omit ipaddress. What if Iwant it available at any address? The writer of the article says he has used this method to broadcast to 200+ users at the same time. Did not code ip addresses. By the way, before you ask, I have tried to contact author (paul Sanders).
Thanks anyway!

---

