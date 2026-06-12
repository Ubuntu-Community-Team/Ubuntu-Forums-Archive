---
title: "gtk2.0 issues with totem (and other apps)"
date: 2009-04-27
forum: Multimedia Software
---

### Post by Greedo on 2009-04-27
Hi, 

I'm hoping that someone can help me out with an issue I've been having for the last day or so - in that my totem won't start (as well as some other programs which I think are related to this same issue - i.e. I can't get my software sources screen to come up anymore and when I try to click on the computer icon from the places menu then I get an alert box which says "Couldn't display computer - Nautilus cannot handle computer: locations."

When I just click on the movie player icon in the applications list then I get the app starting to open and then it just shuts down. 

When I tried to start totem from bash here was my output
```
totem: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: atk_relation_set_add_relation_by_type

```

When I tried starting nautilus from bash then it did start but showed me this error:
```
** (nautilus:7508): WARNING **: Unable to add monitor: Operation not supported

```

I believe this all has to do with the gtk library, which I might have fraggled a little when I was doing an upgrade of gimp to 2.6 manually from source before I found the deb packages. 

I looked at doing an apt-get remove libgtk-2.0_0, but that looked like it would remove my gnome and about 200 other things when all I wanted was to fix this library itself. When I do apt-get install libgtk-2.0_0 then it tells me "libgtk2.0-0 is already the newest version"

my vlc player will start, but it looks a bit different in the past day or so with a much newer interface, I didn't update this at all, but I think it might be linked to the new libraries I was installing when preforming the gimp compile like babl and gegl and libpng.

Any help on how to remedy this is appreciated,

BTW - I'm running Hardy Herron

---

### Post by Greedo on 2009-04-27
I've fixed my issue it seems (for now) and I'll share how I did it...

I went back to the configure_log of the GTK+-2.16.0 library where I was trying to compile and saw in the log near the end where it needed a different atk library. 

I was able to find that exact version here:
[http://ftp.acc.umu.se/pub/gnome/sources/atk/1.13/]("http://ftp.acc.umu.se/pub/gnome/sources/atk/1.13/")

I re-complied that and did a make then make install, and then I could finally see my sofware sources and update manager. 

Running a check of the update manager fixed my totem. 

This may or may not work for you if you're having the same types of issues

---

