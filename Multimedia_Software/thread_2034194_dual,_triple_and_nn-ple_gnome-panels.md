---
title: "dual, triple and nn-ple gnome-panels"
date: 2012-07-28
forum: Multimedia Software
---

### Post by krnr on 2012-07-28
[[img]http://storage5.static.itmages.ru/i/12/0726/s_1343323585_5313315_9983f8e0d1.png[/img]](http://storage5.static.itmages.ru/i/12/0726/h_1343323585_5313315_9983f8e0d1.png)

I used Ubuntu 12.04 with Nvidia drivers and Desktop+TV combo. When I ran it in "TwinView" mode it all worked perfect, but than once I tried to run on "Separate screens" mode and noticed that Xs don't run on TV - just blank white screen. In proces of restarting more and more Gnome panels appeared on desktop monitor and I don't know the way to remove it to the state it used to be. I would kill user account, BUT there are already two gnome-panels "one-in-one" on default user, so the problem still remains. What is it? How to solve?

---

### Post by WiNeOS on 2012-08-01
I had a similar problem and resolved it deleting ~/.config/dconf/user file.

Make a copy of that file, delete it and restart your user session to view if it worked.

---

### Post by cstein06 on 2012-12-03
thanks a lot, it worked for me.

---

