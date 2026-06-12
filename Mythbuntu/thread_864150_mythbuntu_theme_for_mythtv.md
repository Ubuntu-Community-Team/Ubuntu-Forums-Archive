---
title: "mythbuntu theme for mythtv"
date: 2008-07-19
forum: Mythbuntu
---

### Post by graysky on 2008-07-19
Anyone know where I can download the mythbuntu theme for use with an existing mythtv box?

---

### Post by superm1 on 2008-07-19
> **graysky said:**
> Anyone know where I can download the mythbuntu theme for use with an existing mythtv box?
[https://code.edge.launchpad.net/~mythbuntu/mythbuntu/mythtv-theme-mythbuntu](https://code.edge.launchpad.net/~mythbuntu/mythbuntu/mythtv-theme-mythbuntu)

---

### Post by superm1 on 2008-07-19
Or better yet (so you dont get trunk cruft):
[http://packages.ubuntu.com/hardy/mythtv-theme-mythbuntu](http://packages.ubuntu.com/hardy/mythtv-theme-mythbuntu)

---

### Post by graysky on 2008-07-19
Thanks man, I was able to get that deb and I used ```
# ar -x <name>.deb
``` to get the files out.  I manually placed them in /usr/share/mythtv/themes and was able to load the 8.04 theme into my mythfrontend.  The screen went black and I was back at the x desktop.  I got a number of missing file errors when I launched it from the console.  Is it a permission's problem?

---

### Post by nickrout on 2008-07-19
is there some reason why you didn't install it the normal way?

apt-get install mythtv-theme-mythbuntu

---

### Post by graysky on 2008-07-19
> **nickrout said:**
> is there some reason why you didn't install it the normal way?

apt-get install mythtv-theme-mythbuntu

Couldn't find package. I did an apt-get update prior to the install:

```
# apt-get install mythtv-theme-mythbuntu
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mythtv-theme-mythbuntu
```

What do I need to add to my /etc/apt/sources.list to see it?

Forgot to mention, I'm using [R5.5 of Knoppmyth](http://knoppmyth.net/) which is based on the debian unstable, so I don't wanna roach my system in the process :)

Here's my /etc/apt/sources.list:```
#Debian repos
deb http://ftp.debian.org unstable main contrib non-free
deb-src http://ftp.debian.org stable main contrib non-free

#For libnet-upnp
deb http://debian.slimdevices.com unstable main

#For FreeNX
#deb http://packages.debianbase.de/testing/i386/nx/ ./

#For xorg-edit
#deb http://debian.geole.info/ sid main contrib non-free

#For additional multimedia packages
deb http://www.debian-multimedia.org sid main
deb-src http://www.debian-multimedia.org sid main
#deb http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia unstable main
#deb-src http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia stable main
```

---

### Post by nickrout on 2008-07-19
It would have been helpful to say that first. Of course the mythbuntu theme is not going to be in the debian repos.

I would suggest to download the deb file and install it with dpkg.

---

### Post by superm1 on 2008-07-19
Its also dependent upon the project grayhem themes.  You need to install those first for it to work.

---

### Post by graysky on 2008-07-19
Thanks for the info, guys.

---

