---
title: "Need to set VNC to use 3.x"
date: 2006-03-11
forum: Networking &amp; Wireless
---

### Post by kseise on 2006-03-11
I am trying to connect to a VNC4Server setup on my Ubuntu using PocketVNC on a Dell Axim PocketPC.  The PocketVNC client only supports VNC protocol up to 3.x.  Does anyone know how to set VNC4Server to support older protocols?

---

### Post by pauljwells on 2006-05-25
Not exactly an answer to your question, but I just managed to get a vnc client on my iPaq to see my ubuntu (dapper) desktop.

I got the freeware vnc client from 

[http://www.mochasoft.dk/vncce.htm](http://www.mochasoft.dk/vncce.htm)

It's the only one I could find that would work

I had to do one tiny hack on the ubuntu box (because of my router setup, you might be ok without this) 

[http://www.ubuntuforums.org/showthread.php?t=181605](http://www.ubuntuforums.org/showthread.php?t=181605)

I activated vnc in the System/Preferences menu  and noted the name to connect to, and then I could connect from the pocket pc to the name, without the :0 at the end.

Hope this is useful to someone

---

