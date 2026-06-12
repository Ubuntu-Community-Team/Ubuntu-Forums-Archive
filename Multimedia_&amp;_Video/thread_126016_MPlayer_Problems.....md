---
title: "MPlayer Problems...."
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by steve k on 2006-02-05
Hey,

I've been trying to install Mplayer for most of the afternoon...

although it should be as simple as 'apt-get install mplayer' that just doesn't seem to work:

take a look at the errors I'm getting from apt.

```
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-586: Depends: libartsc0 (>= 1.5.0-1) but 1.4.3-0ubuntu1 is to be installed
               Depends: libasound2 (> 1.0.10) but 1.0.9-2 is to be installed
               Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1 is to be installed
               Depends: libfribidi0 (>= 0.10.7-1) but 0.10.5-2 is to be installed
               Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
               Depends: libglib2.0-0 (>= 2.8.5) but 2.8.3-0ubuntu1 is to be installed
               Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: libpango1.0-0 (>= 1.10.2) but 1.10.1-0ubuntu1 is to be installed
               Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
               Depends: libxrender1 (>= 1:0.9.0.2) but 1:0.9.0-1 is to be installed
E: Broken packages

```

Any ideas why?  

It seems like Mplayer works just fine for lots of people on here.  Should I try compiling it from source or something?

---

### Post by BitTorrentBuddha on 2006-02-05
try installing the package dependencies that it listed
```
sudo apt-get <missing package (i.e. libartsc0)]
```
this is just a guess though

---

### Post by steve k on 2006-02-05
See,
the problems is that apt would normally download the dependencies needed as a matter of course, however, since these guys AREN'T going to be installed (because other ubuntu versions ARE going to be installed) Mencoder doesn't want to appear?  

```
Depends: libartsc0 (>= 1.5.0-1) but 1.4.3-0ubuntu1 is to be installed
```

---

