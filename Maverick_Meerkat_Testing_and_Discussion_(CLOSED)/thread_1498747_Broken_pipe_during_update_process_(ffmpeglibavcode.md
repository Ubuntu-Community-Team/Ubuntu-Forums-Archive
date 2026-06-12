---
title: "Broken pipe during update process (ffmpeg/libavcodec-extra-52)"
date: 2010-06-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rubenverweij on 2010-06-01
The first breakage has already come for me. :P
Today I tried to update my maverick (sudo apt-get update && sudo apt-get safe-upgrade) but the update process didn't finish and I got the following error:
```

Unpacking replacement ffmpeg ...
dpkg: error processing /var/cache/apt/archives/ffmpeg_4%3a0.6~svn20100505-1ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/ffmpeg/libx264-baseline.ffpreset', which is also in package libavcodec-extra-52 4:0.5.1-1ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_4%3a0.6~svn20100505-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libavdevice52:
 libavdevice52 depends on libavcodec52 (>= 4:0.6~svn20100505-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6~svn20100505-1ubuntu1); however:
  Package libavcodec52 is not installed.
  Version of libavcodec-extra-52 on system is 4:0.5.1-1ubuntu1.
dpkg: error processing libavdevice52 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavformat52:
 libavformat52 depends on libavcodec52 (>= 4:0.6~svn20100505-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6~svn20100505-1ubuntu1); however:
  Package libavcodec52 is not installed.
  Version of libavcodec-extra-52 on system is 4:0.5.1-1ubuntu1.
dpkg: error processing libavformat52 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libavdevice52
 libavformat52

```
When trying to install libavcodec52:
```
The following packages have unmet dependencies:
  ffmpeg: Depends: libavdevice52 (< 4:0.5.1-99) but 4:0.6~svn20100505-1ubuntu1 is to be installed or
                   libavdevice-extra-52 (< 4:0.5.1-99) but it is not going to be installed
          Depends: libavformat52 (< 4:0.5.1-99) but 4:0.6~svn20100505-1ubuntu1 is to be installed or
                   libavformat-extra-52 (< 4:0.5.1-99) but it is not going to be installed
  libavcodec-extra-52: Conflicts: libavcodec52 but 4:0.6~svn20100505-1ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
So I tried apt-get -f install, but this just gives me the broken pipe error again I got before. Is anyone experiencing this too and does anyone has an idea how to fix this or whether this should be reported? Or should I just wait for alpha1 whether it's smoothed out by then? :P
Thanks!

---

### Post by dino99 on 2010-06-01
this issue have been discussed here a few days ago here, dont upgrade these packages as they brake video, need some more packages to be built

---

### Post by rubenverweij on 2010-06-02
Ok, thanks, then I guess I´ll just wait for the fix then.

---

### Post by rubenverweij on 2010-06-03
Great, the updates solved it now. I also have the patch for metacity now, so everything rocks again! :popcorn:

---

### Post by mdurham on 2010-06-03
> **rubenverweij said:**
> Great, the updates solved it now. I also have the patch for metacity now, so everything rocks again! :popcorn:
Didn't fix it for me, I still get:
> E: /var/cache/apt/archives/ffmpeg_4%3a0.6~svn20100505-1ubuntu1_i386.deb: trying to overwrite '/usr/share/ffmpeg/libx264-baseline.ffpreset', which is also in package libavcodec-extra-52 4

Any ideas?
Cheers, Mike

---

### Post by rubenverweij on 2010-06-04
Are you using the main repositories? Maybe you have to wait for your mirror to settle. Otherwise, I don't know, I just waited myself.

---

### Post by luceerose on 2010-06-04
Don't know if this is off-topic or of any consequence, but I had exactly the same breakage on Debian. It fixed itself when I added the sid & experimental repos & did an update.

---

### Post by mdurham on 2010-06-04
> **rubenverweij said:**
> Are you using the main repositories? Maybe you have to wait for your mirror to settle. Otherwise, I don't know, I just waited myself.
Thanks for replying, I am using the main repos. Strange isn't it?

---

