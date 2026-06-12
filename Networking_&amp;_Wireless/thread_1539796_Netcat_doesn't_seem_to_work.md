---
title: "Netcat doesn't seem to work"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by oomar on 2010-07-27
ok I've tried to use netcat in the past and assumed it was my stupidity that was preventing it from working... but this is getting ridiculous. I'll execute

nc -l 3333 on a server at 192.168.0.105 (after opening it on the firewall of course)

then I run nc 192.168.0.105 3333 on my laptop (from 192.168.0.101).

and nothing happens... i start typing and nothing comes up on the terminal.

I run nc -z 192.168.0.105 80 which should ideally do a port scan of port 80 on that server (of which I'm running a web server that clearly works) but it doesnt even give me any feedback. Nothing happens. 


Now when I use the verbose flag i see that I am indeed connecting to the specified port on the server successfully (so the port scan one is a success but only with the verbose flag... which shouldnt be the case I believe). 

But still once I have the server listening and the laptop connected... I type in both windows and nothing happens...


perhaps I just don't know what I'm doing with nc. idk help?

---

### Post by jdac on 2010-07-29
Hi!

Apparently Ubuntu (I have 9.10) comes with a default package for netcat, called "netcat-traditional". This netcat was behaving strangely (according to what could be expected from the manpage). Looking in Synaptic I saw another netcat package "netcat-openbsd". Installing that one gave me a working netcat.


I found the problem when I was trying to implement the minimalistic "server" explained on the manpage:

On one console
netcat -l -v 5000

And on another
netcat 127.0.0.1 5000

With the netcat-traditional the "server" would just tell me that it started listening on some random port and not 5000. And even if i tried to use that random port (say 38218 ) from the "client", the connection was inmediately closed.

With the netcat-openbsd, listening started OK, and when trying to connect from the "client" console, the connection was established and what I typed in the second console showed up in the first one.

PS:
I just installed netcat-openbsd, without first uninstalling the traditional. The installer moved the old nc to /bin/nc.traditional and created a new one, /bin/nc.openbsd. The new /bin/nc became just a symlink for /bin/nc.openbsd.

---

