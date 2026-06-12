---
title: "Updating Mythtv to 0.26 not working"
date: 2014-01-16
forum: Mythbuntu
---

### Post by mcapaldo on 2014-01-16
I have Ubuntu 12.04 64 Bit, and Mythtv 0.25 according to front end system status.  I have the Mythtbuntu control center installed and checked the update Mythtv Repo and chose 0.26 next to it, then manually removed the 0.25 updates from Update Manager.  I Clicked Refresh/reload and the 0.26 files show up but will not install, the 1st one is checked but rest are greyed out and when I try to install it says no updates available or run a partial upgrade.

What am I doing wrong?

I tried terminal "sudo apt-get update" also and did not seem to do anything.  

I stopped backend and purposly choose wrong password so it should not have re-started to run update manager but no help

Any ideas?

---

### Post by tuat2 on 2014-01-17
Dependencies have changed. Therefore, you need to use a terminal and use "sudo apt-get dist-upgrade". The updater tool only does an "apt-get upgrade", which doesn't work in this case.

---

