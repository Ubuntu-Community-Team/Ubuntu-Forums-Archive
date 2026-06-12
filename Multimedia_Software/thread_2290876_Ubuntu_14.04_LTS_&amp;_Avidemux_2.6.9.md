---
title: "Ubuntu 14.04 LTS &amp; Avidemux 2.6.9"
date: 2015-08-16
forum: Multimedia Software
---

### Post by czgirb on 2015-08-16
Just installed **Avidemux 2.6.9** via the following tutorial [http://ubuntuhandbook.org/index.php/2015/05/avidemux-2-6-9-release-how-to-install-in-ubuntu-15-0414-04/](http://ubuntuhandbook.org/index.php/2015/05/avidemux-2-6-9-release-how-to-install-in-ubuntu-15-0414-04/) after everything is done, i unable to RUN it.

**Note:**
Within **Applications > Sound & Video**, I saw there is **2 Avidemux**.
[B]* Avidemux 2.6 (GTK+)
* Avidemux 2.6 (Job)
[/B]
Why I can't have it run? I **100% believe that there is no wrong with the tutorial**.
It's me, and it should be me ... which make a mistake during the process, which I do not know.

Is having **two Avidemux menu** is normal? If not, how can I solve it?
Please guide me ... thank you

---

### Post by mc4man on 2015-08-16
Start it from a terminal & see what shows up. (seems broken on gtk3 or glib) run command is - 
avidemux3_gtk
You may have more luck with the qt version - avidemux2.6-qt

---

### Post by czgirb on 2015-08-17
> **mc4man said:**
> Start it from a terminal & see what shows up. (seems broken on gtk3 or glib) run command is - 
avidemux3_gtk
You may have more luck with the qt version - avidemux2.6-qt

**SORRY** ... yesterday, i run:[B]
1. sudo apt-get remove avidemux2.6
2. sudo apt-get remove avidemux2.6-gtk[/B]
**3.** ... the last, i **remove the uninstall software, avidemux, via synaptic package manager**
and restart the notebook

but **avidemux (Job)** within **Sound & Video**'s drop down menu still exist
 ... and when I click it, it still able to show-up the job's list
how can I totally remove it?

---

### Post by mc4man on 2015-08-17
with
```
sudo apt-get purge avidemux2.6-jobs
```
(the qt version does work, why the gtk version is still in 14.04 for getdebs is unclear, maybe it worked at release but no more.

---

### Post by czgirb on 2015-08-17
**SORRY** ... just run:
**  sudo apt-get autoremove**
and all removed ... **SORRY**
Will give it avidemux installed and report back again.
**Thank you**

---

