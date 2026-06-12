---
title: "Amarok (2:1.4.8-0ubuntu1~gutsy1) iPod No Longer Works"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by RLovelett on 2008-02-04
I have Ubuntu 7.10 (Gutsy) and have been running my 3G iPod nano great since January.  Then (I think it was Friday) there was an update to Amarok in the repos and I performed the upgrade.  There where some files that where no longer needed, unfortunately I don't remember what they where (kde-desktop??) so I removed them (sudo apt-get autoclean && sudo apt-get autoremove).

Now my iPod is no longer seen by Amarok.  I know that it's mounting properly because gtkpod works great and can see, edit and delete stuff from my iPod.  I can use gtkpod for the time being to send file to and from my iPod, but I'd really like to have Amarok back as I like it more.

When I tell it to "Autodetect Devices" in "Configure Amarok" this is the error that I get back.

[QUOTE="Amarok"]No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.[/QUOTE]

I've already tried "Mark for Reinstallation" in the Synaptic Package Manager and even "Mark for Complete Removal".  I don't think this worked as expected because when I installed it again, it retained all of it's previous settings.  In other words it already new the setup (username and password for my MySQL database).

Amarok (2:1.4.8-0ubuntu1~gutsy1)
libgpod2 (0.5.3+actually0.6.0)

Please let me know if I can give any more information.  I'd really like to see this problem solved!

Thanks,
Ryan

---

### Post by RLovelett on 2008-02-27
Update I had enabled the gutsy backports by accident and this is the version of Amarok in the backports.  It does not have MTP support.  I removed the backports list from my sources and went back to 1.4.7, so all has been fixed.

---

