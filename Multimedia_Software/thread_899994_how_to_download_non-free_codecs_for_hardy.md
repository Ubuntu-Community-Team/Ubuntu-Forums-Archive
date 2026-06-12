---
title: "how to download non-free codecs for hardy?"
date: 2008-08-24
forum: Multimedia Software
---

### Post by A117 on 2008-08-24
i've read a couple of posts but still fail.
the top post in here requires me to set medibuntu as a repository.
the nongeeksight post was for dapper, which said the only things are libxine-extracodecs and w32codecs.

i want to download packs and install them on different machines. so repository addition is my last choice.
i installed w32codecs. but found no libxine-... for hardy in medibuntu's pool. what's more, libxine1-... are not installed on my xubuntu by default.

except w32codecs, what else should i download and install please? thank you.

---

### Post by jimmy the saint on 2008-08-24
[http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

You can download and save the packages here in medibuntu.  Also you can install the xubuntu-restricted-extras package which includes many usefull packages including windows fonts, flash and some codecs (mp3, DVD etc).

---

### Post by A117 on 2008-08-24
> **jimmy the saint said:**
> [http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

You can download and save the packages here in medibuntu.  Also you can install the xubuntu-restricted-extras package which includes many usefull packages including windows fonts, flash and some codecs (mp3, DVD etc).

i found the place, but donno what to download. libxine1*?

---

### Post by aysiu on 2008-08-24
**Step 1**
Run ```
sudo apt-get clean
``` **Step 2**
Install the codecs you want.

**Step 3**
Go to /var/cache/apt/archives and find all the .deb files for those codecs

**Step 4**
Copy them to the appropriate medium.

---

### Post by jimmy the saint on 2008-08-24
linxine1 should be it.  Unless you will be installing this on a bunch of computers that either have no internet connection, or that use dial up, it is easier to just add the repository.  You don't have to even type anything!

Go here ---- [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)   ----  and copy the appropriate commands into a terminal.  Incredibly easy and fast.  alternately, you could open up synaptic and copy the address portion of the command in the repo section, but that takes way to long.

---

### Post by A117 on 2008-08-25
the /var/cache/apt/archives method is nice, though i still downloaded single packages manually.
libxine1 is not enough, totem-xine is needed too. original totem-gstreamer is removed and now totem plays my mp3 and wma:guitar:

---

