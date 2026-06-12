---
title: "x11vnc  single application?"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by walmartshopper67 on 2010-04-06
I use x11vnc to run a remote X11 session on my desktop. Would it be possible to connect to only **one** application instead of the whole desktop? I know how to run remote apps over ssh with x11 forwarding, but that just starts another instance of the application. I would like to be able to connect to the **running** session of an application. For example, i'm on my laptop and want to run pidgin, so i would write a little script to connect to my desktop with X11vnc and view the currently running pidgin session - that way i can see any messages people left me while i was gone, or doing the same thing with Firefox would make it easier to have just one set of favorites/history/etc. instead of having to synchronize them. Is this possible with X11vnc, or is there some other method or application? Thanks.

---

### Post by krunge on 2010-04-06
> For example, i'm on my laptop and want to run pidgin, so i would write a little script to connect to my desktop with X11vnc and view the currently running pidgin session - that way i can see any messages people left me while i was gone, or doing the same thing with 
It is possible to do this in a (very) limited fashion with the x11vnc '-id' or '-sid' option:
[INDENT][http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-id](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-id)[/INDENT]
It is really only usable if the application only has one or two windows that you want to view and interact with. With a complicated (many windowed) application like firefox it is doubtful that it would be usable.

There is also an experimental option -appshare that tries to handle the many windowed app case, but it too is rough.

---

### Post by walmartshopper67 on 2010-04-07
Sweet - exactly what i was looking for. I can see how it could dragged down with many windows though, my main goal is Pidgin - i'm an AIM geek with way too many AIM friends. I'll give it a shot, thanks!

---

