---
title: "Can't login to Ubuntu after uninstalling alsa drivers"
date: 2008-05-20
forum: Multimedia Software
---

### Post by g0nzo on 2008-05-20
Hi,

I had problems with my soundcard in Ubuntu 7.10 and fixed it by installing alsa 1.0.16 from the sources (3 packages - alsa-driver, alsa-lib and alsa-utils).

After upgrading to Ubuntu 8.04, the soundcard behave really strange - generally it worked, but i.e. the sound volume in the panel was always muted after starting the computer and changing it didn't make any difference to the volume. Some players like VLC always worked, some, like i.e. Amarok, were somehow breaking my soundcard, so i.e. before running Amarok, I had sound in Rhythmbox, after running Amarok it was gone, sometimes sound in flash videos was gone etc.

I saw alsa-base 1.0.16 package installed in synaptic and figured out that maybe there's some conflict. So unfortunately I decided to uninstall manually installed alsa packages and reinstall alsa-base package.

Uninstalling went fine, reinstalling didn't went so well (it complained that it can't start gnome or sth).

After rebooting I can't login anymore - after typing my user/pass I get dialog box saying that my session lasted less than 10 seconds and that there's probably problem with Ubuntu installation.

Any ideas how to fix problem with logging in and how to properly install alsa drivers?

Regards

---

