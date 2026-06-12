---
title: "Internet works locally, can't connect to http or via ssh"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by rainbowFish on 2009-11-13
Hello all,

I'm having a strange problem with a new upgrade to 9.10.
When I first boot up, wicd connects to my wireless network successfully, and everything works great. I can ssh into the server, I can connect to the apache server, etc. But then, usually after an hour or so, the internet still works locally on the server, but I can't connect to it over http or ssh.
Ssh returns: Read from remote host 192.168.1.101: No route to host
Connection to 192.168.1.101 closed.

But then, strangely, it will sometimes come back on and I will be able to connect after an indiscriminate amount of time.

I'm relatively new to using Linux, so if you guys could give me some log files and other things to look at and post for you to look at, that would be great.

Thanks!

---

### Post by rainbowFish on 2009-11-15
Nobody else experiencing this? It's driving me crazy!

---

### Post by driftertx on 2009-11-15
how are you connecting to the server in question? from a windows box? Sounds like your wifi might be dropping out, try switching wifi channels..

---

### Post by crankyadm1n on 2009-11-15
I agree... I the machine your connecting (trying to) have a static or a dynamic ip address. No Route to Host means exactly as it sounds there is no route to the host. Now the fact you can still see the Internet from it leads me to believe the ip address has changed. Prob from your wireless droping and reconnecting again.

---

### Post by rainbowFish on 2009-11-17
That would be my guess as well, but like I said, the internet still works on my linux box, as well as on the computer I'm trying to remotely connect to. Usually, I'll get the "No Route to Host" error once, and if I try to ssh into it again, "Host is down."

---

