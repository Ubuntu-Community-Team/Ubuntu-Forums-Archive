---
title: "Envy 0.9.3-0ubuntu6"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by drietow on 2007-06-03
I'm trying to install my Nvidia Geforece4 MX 4000 PCI card on a Compaq 5003US computer.
After much failed attempts I tried Envy 0.9.3-0ubuntu6.  After running Option #1 my xserver came up for the very first time ever.  I ran it through every programs I wanted and had no problems however once I rebooted I was back to nothing working.  I tried to uninstall and reinstall the drivers using Envy but again I can't get my xserver up.  What do I do know?

---

### Post by tseliot on 2007-06-03
Envy made a backup of your xorg.conf.

Boot in Recovery mode and type:
```
ls /etc/X11/

```
you will see something like this:
```
xorg.conf
xorg.conf_backup_200702271039
```

the file with the “backup” word is the one you’re looking for.

type:
```
sudo cp xorg.conf_backup_200702271039 xorg.conf
```

and type this to restart your computer:
```
reboot
```

---

### Post by drietow on 2007-06-03
Looks like I screwed it up so bad that I had not luck with the backup.
I was able to start xserver but manually 
sudo_dpkg-reconfigure xerver-xorg
So I'm back to using my onboard controler 'Intel i810'.  I've had the taste

---

### Post by drietow on 2007-06-03
OK this time I ran Envy 0.9.4-0ubuntu6 (UNSTABLE RELEASE), Again the xserver loaded but I have an error
Internal Error
Failed to initialize HAL!

I ignorred the Error and rebooted.  Everything came back up again but without the Error.

Should I be conserned about this HAL! error?

Before I forget "YOU ARE THE MAN!!".  I am one happy dude!

---

