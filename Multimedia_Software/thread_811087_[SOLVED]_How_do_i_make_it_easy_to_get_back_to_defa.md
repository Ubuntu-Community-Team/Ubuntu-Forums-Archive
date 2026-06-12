---
title: "[SOLVED] How do i make it easy to get back to default"
date: 2008-05-28
forum: Multimedia Software
---

### Post by rover3500 on 2008-05-28
hi everyone.i keep trying all different drivers and formats for my ati 1650 card,but no luck yet.keep getting a black screen.how do i make it easy to put everything back the way it was b4?i keep having to reinstall,is driving me round the bend-at least 50 times now.am about to give up and go back to windows(oh no!).have posted a few threads about various things,like how to disable desktop effects from 'failsafe console' but no-one is helping...?am new to linux..thanx.-KDE remix(latest)

---

### Post by nhandler on 2008-05-29
Well, the easiest thing to do would be to backup a working installation of kubuntu to a different hard drive. That way, if/when you mess up the installation, you could just copy over the working installation. This would prevent you from having to do an install from the cd. If you are only modifying a few specific files, you could just back up those files (instead of doing a complete backup).

---

### Post by stickx911 on 2008-06-01
is there a command line I can do in the repair line to remove the ATI drivers, or use the default display drivers?

---

### Post by rover3500 on 2008-06-08
> **stickx911 said:**
> is there a command line I can do in the repair line to remove the ATI drivers, or use the default display drivers?
Thanx alot 4 your reply,was helpful.Have been away for a bit is why i didn't say thanx 4 a while...

---

### Post by rover3500 on 2008-06-08
> **Cheater said:**
> Well, the easiest thing to do would be to backup a working installation of kubuntu to a different hard drive. That way, if/when you mess up the installation, you could just copy over the working installation. This would prevent you from having to do an install from the cd. If you are only modifying a few specific files, you could just back up those files (instead of doing a complete backup).
Thanx alot 4 your reply,was helpful.Have been away for a bit is why i didn't say thanx 4 a while...

---

### Post by Rocket2DMn on 2008-06-11
You can reset your xorg settings by running
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE.
To remove restricted ati drivers, run
```
sudo apt-get remove --purge xorg-driver-fglrx
```
If you installed them with EnvyNG, they can be uninstalled from there.  If you installed them manually from ATI's website, the .run file should be able to uninstall them (unless you used a .deb, in which case the first command should work).

Hope that helps.

---

