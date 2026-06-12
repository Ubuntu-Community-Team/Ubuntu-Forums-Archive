---
title: "Interhack and &quot;Can't access() script&quot; error"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by arvigeus on 2010-02-12
Hello! :)
I'm trying to run [Interhack]("http://interhack.us/") (spoiled variant of Nethack) for local game. Is looking through settings I saw that:
```
our %servers = (
    ih_server => { server => 'localhost',
                   port   => 9999,
                   name   => 'ih_server',
                   type   => 'ih-server',
                 },
```
When I try to start it with ih_server option it gives me that error:
```
Can't access() script
Could not create socket: Connection refused
```
I think my problem is closed port:
```
nc localhost 9999
localhost [127.0.0.1] 9999 (?) : Connection refused
```

How do I fix this?

---

### Post by leprasmurf on 2011-07-27
The way interhack works, for local games, is rather confusing.  The method can be found here: [http://interhack.us/FAQ.html#devnull](http://interhack.us/FAQ.html#devnull) .  Basically, you add the line:

server 'ih_server';

to your config (~/.interhack/config).  you then run nethack with the "nethack" command.  Note:  the text did not appear on screen for me, though the command worked fine.  I think what this does is puts interhack into server and client mode, and encapsulates the nethack session in a pseudo terminal...though I haven't dug around the source code, so that's just speculation.

---

### Post by arvigeus on 2011-07-27
Hehe, answers never come late :)
Because it was really long ago for my, can't remember much details, but I think I tried that too. Anyway, I'll try again. Thanks for the effort!

---

