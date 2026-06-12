---
title: "Nvidia resolution change crashed my Ubuntu"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by iheartubuntu on 2007-10-01
I was able to change my nvidia screen resolution to 1440x900 (the default in my windowsXP) and it looked great, worked great, felt great, then when I rebooted I can no longer access my Ubuntu partition. Any tips?

I believe I cannot access the system because of the resolution change (i could be wrong). Once Ubuntu starts to load up, the screen go blank for a while, then I get some text on the screen... I dont know if this is all of it, the left side of the text could be chpped off... but what I can see is this:

[B]/bin/sh: cant access tty; job control turned off

initramfs)[/B]

and then I have an option to type something on that command line (feels sort of like a terminal). If I type help, it gives me a list of commands, but I have no idea what to do.

If there was some way I could change my resolution, I might be able to access Ubuntu again.

I am not a fan of other screen resolutions.. .1440x900 is my standard in XP... Id like to keep it like that in Ubuntu if possible.

---

### Post by iheartubuntu on 2007-10-01
bump
anyone?
please?

---

### Post by fain on 2007-10-01
check your /etc/X11/xorg.conf

heres a HOWTO set your resolution
[http://ubuntuforums.org/showthread.php?t=83973&highlight=change+resolution]("http://ubuntuforums.org/showthread.php?t=83973&highlight=change+resolution")

---

