---
title: "AMD Catalyst 12.8 released"
date: 2012-08-16
forum: Multimedia Software
---

### Post by Dr.Paneas on 2012-08-16
The new driver 12.8 for AMD Radeon HD is out there. It was very funny accident that the link was broken since yesteday :P Today they fixed it. 

You can download the driver of the [official website]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")
For any help with installing [check this]("http://ubuntuxtreme.com/news/amd-catalyst-12-8-released-install-guide/")

or you can just sudo apt-apt upgrade (in case you are using Xorg-Edgers PPA).

Please if you have **Radeon** and **GNOME 3** let me know if you have any **flickering/tearing** problems, see any **artifacts** etc.

---

### Post by MaxR84 on 2012-08-20
I'm still having troubles using Gnome and Unity (except for the without effect versions) also with this release.
May I ask you to take a look at the info tab of the Catalyst to confirm that under the voice driver package version the code is 8.96.7? I have updated but the *.run is named 8.98.2.

---

### Post by Dr.Paneas on 2012-08-22
Currently I am testing my new GTX, so had no time to bench with my Radeon. I can't help with GNOME 3 since I have no experience of that matter. Perhaps guyes over [World of Gnome]("http://worldofgnome.org") could help you. If Catalyst version is not updated, use the --force parameter.

[php]sudo dpkg --force-overwrite -i *.deb
[/php]

---

