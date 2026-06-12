---
title: "Dependency problem on trying to compile FFmpeg"
date: 2020-07-20
forum: Multimedia Software
---

### Post by johnaaronrose on 2020-07-20
I use Bionic 64 bit desktop.
I tried following the instructions from "How to compile FFmpeg for Ubuntu" at
 [[https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu]](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu])[1]


These are:
sudo apt-get update -qq && sudo apt-get -y install \
  autoconf \
  automake \
  build-essential \
  cmake \
  git-core \
  libass-dev \
  libfreetype6-dev \
  libgnutls28-dev \
  libsdl2-dev \
  libtool \
  libva-dev \
  libvdpau-dev \
  libvorbis-dev \
  libxcb1-dev \
  libxcb-shm0-dev \
  libxcb-xfixes0-dev \
  pkg-config \
  texinfo \
  wget \
  yasm \
  zlib1g-dev


However, I get:
The following packages have unmet dependencies.
 libsdl2-dev : Depends: libsdl2-2.0-0 (= 2.0.8+dfsg1-1ubuntu1.18.04.4) but 2.0.9+dfsg1-1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

Help please!

---

### Post by &amp;KyT$0P# on 2020-07-20
Please post the output from running the following command in Terminal -
```
apt-cache policy libsdl2-dev libsdl2-2.0-0
```

---

### Post by johnaaronrose on 2020-07-20
john@JohnPC:~$ apt-cache policy libsdl2-dev libsdl2-2.0-0
libsdl2-dev:
  Installed: (none)
  Candidate: 2.0.8+dfsg1-1ubuntu1.18.04.4
  Version table:
     2.0.8+dfsg1-1ubuntu1.18.04.4 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages
     2.0.8+dfsg1-1ubuntu1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
libsdl2-2.0-0:
  Installed: 2.0.9+dfsg1-1ubuntu1
  Candidate: 2.0.9+dfsg1-1ubuntu1
  Version table:
 *** 2.0.9+dfsg1-1ubuntu1 100
        100 /var/lib/dpkg/status
     2.0.8+dfsg1-1ubuntu1.18.04.4 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages
     2.0.8+dfsg1-1ubuntu1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages

BTW Not 'quoted' as Code due to no code icon available on Quick Reply

---

### Post by &amp;KyT$0P# on 2020-07-20
Thanks.  Now could you please post the output from running this command? -
```
apt-get -s install libsdl2-2.0-0/bionic
```

> **johnaaronrose said:**
> BTW Not 'quoted' as Code due to no code icon available on Quick Reply

You could also just type [FONT=Courier New][noparse]```
[/noparse][/FONT] at the beginning and [FONT=Courier New][noparse]
```[/noparse][/FONT] at the end.

---

### Post by johnaaronrose on 2020-07-20
Seems to have installed. Thanks.
```

john@JohnPC:~$ sudo apt-get -s install libsdl2-2.0-0/bionic[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '2.0.8+dfsg1-1ubuntu1.18.04.4' (Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64]) for 'libsdl2-2.0-0'
The following packages were automatically installed and are no longer required:
  libsndio6.1:i386 libwayland-client0:i386 libwayland-cursor0:i386 libwayland-egl1:i386 libx11-6:i386
  libxcursor1:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386 libxrandr2:i386
  libxrender1:i386 libxss1:i386 libxxf86vm1:i386
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  libsdl2-2.0-0:i386
The following packages will be DOWNGRADED:
  libsdl2-2.0-0
0 to upgrade, 0 to newly install, 1 to downgrade, 1 to remove and 0 not to upgrade.
Remv libsdl2-2.0-0:i386 [2.0.9+dfsg1-1ubuntu1]
Inst libsdl2-2.0-0 [2.0.9+dfsg1-1ubuntu1] (2.0.8+dfsg1-1ubuntu1.18.04.4 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])
Conf libsdl2-2.0-0 (2.0.8+dfsg1-1ubuntu1.18.04.4 Ubuntu:18.04/bionic-updates, Ubuntu:18.04/bionic-security [amd64])

```

However, redoing original install attempt gives problem:
```

john@JohnPC:~$ sudo apt-get update -qq && sudo apt-get -y install \
> autoconf \
> automake \
> build-essential \
> cmake \
> git-core \
> libass-dev \
> libfreetype6-dev \
> libgnutls28-dev \
> libsdl2-dev \
> libtool \
> libva-dev \
> libvdpau-dev \
> libvorbis-dev \
> libxcb1-dev \
> libxcb-shm0-dev \
> libxcb-xfixes0-dev \
> pkg-config \
> texinfo \
> wget \
> yasm \
> zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'git' instead of 'git-core'
autoconf is already the newest version (2.69-11).
autoconf set to manually installed.
automake is already the newest version (1:1.15.1-3ubuntu2).
automake set to manually installed.
build-essential is already the newest version (12.4ubuntu1).
build-essential set to manually installed.
libfreetype6-dev is already the newest version (2.8.1-2ubuntu2).
libfreetype6-dev set to manually installed.
libtool is already the newest version (2.4.6-2).
pkg-config is already the newest version (0.29.1-0ubuntu2).
pkg-config set to manually installed.
zlib1g-dev is already the newest version (1:1.2.11.dfsg-0ubuntu2).
zlib1g-dev set to manually installed.
texinfo is already the newest version (6.5.0.dfsg.1-2).
texinfo set to manually installed.
cmake is already the newest version (3.10.2-1ubuntu2.18.04.1).
git is already the newest version (1:2.17.1-1ubuntu0.7).
libxcb-shm0-dev is already the newest version (1.13-2~ubuntu18.04).
libxcb-shm0-dev set to manually installed.
libxcb1-dev is already the newest version (1.13-2~ubuntu18.04).
libxcb1-dev set to manually installed.
wget is already the newest version (1.19.4-1ubuntu2.2).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libsdl2-dev : Depends: libsdl2-2.0-0 (= 2.0.8+dfsg1-1ubuntu1.18.04.4) but 2.0.9+dfsg1-1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by &amp;KyT$0P# on 2020-07-20
> **johnaaronrose said:**
> However, redoing original install attempt gives problem:

Yeah, it would.  That command was just a simulation.  I want to check for side effects before suggesting actually going ahead.

Why do you have the 32-bit version of that library installed?

If you really need the 32-bit version, please post the output of running this command in Terminal -
```
apt-get -s install libsdl2-2.0-0:i386/bionic libsdl2-2.0-0/bionic
```

---

### Post by johnaaronrose on 2020-07-20
I have no idea why the 32-bit version of libsdl2 is installed. My PC's Ubuntu 18.04 64 bit was a clean install on an 8GB Intel Celeron barebones computer approx in September 2018.
What now?

---

### Post by SeijiSensei on 2020-07-20
I've compiled ffmpeg in the past and found the standard

```
sudo apt-get build-dep ffmpeg
```

brought in all the source dependencies I needed.

---

### Post by &amp;KyT$0P# on 2020-07-20
> **johnaaronrose said:**
> I have no idea why the 32-bit version of libsdl2 is installed. 

Ok, then try -
```
sudo apt-get install libsdl2-2.0-0/bionic
```
... and let it remove the 32-bit version of libsdl2, as the simulation said would happen. (If it turns out you do need it, you should be able to reinstall it later.)

Then retry the install of ffmpeg build dependencies.  Does it now work?

---

### Post by johnaaronrose on 2020-07-20
> **SeijiSensei said:**
> I've compiled ffmpeg in the past and found the standard

```
sudo apt-get build-dep ffmpeg
```

brought in all the source dependencies I needed.

Above command failed:
```

john@JohnPC:~$ sudo apt-get build-dep ffmpeg
[sudo] password for john: 
Reading package lists... Done
E: You must put some 'source' URIs in your sources.list

```

---

### Post by johnaaronrose on 2020-07-20
> **halogen2 said:**
> Ok, then try -
```
sudo apt-get install libsdl2-2.0-0/bionic
```
... and let it remove the 32-bit version of libsdl2, as the simulation said would happen. (If it turns out you do need it, you should be able to reinstall it later.)

Then retry the install of ffmpeg build dependencies.  Does it now work?

Now works. Thanks.

---

### Post by &amp;KyT$0P# on 2020-07-20
You're welcome. :KS

---

### Post by SeijiSensei on 2020-07-21
> **johnaaronrose said:**
> Above command failed:
```

john@JohnPC:~$ sudo apt-get build-dep ffmpeg
[sudo] password for john: 
Reading package lists... Done
E: You must put some 'source' URIs in your sources.list

```


That means the entries beginning with "deb-src" are commented out in /etc/apt/sources.list.

---

