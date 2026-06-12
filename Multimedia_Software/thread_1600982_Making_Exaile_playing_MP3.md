---
title: "Making Exaile playing MP3"
date: 2010-10-19
forum: Multimedia Software
---

### Post by LHXS on 2010-10-19
Hi folks,
I've just changed from Windows 7 to Ubuntu 10.04 LTS - so I'm a newbie to Ubuntu.

I'm trying to set up an MP3 player. Following some discussion in this form
[http://ubuntuforums.org/showthread.php?t=624716](http://ubuntuforums.org/showthread.php?t=624716)
I've chosen to install "Exaile". The version I have is 0.3.1.1. I've got it installed using the Synaptic Package Manager.
However, I still cannot play any MP3 with Exaile. Instead I get the following (and very useless) message

"You do not have a decoder installed to handle this file. You might need to install the necessary plugin."

It is not saying which decoder I have to install. Neither does it tell what plugin is needed. Honestly, this is not helpful at all.

I've made Google search and found
[https://bugs.launchpad.net/exaile/+bug/500320](https://bugs.launchpad.net/exaile/+bug/500320)
[http://www.debianadmin.com/install-exaile-media-player-and-enjoy-your-music-in-ubuntu.html](http://www.debianadmin.com/install-exaile-media-player-and-enjoy-your-music-in-ubuntu.html)

But I haven't found anything towards the version 0.3.1.1 of Exaile.
If someone could give me a step by step installation description that would be fantastic!

Thanks,
LHXS

---

### Post by Lazaruss on 2010-10-19
```
sudo apt-get install ubuntu-restricted-extras
```

should install the multimedia codecs for you

---

### Post by LHXS on 2010-10-19
> **Lazaruss said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```should install the multimedia codecs for you

Thanks a lot! It's working. After typing your suggestion 165MB of plugins were downloaded and installed. For other newbies (quoting from Wikipedia):
ubuntu-restricted-extras is a software package for the computer operating system Ubuntu 
 that allows the user to install essential software which is not already included due to legal or copyright reasons.

---

### Post by 1remus on 2010-11-24
would someone who has xubuntu do the same?

---

### Post by Elfy on 2010-11-24
> **1remus said:**
> would someone who has xubuntu do the same?

Almost ... 

```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by Lazaruss on 2010-11-24
and of course for kubuntu:
```
sudo apt-get install kubuntu-restricted-extras
```

---

