---
title: "New install Ubuntu 8.10 ffmpeg error"
date: 2010-02-15
forum: Multimedia Software
---

### Post by coolercooler on 2010-02-15
Hi all.

I've just upgraded from 8.04 to 8.10, and when I tried to compile ffmpeg, I got this error.

```
# apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for ffmpeg could not be satisfied.

```

Whats wrong, and how can I fix this?

Thanks

---

### Post by FakeOutdoorsman on 2010-02-15
I recommend this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

I attempt to keep it up-to-date and there are versions of the guide for five various Ubuntu releases.

---

### Post by coolercooler on 2010-02-15
Thanks thats a brill guide.

However that gave further problems.

```
 # apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libsdl1.2-dev libx11-dev libxfixes-dev libxvidcore4-dev zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
  libx11-dev: Depends: libx11-6 (= 2:1.1.5-2ubuntu1) but 2:1.1.5-2ubuntu1.1 is to be installed
E: Broken packages

```

---

### Post by coolercooler on 2010-02-16
To solve some of the above errors I have to do this.

```
aptitude purge build-essential
aptitude install libc6-dev
aptitude update && aptitude install build-essential
Gave the above commands it then asked to downgrade packgaes, chose (Y)  
```

But now I get these errors.

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libpng12-dev: Depends: libpng12-0 (= 1.2.27-1) but 1.2.27-1ubuntu0.1 is to be installed
  libvorbis-dev: Depends: libvorbis0a (= 1.2.0.dfsg-3.1) but 1.2.0.dfsg-3.1ubuntu0.8.10.2 is to be installed
                 Depends: libvorbisenc2 (= 1.2.0.dfsg-3.1) but 1.2.0.dfsg-3.1ubuntu0.8.10.2 is to be installed
                 Depends: libvorbisfile3 (= 1.2.0.dfsg-3.1) but 1.2.0.dfsg-3.1ubuntu0.8.10.2 is to be installed
E: Broken packages
 
```

If I try to install any of the packages, with apt-get.
```
  apt-get install libpng12-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpng12-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded
```

Ubuntu 8.10 with 2.6.27.7-generic.

---

### Post by mc4man on 2010-02-16
The 2 -dev packages (libpng12-dev, libvorbis-dev) are showing intrepid versions available but the dependencies are intrepid-update versions

Why don't you go to System -> Admin -> software sources and under the update tab make sure the first 2 are enabled (security and recommended

If you have to enable one and or the other then click close and reload and try your installl again or run this

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by coolercooler on 2010-02-16
Thanks thats worked, I had disabled those as I didn't wanted to update headers, am using patched drivers for some of my hardware, but if updated the header it makes them stop working with patches.

But that also stop other updates.

---

