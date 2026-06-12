---
title: "DeVeDe vs. k9copy dependency hell in 16.04"
date: 2016-05-09
forum: Multimedia Software
---

### Post by cbraxton on 2016-05-09
I just performed a fresh install of Ubuntu Mate 16.04 and am trying to restore some of the lost functionality that earlier versions had in dealing with DVDs. The programs I primarily use are k9copy to backup DVD discs, and DeVeDe or DVD Styler to create DVDs.

The original developer of k9copy stopped development some time ago, but the program has been picked up by others and is now "k9copy-reloaded." I found a ppa for it that seems to work:

  [https://launchpad.net/~tomtomtom/+archive/ubuntu/k9copy](https://launchpad.net/~tomtomtom/+archive/ubuntu/k9copy)

However, when k9copy is installed, the package "libavcodec-ffmpeg-extra56" is uninstalled and "libavcodec-ffmpeg56" is installed in its place. (I assume this means there will be fewer codecs available to ffmpeg.)

DeVeDe is in the standard Ubuntu repositories. However, if an attempt is made to install that, Synaptic (or apt-get) wants to remove libavcodec-ffmpeg56 that was pulled in by k9copy and replace it with libavcodec-ffmpeg-extra56. If this is done k9copy will also be removed.

```

# apt-get install devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libavcodec-extra libavcodec-ffmpeg-extra56
Suggested packages:
  mencoder
The following packages will be REMOVED:
  k9copy libavcodec-ffmpeg56
The following NEW packages will be installed:
  devede libavcodec-extra libavcodec-ffmpeg-extra56
0 upgraded, 3 newly installed, 2 to remove and 12 not upgraded.
Need to get 5,509 kB of archives.
After this operation, 1,009 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

Is there any way to resolve this such that both k9copy and DeVeDe can coexist and the extra codecs will be available? (Seems like it should be possible for k9copy to work with the "extras" codec package if that is a superset of the standard package. But it insists on having the less functional codec package installed. :confused:)

I have not found a place yet to obtain DVD Styler binaries compatible with 16.04.  I did find and install the Bombono DVD authoring program but am not familiar with it and don't know yet how it will work out.

---

### Post by tomtom1982 on 2016-05-10
Until I can fix the dependencies and the new files will be in the launchpad repo you can try this workaround:

Download the package
```

wget https://launchpad.net/~tomtomtom/+archive/ubuntu/k9copy/+files/k9copy_3.0.3-6~ppa~xenial_amd64.deb

```
make a directory for the changes
```

mkdir -p k9copy/DEBIAN

```
extract the control file
```

dpkg -e k9copy_3.0.3-6~ppa~xenial_amd64.deb k9copy/DEBIAN

```
extract the content of the package
```

dpkg -x  k9copy_3.0.3-6~ppa~xenial_amd64.deb k9copy/

```
change the dependency in control file
```

sed -i s/libavcodec-ffmpeg56/"libavcodec-ffmpeg56 | libavcodec-ffmpeg-extra56"/g k9copy/DEBIAN/control

```
the packages hast to be rebuild
```

dpkg -b ./k9copy k9copy_3.0.3-6~ppa~xenial_amd64.deb

```
At last the new package can be installed with
```

sudo dpkg -i k9copy_3.0.3-6~ppa~xenial_amd64.deb

```
If you are using a 32 bit system change amd64 in this HowTo to i386.

---

### Post by Bucky Ball on 2016-05-10
*Thread moved to **Multimedia Software**. *

---

### Post by cbraxton on 2016-05-10
> **tomtom1982 said:**
> Until I can fix the dependencies and the new files will be in the launchpad repo you can try this workaround: ...

Great, thanks!

I just applied the workaround and it worked just fine, I now have k9copy installed along with devede and the extra codecs. (Now I'll have to see if I can find a way to run dvdstyler...)

---

### Post by mc4man on 2016-05-10
> **cbraxton said:**
> (Now I'll have to see if I can find a way to run dvdstyler...)
[wxsvg was removed from debian/ubuntu]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=813151") as nothing in their repos depended on.

---

### Post by tomtom1982 on 2016-05-10
I dputted the new version to canonical build servers.

When

```

apt-cache show k9copy

```

shows the version 

3.0.3-7~ppa~xenial

the package with the corrected dependency will be available in the repo.

---

### Post by cbraxton on 2016-05-12
Hi, just wanted to let you know it looks like there's a typographical error in the dependency for the "extras" library.

```

# apt-get install k9copy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 k9copy : Depends: libavcodec-ffmpeg56 but it is not going to be installed or
                   livavcodec-ffmpeg-extra56 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

The package is looking for "li**v**avcodec..." when it should be "li**b**avcodec..." Took me a while to see it!

---

### Post by tomtom1982 on 2016-05-12
grml

Fixed in 3.0.3-8. Thanks for feedback.

---

### Post by cbraxton on 2016-05-12
> **tomtom1982 said:**
> grml

Fixed in 3.0.3-8. Thanks for feedback.

Thank you for your efforts in making k9copy available! I've made that kind of mistake many times myself, it's all too easy. It was driving me nuts until I took a real close look at the error message from apt-get.

I've gone ahead and installed the latest revision from your PPA and it works just fine. :D

---

### Post by alan64 on 2016-08-26
This conflict between Devede and K9copy also existed in Ubuntu 15.10.

In any case, I am running Ubuntu 16.04 now, and haven't tried to install Devede yet, but K9copy works beautifully. It now copies all audio tracks by default, so you don't have to go through and click on each one beforehand.  Thank you, thank you, Tomtomtom!

---

