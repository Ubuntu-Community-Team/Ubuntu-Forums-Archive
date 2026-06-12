---
title: "Instructions needed for console reinstall of ATI/open drivers"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by two00lbwaster on 2007-12-30
I need someone to instruct me on how to get my graphics working on 64bit Gutsy as they're so completely screwed that I can't understand the display output.

The console mode is fine however so I just need some brief printable instructions that I can follow on reinstalling ATI drivers.  I think the graphics were screwed from going from ati restricted back to the open drivers(I don't need 3d).

I hope that there's someone that can help me out here as I'm fairly new to Linux but want to learn it a bit better (already worked out things like replacing gedit w/nano in console mode).

---

### Post by erfahren on 2007-12-31
by "console mode" are you referring to doing it like from the command line in recovery mode?

anyway, get to the command line and enter your password if it asks for the root password.

then type in 
```

dpkg-reconfigure xserver-xorg

```
(if you're not runing as root you'll have to do:
```

sudo dpkg-reconfigure xserver-xorg

```
and enter your password.)

anyway, you'll be taken through some steps to reconfigure the X Server (the /etc/X11/xorg.conf file)

you can just accept the defaults on most. When you get to select the display driver part you won't want "vesa" - that's the default generic driver - take the open-source driver that's available for your card.

to reboot from the command line type (shutdown reboot now):
```

shutdown -r now

```

(I haven't seemed to be able to find much documentation on it but here's some other info on it:
[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server) )

(it'll automatically create a backup of your /etc/X11/xorg.conf file)

hope that helps

---

### Post by two00lbwaster on 2007-12-31
Hi,

Thanks for getting back to me.  I did manage to get a graphical display back by doing pretty much what you suggested though I also blacklisted the fglrx driver too.

I should have posted back but it was 4:40 when I crawled back to bed.

And yes bad windows terminology creeping that I should have said was via the tty1 terminal.

But now I'm stuck at a resolution of 800x600. I get the option to choose graphics card driver and monitor resolution at boot but it doesn't keep the settings.  I'll start a new thread about that though.

---

