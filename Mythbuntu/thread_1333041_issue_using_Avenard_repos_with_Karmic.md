---
title: "issue using Avenard repos with Karmic"
date: 2009-11-21
forum: Mythbuntu
---

### Post by fredcorp on 2009-11-21
I'm having some dramas using Avenards repositories with Karmic. 

As per the instructions on his site I enabled the repos and reload however it didn't give me an option to upgrade the nvidia-185 files. Instead it's reporting they are the latest version and then it goes on to crash and subsequently reports I have a broken package.

This is the error;
dpkg: error processing /var/cache/apt/archives/libvdpau1_0.2.1-0ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9

---

### Post by Nikas on 2009-11-21
> **fredcorp said:**
> I'm having some dramas using Avenards repositories with Karmic. 

As per the instructions on his site I enabled the repos and reload however it didn't give me an option to upgrade the nvidia-185 files. Instead it's reporting they are the latest version and then it goes on to crash and subsequently reports I have a broken package.

This is the error;
dpkg: error processing /var/cache/apt/archives/libvdpau1_0.2.1-0ubuntu3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9

Try this first:
sudo apt-get install libvdpau1

Then try apt-get upgrade

Same error? Try:
```
sudo dpkg -i --force-all /var/cache/apt/archives/libvdpau1_0.2.1-0ubuntu3_i386.deb
```

---

### Post by williammanda on 2009-11-21
Here is a post on how to avoid the error you recieved:

[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html]("http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html")

---

