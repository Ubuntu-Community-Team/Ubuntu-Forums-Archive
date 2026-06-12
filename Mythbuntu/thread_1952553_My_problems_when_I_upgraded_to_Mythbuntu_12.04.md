---
title: "My problems when I upgraded to Mythbuntu 12.04"
date: 2012-04-04
forum: Mythbuntu
---

### Post by ernstp on 2012-04-04
Hi!
I made a backup and jumped into the cold water and upgraded to Mythbuntu 12.04.

Here's a list of the problems I had directly after the upgrade:

* Volume control stopped working. I uninstalled Pulseaudio and switched to bare metal Alsa. I also noticed some performance problems disappeared when switching to Alsa.
* The upgrade installed mysql-5.5. When I later purged mysql-5.1 from the system, mysqld didn't start automatically anymore. sudo dpkg-reconfigure mysql-something solved the problem.
* The picture was horrible! :-) Hue was reset to 0, should be 50. Took a few minutes googling to find. And btw, you can't change it from settings, you have to start watching something and change it from the menu there AFAIK.
* I think there was something else also, will add it if I remember...
(Haven't filed bugs yet.. :-()

How it's working:
* Fine! :-)
* Switched to OpenGL UI, works great, a few nice animations here and there.
* Live TV, watching recordings, DVD and video-file playback works great, no crashes or problems there so far.
* I think scheduled recordings are having problems, haven't investigated yet...

Hardware:
Amd 4850e
Mobo with integrated Radeon 3200
Mystique TeRiX T2 DVB-T card (paid subscription @ Boxer/Sweden)

---

### Post by nickrout on 2012-04-04
What did you upgrade from (ubuntu version and mythtv version)?

---

### Post by ernstp on 2012-04-04
> **nickrout said:**
> What did you upgrade from (ubuntu version and mythtv version)?

11.10 with MythTV 0.24-fixes.

---

### Post by tgm4883 on 2012-04-04
> **ernstp said:**
> Hi!
I made a backup and jumped into the cold water and upgraded to Mythbuntu 12.04.

Here's a list of the problems I had directly after the upgrade:

* Volume control stopped working. I uninstalled Pulseaudio and switched to bare metal Alsa. I also noticed some performance problems disappeared when switching to Alsa.
* The upgrade installed mysql-5.5. When I later purged mysql-5.1 from the system, mysqld didn't start automatically anymore. sudo dpkg-reconfigure mysql-something solved the problem.
* The picture was horrible! :-) Hue was reset to 0, should be 50. Took a few minutes googling to find. And btw, you can't change it from settings, you have to start watching something and change it from the menu there AFAIK.
* I think there was something else also, will add it if I remember...
(Haven't filed bugs yet.. :-()

How it's working:
* Fine! :-)
* Switched to OpenGL UI, works great, a few nice animations here and there.
* Live TV, watching recordings, DVD and video-file playback works great, no crashes or problems there so far.
* I think scheduled recordings are having problems, haven't investigated yet...

Hardware:
Amd 4850e
Mobo with integrated Radeon 3200
Mystique TeRiX T2 DVB-T card (paid subscription @ Boxer/Sweden)

Mythbuntu doesn't install pulseaudio.

---

### Post by jaakan on 2012-04-28
"sudo dpkg-reconfigure mysql-server-5.5" 

Did the trick for me. I should not have ignored the upgrade part where it asked me to set a new password for mysql

> **ernstp said:**
> Hi!
I made a backup and jumped into the cold water and upgraded to Mythbuntu 12.04.

Here's a list of the problems I had directly after the upgrade:

* Volume control stopped working. I uninstalled Pulseaudio and switched to bare metal Alsa. I also noticed some performance problems disappeared when switching to Alsa.
* The upgrade installed mysql-5.5. When I later purged mysql-5.1 from the system, mysqld didn't start automatically anymore. sudo dpkg-reconfigure mysql-something solved the problem.
* The picture was horrible! :-) Hue was reset to 0, should be 50. Took a few minutes googling to find. And btw, you can't change it from settings, you have to start watching something and change it from the menu there AFAIK.
* I think there was something else also, will add it if I remember...
(Haven't filed bugs yet.. :-()

How it's working:
* Fine! :-)
* Switched to OpenGL UI, works great, a few nice animations here and there.
* Live TV, watching recordings, DVD and video-file playback works great, no crashes or problems there so far.
* I think scheduled recordings are having problems, haven't investigated yet...

Hardware:
Amd 4850e
Mobo with integrated Radeon 3200
Mystique TeRiX T2 DVB-T card (paid subscription @ Boxer/Sweden)

---

