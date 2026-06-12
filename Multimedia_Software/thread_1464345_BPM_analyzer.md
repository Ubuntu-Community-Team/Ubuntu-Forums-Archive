---
title: "BPM analyzer"
date: 2010-04-28
forum: Multimedia Software
---

### Post by prconnor@gmail.com on 2010-04-28
Hello,

I would like to include BPM data in all my id3 headers.  I can do this one song at a time with banshee, but I have lots of songs, and it would take a very long time.

In [this]("http://getsatisfaction.com/songbird/topics/integrated_bpm_counter") thread I read about bmpdj and I am attempting to install this from source.

I run into problems with the make command which gives me:

```
Link targets:
User Interface Resources:
  [uic] ui-about.h
  [uic] ui-album.h
  [uic] ui-beatgraph.h
  [uic] ui-bpmcounter.h
  [uic] ui-bpmdj-pref.h
  [uic] ui-bpmmerge.h
  [uic] ui-capacity.h
  [uic] ui-clustering.h
  [uic] ui-freq-mapping.h
  [uic] ui-importing.h
  [uic] ui-installremotes.h
  [uic] ui-loader.h
  [uic] ui-logs.h
  [uic] ui-metrics.h
  [uic] ui-mixerdialog.h
  [uic] ui-player.h
  [uic] ui-renamerstart.h
  [uic] ui-renamer.h
'GroupBox1' isn't a valid widget
  [uic] ui-rhythm.h
  [uic] ui-selector.h
  [uic] ui-setupwizard.h
  [uic] ui-song-information.h
  [uic] ui-spectrum.h
  [uic] ui-stats.h
Resource files:
  [rcc] rc-player.cpp
Source Files:
make[1]: *** No rule to make target `profile-clock.o', needed by `profile-clock'.  Stop.
make: *** [.source-creator] Error 2

```

I don't know what profile-clock.o is, or what package provides it.

Thank you for any help

Phil

---

### Post by QwUo173Hy on 2010-09-16
The developers of that project have left contact details on their webpage: [http://bpmdj.yellowcouch.org/aftersplash.html](http://bpmdj.yellowcouch.org/aftersplash.html)

I would try contacting them.

---

### Post by kat_ams on 2011-08-12
BpmDj is actually really easy to install under Ubuntu.

Just download the bpmdj-4.2.pl2-0.x86_64.rpm
from the site
(this is the 64bit package, there is also a 32 bit one available ending in i586)
```

ftp://bpmdj.yellowcouch.org/bpmdj/

```
then use alien to covert it to a deb
```

sudo alien -k bpmdj-4.2.pl2-0.x86_64.rpm

```
then install it with dpkg
```

sudo dpkg -i bpmdj-4.2.pl2-0.x86_64.deb

```

---

