---
title: "Upgrade Mythbuntu 8.10 to 9.04 advice?"
date: 2009-05-06
forum: Mythbuntu
---

### Post by pcooley on 2009-05-06
Checking with the community on this.

I currently have a first time (aka beta) Mythbuntu running at my home to learn the ropes.  I set it up on 8.10 and plan to upgrade to 9.04. I am hoping for the minimal downtime upgrade scenario.  

I purchased 2 identical hard drives (one in use, one a spare) and pose the question:
** should I simply clone the system to the secondary drive (backup) and run use the Ubuntu 9.04 upgrade scenario ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)) or install from the Mythbuntu 9.04 live cd on the 2nd drive and move some DBs, files, and configuration over?


Further Hardware Details

Case: Fusion Remote Black - [http://www.antec.com/Believe_it/product.php?id=NzE4](http://www.antec.com/Believe_it/product.php?id=NzE4)
Motherboard: Asus M3N78-EM on board video Geforce 8300 [http://usa.asus.com/products.aspx?l1=3&l2=149&l3=676&l4=0&model=2260&modelmenu=1](http://usa.asus.com/products.aspx?l1=3&l2=149&l3=676&l4=0&model=2260&modelmenu=1)
CPU: 65w AMD Athlon 64 X2 5200 Brisbane 2.7GHz
Optical: LiteOn DVD-RAM
Tuner: HD Homerun - [http://www.silicondust.com/](http://www.silicondust.com/)
HDs: 2 x Western Digital Green 1TB - WDC WD10EADS-00L

---

### Post by wizgnome on 2009-05-06
Don't, if you need to use the MythBrowser plugin as it has been removed.

---

### Post by pcooley on 2009-05-06
Thanks for the heads up.  In my case I haven't even started the mythbrowser plugin.

---

### Post by bobbob1016 on 2009-05-06
If you are upgrading, mythbrowser stays.  I upgraded and kept mythbrowser, if you are doing a fresh install, then I don't know how easy it is to keep mythbrowser.

I had an issue with sound not going over spdif, but I fixed it by adding some line to a conf file, I found it on the forums quickly, so I'm not sure what line and to what file at the moment.

---

### Post by pcooley on 2009-05-06
What audio processor do you have (that spdif stopped working on 9.04)?  Mine, in the Asus M3N78-EM, is a "Realtek ALC1200 8-Channel High Definition Audio Codec."

---

### Post by chcubsfan on 2009-05-07
> **wizgnome said:**
> Don't, if you need to use the MythBrowser plugin as it has been removed.

I grabbed the mythbrowser deb for Intrepid and installed it, seems to work fine.

---

### Post by jaakan on 2009-05-07
> **pcooley said:**
> Checking with the community on this.

I currently have a first time (aka beta) Mythbuntu running at my home to learn the ropes.  I set it up on 8.10 and plan to upgrade to 9.04. I am hoping for the minimal downtime upgrade scenario.  

I purchased 2 identical hard drives (one in use, one a spare) and pose the question:
** should I simply clone the system to the secondary drive (backup) and run use the Ubuntu 9.04 upgrade scenario ([http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)) or install from the Mythbuntu 9.04 live cd on the 2nd drive and move some DBs, files, and configuration over?


Further Hardware Details

Case: Fusion Remote Black - [http://www.antec.com/Believe_it/product.php?id=NzE4](http://www.antec.com/Believe_it/product.php?id=NzE4)
Motherboard: Asus M3N78-EM on board video Geforce 8300 [http://usa.asus.com/products.aspx?l1=3&l2=149&l3=676&l4=0&model=2260&modelmenu=1](http://usa.asus.com/products.aspx?l1=3&l2=149&l3=676&l4=0&model=2260&modelmenu=1)
CPU: 65w AMD Athlon 64 X2 5200 Brisbane 2.7GHz
Optical: LiteOn DVD-RAM
Tuner: HD Homerun - [http://www.silicondust.com/](http://www.silicondust.com/)
HDs: 2 x Western Digital Green 1TB - WDC WD10EADS-00L


I ran in to two issues updating from 8.10 to 9.04

1. removed everything from medbuntu repo you have installed or the updated might crap out near the the tail end when it tries to get the MS fonts

2. the backend seems to be crashing now and than, I think something in how the Database changed, database optimize/repair + 2 reboots seems to fix it

there was an update for Mysql yesterday I had to rerun optimize/repair and rebooted 2 times this morning and everything was ok again.

if you don't have many recordings just do a clean install of 9.04

---

### Post by Blastz on 2009-06-03
Avoid 9.04 if you have a Nebula PCI card. Kernel 2.6.28, which ships with 9.04 will not tune this card nor let it display pre-tuned channels.

I tried installing kernel 2.6.27 and the tuner worked when I booted in that kernel but other things had problems so I went back to 8.10.

There are bug postings about this.

---

