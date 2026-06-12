---
title: "Laptop GeForce Go 7800GTX No Display"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by deadfolk on 2007-02-03
Hi all,

I have finally just bitten the bullet and installed Edgy on my laptop (which is the machine I use most).  Pleasant experience overall - even the Wi-Fi works without a hitch, which is better than I can do on my desktop.

Anyway, obviously I have a problem, or I wouldn't be posting in this forum, so here goes:
I can't get the nvidia drivers to work.  If I use "nv" in my xorg.conf file, I can get a display (but only at 1024x768, which looks horrible on my laptop).  I have followed several guides to install the actual "nvidia" driver, but with every single one, when X starts, I hear the startup sound, but I only get a blank screen.  I can't press ctrl+alt+f.. to get a terminal.  I have to start up in recovery mode and change the xorg.conf back to using "nv".

If anyone could help, I would be extremely grateful - this screen really does look horrid!:(

Thanks,

DF

---

### Post by LostShootingStar on 2007-02-03
gave you tried using Automatix to install the drivers? also, in your xorg.conf file, you can add extra display "modes" or resolutions. you will see where it specifies 1024x768, just add "1280x1024" or whatever resolution you use in windows in the same format

```

        SubSection "Display"
                Depth           24
                Modes           "1024x768" "1280x1024"
        EndSubSection

```

---

### Post by deadfolk on 2007-02-03
Yep - tried both of those.  Automatix was the first thing I did upon install.

I added more resolutions into the xorg.conf file, but when I go to System\Preferences\Screen Resolution, they do not appear.  Is there somewhere else I can set the resolution?

---

