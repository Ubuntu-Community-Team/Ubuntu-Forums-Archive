---
title: "nVidia Drivers"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by CaptainMorgan08 on 2007-07-12
This has probably been asked a million times, but I cannot get nVidia drivers to work on Ubuntu.  I just recently downloaded and installed Ubuntu Feisty from Ubuntu's site.  I have dual GeForce 8800 GTX's.  I have tried following tutorials from at least 5 different sites, but all of them resulted in the X Server not being able to start.  I would really appreciate it if someone could help me through this.

---

### Post by benerivo on 2007-07-12
I'm not sure what methods you have already tried, but the simplest is usually using the system installation from system>prefs>desktop effects, or failing that Automatix.

---

### Post by kansas_plainsman on 2007-07-12
In my case the settings dialogs were ineffective - the reported resolution was quite incorrect, and nothing I did could change it in any useful way,

I ended up opening a terminal window and running:

    sudo dpkg-reconfigure xserver-xorg

Answered the prompts (had to know technical details of the card and monitor), which didn't result in a correction, BUT it did put useful lines in the xorg.conf file.  I then edited the xorg.conf file down to only the lines I KNEW were correct - commenting out the incorrect resolutions and such.

Side note: I also removed all the mysterious watcom tablet entries which get put in the xorg.conf file (by something in the kubuntu install).  Once I did that, I got my normal resolutions.  To be on the safe side, I saved a copy of the xorg.conf file off to a backup drive.

This is really a problem with ubuntu.

---

### Post by FetusHunter on 2007-07-12
I'm also having the same problem, and neither of these suggestions worked. Thanks for the help so far everybody, but does any one have any more ideas?

---

