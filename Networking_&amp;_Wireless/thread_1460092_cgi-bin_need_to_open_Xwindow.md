---
title: "cgi-bin need to open Xwindow"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by udina on 2010-04-22
Hi,
I used to have a cgi-bin that, when launched by the apache2 server, runs a progrma that need to open some Xwindows to make a graph and then return the graph (as a link to a file).

So, I need to use the X from my prgorma. I used to do it via export DISPLAY=host:0.0 and giving permissions via xhost.

Now, it doesn't work under ubuntu 9 (I was using it on diferent linux distros)

Using ssh is not a solution form me, because it all is run from the apache server.

How could I do it?

Thanks

---

