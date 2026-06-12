---
title: "audio jack not working"
date: 2011-08-23
forum: Multimedia Software
---

### Post by bahjat on 2011-08-23
hello i am fairly new to ubuntu and i have a toshiba satellite A200 32 bit
my sound from internal speakers is working but every time i connect my headphones it doesn't work any idea why thank you in advance.

this is the link for the script : [http://www.alsa-project.org/db/?f=1c0e6dc078d96c7fd02bc5904c33924b18d69c27](http://www.alsa-project.org/db/?f=1c0e6dc078d96c7fd02bc5904c33924b18d69c27)

---

### Post by handy on 2011-08-23
Welcome to the forums; have you been through this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

When you do find a solution to a thread you start, it is appreciated if you open you original post (OP) & mark the beginning of the title as [SOLVED]. Enjoy your stay.

---

### Post by bahjat on 2011-08-23
i have tried that solution but it didn't work every time i get to step 4 and type in this code : 

sudo modprobe snd-

it gives me fatal commandnot found or something like that

---

### Post by lidex on 2011-08-24
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=toshiba" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by bahjat on 2011-08-24
@lidex using that code didn't work i entered it and after it askes me to enter my password nothing happens it stays open this is what i get:

bahjat@Godzilla:~$ echo "option snd-hda-intel model=toshiba"
option snd-hda-intel model=toshiba
bahjat@Godzilla:~$ sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for bahjat: 


and i have rebooted and nothing changed!

---

### Post by lidex on 2011-08-28
> **bahjat said:**
> @lidex using that code didn't work i entered it and after it askes me to enter my password nothing happens it stays open this is what i get:

bahjat@Godzilla:~$ echo "option snd-hda-intel model=toshiba"
option snd-hda-intel model=toshiba
bahjat@Godzilla:~$ sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for bahjat: 


and i have rebooted and nothing changed!

Did you copy and paste that command or type it in? There is a typo, option should be option[COLOR="Red"]s[/COLOR]
Change it here:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

