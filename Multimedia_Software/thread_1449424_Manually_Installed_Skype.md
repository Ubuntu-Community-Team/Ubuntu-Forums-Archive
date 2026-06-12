---
title: "Manually Installed Skype"
date: 2010-04-07
forum: Multimedia Software
---

### Post by CarlosinFL on 2010-04-07
I have never used Skype or had a need to however today I was told that I need to have a video chat over the web using Skype. I loaded my Samsung netbook with Skype and installed 9.10 Netbook remix. It works OK but when it came to install Skype, I went to Skype's site and downloaded the Ubuntu .deb package and manually installed it. It installed fine after needing some dependencies which I self resolved however I was wondering if this was OK? Should I have installed Skype using Apt?

---

### Post by progre55_icky on 2010-04-07
It's okay, as the default Ubuntu repos do not contain skype.
You could, on the other hand, add the medibuntu repos into your /etc/apt/sources.list.
just append the following line into sources.list and "apt-get update":
```
deb http://packages.medibuntu.org/ karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
```then you can install skype using apt.

/progre55

---

### Post by CarlosinFL on 2010-04-08
Skype manual install appears to be working fine on my Netbook so for now I will leave it as is.

Thanks.

---

### Post by Island_Jon on 2010-04-10
I found the Skype for Linux **[COLOR="DarkRed"]Beta[/COLOR]** v2.1.0.81 direct from Skype's web site to be the easiest method of installing -- better than using Medibuntu.

My first attempt to install was by enabling Medibuntu and using Synaptic to install: skype-mid, libqt4-svg and it DID succeed in installing. 
**_However_** once I started the application and registered an account (successfully) I _could not login_ to the newly created account. I therefore used Synaptic to uninstall both skype-mid, libqt4-sv and just downloaded the Skype for Linux Beta v2.1.0.81 package from the Skype website as described in [http://ubuntu-tutorials.com/2010/01/...n-ubuntu-9-10/]("http://ubuntu-tutorials.com/2010/01/...n-ubuntu-9-10/")

And as described in this above link, everything installed properly and it's a **_newer version too_**. I was not able to test the web cam since I do not have one, but voice did work.
------------
This PC is an old Dell Inspiron 8600 Pentium M running Intrepid v. 8.10.

---

