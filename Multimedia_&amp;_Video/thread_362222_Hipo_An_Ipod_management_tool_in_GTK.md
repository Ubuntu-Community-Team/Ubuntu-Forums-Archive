---
title: "Hipo: An Ipod management tool in GTK"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by raul_ on 2007-02-15
How come my search in the forums produced merely 2 results with "hipo"?
Hasn't anyone heard of this?

Anyway, this is a pretty cool alternative to gtkpod (NOT A PLAYER). It's prettier and it's very straightforward: add music, remove music, edit tracks(including artwork), done.

[Homepage]("http://www.gnome.org/~pvillavi/hipo/") 

Anywayz, i found a problem after installing the Edgy package. Somehow, when i plugged my Ipod Nano, the program would crash. Pretty inconvenient for an ipod management tool. The error in the terminal was something about not finding the icon for my device. I did some digging and this worked:

> omment #7 from stacktracer  (reporter, points: 2)
2007-01-05 04:01 UTC [reply]

Well, I cannot for the life of me reproduce the problem.

  * uninstalled all hipo versions
  * manually removed the icon cache file from under /usr/local/
  * touched all the dirs in /usr/share/icons
  * updated the icon cache
  * installed hipo 0.1-1 (with which I saw the problem originally)

and ... it had no trouble finding the icon. This wasn't working last night;
either  Hipo's icons are still floating around in my icon cache somewhere, or
somehow installing the newer version fixed the problem for good.

Either way, this can be marked as fixed. Thanks for the quick response -- Hipo
rules!


From [http://bugzilla.gnome.org/show_bug.cgi?id=392593]("http://bugzilla.gnome.org/show_bug.cgi?id=392593")

NOTE:
You can touch all those dirs with
```

sudo touch /usr/share/icons/*

```

and update the icon cache with
```

gtk-update-icon-cache

```


Enjoy! :)

---

### Post by becominglumberg on 2008-01-09
I wholly agree that more people need to hear about Hipo. Before hearing about it, it would take me an eternity to load my ipod using gtkpod. For some reason, the program would grind to a hault after transferring songs in (I assume when it is writing the new itunes db). Anyway, Hipo is MUCH faster.

I really wish it would get more support in the gnome world, since its speed enhancements would be a boost to projects like Rhythmbox and Exaile where they currently use gtkpod, and the slowness problems also exist. Also, this would allow for the use of a Local Music Library (which would be an extremely useful addition to Hipo, as well).

---

### Post by Sammi on 2008-01-09
Ubuntu deb packages here: [http://www.getdeb.net/app.php?name=hipo](http://www.getdeb.net/app.php?name=hipo)

---

### Post by DarinB on 2008-01-31
hipo on my computer crashes the moment it is opened.
Can anyone tell me how to fix it OR how to Remove IT

---

