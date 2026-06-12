---
title: "Natty Factory Reset After Upgrade"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rykel on 2011-04-03
Hi, after upgrading to Natty, how do I do a "factory reset" so that I can experience Natty as it is out of a new box?

Specifically, how do I reset to the defaults for:

[LIST]
[*]Grub2 looks and behaviour
[*]Boot up splash
[*]Login Manager
[*]Desktop startup screen, sounds, wallpaper, icons, panels etc.
[*]Shutdown screen
[/LIST]

---

### Post by drs305 on 2011-04-03
I can only answer for Grub 2. You can purge it and reinstall from the repositories. You purge grub-pc and grub-common, then reinstall them:

```
sudo apt-get update # Make sure your Internet connection is working.
sudo apt-get purge grub-common # Will purge both packages. You will be asked to confirm.
sudo apt-get install grub-pc # Installs both packages. See notes below. 
```
Notes for installation: Use TAB to OK, press spacebar to select the *drive(s)*. Do NOT install to any partition unless you have a specific need to do so.

---

