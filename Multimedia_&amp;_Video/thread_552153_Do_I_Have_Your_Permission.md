---
title: "Do I Have Your Permission?"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by sunus on 2007-09-16
Although I'm mostly a KDE user, I've always preferred Grip as a ripper to create Flac files from my CD's. So after installing Kubuntu 7:04, I subsequently installed Grip from Adept and Flac via apt-get install.

Grip was then able to rip CD's to .wav files but baulked at encoding them to Flac claiming that it did not have write permission. I confirmed this by running Grip as sudo, which worked but left me with files which are owned by root and have root as their group.

Which file permissions or possibly Group memberships do I need to change to get Grip to function for Users?

---

### Post by pheeror on 2007-09-16
cdrom

---

### Post by sunus on 2007-09-16
No, nothing to do with read only devices. I'm writing to hard drive. With root permissions, I'm able to write the .wav files and then these are converted to  .flac files. As a normal user, the .wav files are created but then an error message appears telling me I don't have write permissions. At a guess, I would say that the permissions for /usr/bin/flac are wrong or that something should be assigned to an Audio Group (or similar). But I don't know what.

---

### Post by sunus on 2007-09-16
Solved the problem by doing an apt-get remove on both Grip and Flac and then re-installing. Probably will never know which permissions were wrong :)

---

