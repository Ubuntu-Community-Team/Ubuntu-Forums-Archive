---
title: "HOWTO play real audio with mplayer in Ubuntu Hardy"
date: 2008-05-30
forum: Multimedia Software
---

### Post by jupiter2006 on 2008-05-30
You need to install w32codecs which are not in the default repositories due to legal restrictions.

Follow the instruction in:
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html")

Summary of the steps from the link above, assuming you already have mplayer installed:
NOTE: The following instructions also install libdvdcss2. Remove it from the apt-get command if you don't need it.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get install medibuntu-keyring

sudo apt-get update

```

For i386 users:
```

sudo apt-get install w32codecs libdvdcss2

```

Fot amd64 users:
```

sudo apt-get install w64codecs libdvdcss2

```

---

