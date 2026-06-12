---
title: "Tightvncserver scrambled garbeled keyboard"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by Mercedes300 on 2012-01-31
THIS IS SOLVED

ADD:
export XKL_XMODMAP_DISABLE=1
to your .vnc/xstartup file

Found the solution reading the tightvncserver perl script. :-x

PS. Can a moderator please mark this solved? Thanks.


-----Original post-------

Hi all.

I'm having a problem running tightvncserver. The keyboard gets scrambled in transmission (I guess). When I type the home row keys from left to right, it outputs: 
     asdfghjkl;'
     abfhjk;'`io

This behaviour is in both gnome-session and openbox-session.

The keyboard works fine when running the server via vnc4server.

I need to run on tightvncserver because I need a "view-only" password.

If there is a way to run vnc4server with a view-only password, that would fix my problem too.

Any and all hints and tips and help is appreciated.

Thanks

-John

Ubuntu 10.04 LTS x86_64 Desktop

---

