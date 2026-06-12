---
title: "use ssh for internet"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by yanuanti on 2009-10-29
Hello All,

I am a student in a university. The problem is I have a very limited quota of internet data if I use it from my room.

But I can connect using ssh to my lab server. (the data transfer between my room and lab using ssh are not calculated in my quota).

What I want to do now is, to configure my computer to first connect to my lab using ssh + some options. Next configure firefox to get all the internet data through this connection so that my quota is not used.  Is this possible ? 

I tried to read how to do this on internet but couldn't really do it. Can someone please tell me how to go about this ? 

thanks,
Shailesh

---

### Post by Kokopelli on 2009-10-29
I do not recommend doing this and if you get in trouble with your university don't blame anyone but yourself.

That said  "ssh -D 8080".  Try "man ssh"  for more information or google for "ssh socks proxy"

---

