---
title: "Ubuntu won't boot after changing xorg.conf"
date: 2010-09-07
forum: Multimedia Software
---

### Post by GROwen on 2010-09-07
Hi all,

I changed my xorg.conf file to see if the nVidea graphics card I'm using supports coolbits and after restarting gdm my installation won't boot past the Ubuntu splash screen, the one with the circles underneath Ubuntu (I have auto login).

I'm running 10.04.

Thanks in advance for any help that can be offered.

---

### Post by wojox on 2010-09-07
Reboot and after the BIOS screen hold down the left <Shift> key and choose recovery mode. There should be an option about failsafe X.

If that doesn't work drop into a root shell and run 

```
nvidia-xconfig
```

---

### Post by JBAlaska on 2010-09-07
And if that does not work, rename xorg.conf xorg.old and restart

---

### Post by GROwen on 2010-09-08
Cool, thanks for the tips guys.

---

### Post by wojox on 2010-09-08
Did any of the tips work? 

If so you you state which one and mark as solved for the next individual who comes along with the same question.

---

### Post by VanillaMozilla on 2010-09-08
The other way is to boot in recovery mode.  That will get you a command line.  Rename xorg.conf xorg.conf.sav or something like that.  Then the old file will still be there.  I forget what it's called, maybe xorg.conf~ .  (I forget some details--I'm on Windows at the moment.)

So typical commands would be

cd /etc  (or whatever the directory name is -- I forget)
mv xorg.conf xorg.conf.sav
mv xorg.conf~ xorg.conf

Then reboot and you're on your way.  You could also edit the file, but:
(1) be sure to copy the existing backup file to another file name (so you don't lose it forever).
(2) You'll need a command-line editor.  vi is usually used.  Good luck.

---

