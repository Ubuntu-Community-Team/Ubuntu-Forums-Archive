---
title: "cinelerra bug"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by defenestratos on 2008-04-13
I can't install cinelerra. Should I file a bug report with the readout below? I have never filed one before.

hugo@hugo-laptop:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libasound2 (> 1.0.14) but 1.0.10-2ubuntu4 is to be install ed
             Depends: libavc1394-0 (>= 0.5.3) but 0.5.1-1 is to be installed
             Depends: libc6 (>= 2.7-1) but 2.3.6-0ubuntu20.5 is to be installed
             Depends: libfreetype6 (>= 2.3.5) but 2.1.10-1ubuntu2.4 is to be ins talled
             Depends: libgcc1 (>= 1:4.2.1) but 1:4.0.3-1ubuntu5 is to be install ed
             Depends: libguicast (>= 1:2.1.0) but it is not going to be installe d
             Depends: liblame0 (>= 3.97) but it is not installable
             Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libmpeg3hv (>= 1:2.1.0) but it is not going to be installe d
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.3 is to be installed
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be inst alled
             Depends: libstdc++6 (>= 4.2.1) but 4.0.3-1ubuntu5 is to be installe d
             Depends: libvorbis0a (>= 1.2.0) but 1.1.2-0ubuntu2.2 is to be insta lled
             Depends: libvorbisfile3 (>= 1.2.0) but 1.1.2-0ubuntu2.2 is to be in stalled
             Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-6ubuntu4 is to be  installed
             Depends: libguicast (= 1:2.1.0-2svn20080304) but it is not going to  be installed
             Depends: libquicktimehv (= 1:2.1.0-2svn20080304) but it is not goin g to be installed
             Depends: libmpeg3hv (= 1:2.1.0-2svn20080304) but it is not going to  be installed
E: Broken packages

---

### Post by pops66 on 2008-04-14
Try to install with aptitude.
```
sudo aptitude
```

you use '/' to search, '+' to select and 'g' to apply changes
it will let you know about all kinds of dependency issue right away and may give you a solution.

Otherwise try to install each of those packages that you have listed above individually and then install cinerrela and see what happens.

---

