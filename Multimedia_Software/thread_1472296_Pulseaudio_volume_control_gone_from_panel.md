---
title: "Pulseaudio volume control gone from panel"
date: 2010-05-04
forum: Multimedia Software
---

### Post by satbunny on 2010-05-04
I upgraded from 9.10 to 10.04 and my volume control disappeared from the panel. I have reinstalled pulseaudio but it had not re-appeared. I can't find it in the Add Panel list nor can I find it in the Pulseaudio volume control application as an option.

Help?

---

### Post by inameiname on 2010-05-04
I found this when I was in search of a resolution to the same problem.  And it seems to work:

                                 go to System > Preferences >  Startup Applications

in the startup tab, look for 'Volume Control' and check it if its  unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....

---

### Post by dabl on 2010-05-04
The pulseaudio volume control is a package named pavucontrol.  There's also a pulse manager package that you might want.
```

sudo apt-get update && sudo apt-get install pavucontrol paman
```

Then you can choose to place the pavucontrol icon on your panel in the normal manner.

---

### Post by satbunny on 2010-05-07
Thanks. SOLVED.

---

### Post by balaji31d on 2011-01-25
Dabl Suggestion solved the issue. thanks.

---

### Post by erkout on 2011-06-24
after googling for days and searching forums and following every instruction proposed i still cant get my volume control back 

i tried this
```
sudo apt-get update && sudo apt-get install pavucontrol paman
```and i tried

> go to System > Preferences >  Startup Applications

in the startup tab, look for 'Volume Control' and check it if its  unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....     and still without any luck!!

---

