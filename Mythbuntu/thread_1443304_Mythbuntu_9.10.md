---
title: "Mythbuntu 9.10"
date: 2010-03-30
forum: Mythbuntu
---

### Post by turtle02 on 2010-03-30
I have had 9.10 installed on my compaq s5100nx on a ide HDD and everything works fine.

I am upgrading to a 1TB sata HDD I have a VIA 6421 pci sata controller with 1 sata hdd plugged into it.

When i load mythbuntu 9.10 to install it says sata port io error. when the installer loads and i get to the partition screen it sees my entire drive and i get the option to format the entire drive. I pick that option and fill out the rest of the installers 10 questions. When mythbuntu starts installing it gets to like 5% on formatting the drive and stays there, i have left my machine on for days and the installer never gets any further. So I ask is there any fixes or work arounds or any more info needed? Thanks

---

### Post by SiHa on 2010-03-31
Not exactly an answer, but a suggestion.
What quite a lot of people like to do (myself included) is have separate drives for the OS and media. This makes re-installs a whole lot easier, especially if you backup your database to this drive as well.
The way I have it is the install on the IDE drive, and mount the 1TB drive at /var/lib/mythtv, with all the myth subfolders (recordings, music, livetv etc.) on the root of the extra drive.

---

### Post by turtle02 on 2010-03-31
I think that is what i will do but i cannot get mythbuntu to recognize that drive until i get it formatted and gparted still willnot format the drive it is having communications problems

---

### Post by SiHa on 2010-04-01
Sounds more like a hardware/driver problem with your SATA card. Perhaps you'd be better off posting in the [[COLOR="Blue"]_hardware_[/COLOR]](http://ubuntuforums.org/forumdisplay.php?f=332) forum.

---

### Post by 4dognight on 2010-04-01
Also, beware there is a bug in gparted with 2.6 kernels. You need to get .51 or later version.9.10 ships with .45 I believe. I doubt this is your problem, but just letting you know.

---

