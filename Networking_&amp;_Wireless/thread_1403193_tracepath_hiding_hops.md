---
title: "tracepath hiding hops"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by borgward on 2010-02-10
Why does tracepath hide hops? I ran tracert on a winblows machine and it displays all the hops.

Why does not ubuntu offer traceroute like just about everybody else?

Something wrong w/traceroute?

---

### Post by athevil on 2010-02-10
it is expected to do the same...

and it DOES on my machine!
can u explain something more, and put output herem or wat exactly it showing, how many hop it is omitting?

---

### Post by bestbeforetoday on 2010-02-13
Tracepath sends UDP packets whereas tracert on Windows sends ICMP packets.  To get similar results to Windows tracert in Ubuntu you should be able to do one of the following:


[LIST=1]
[*]Install the the 'traceroute' package and either use 'tracert' or 'traceroute -I' (as root).
[*]Use the 'mtr' command.
[/LIST]

Hope that helps.

---

