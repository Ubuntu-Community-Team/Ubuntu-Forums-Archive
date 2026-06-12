---
title: "FFmpeg-extra / libfaac support"
date: 2010-10-20
forum: Multimedia Software
---

### Post by siren09 on 2010-10-20
Hi guys - hoping someone can help me here.  I was using the ffmpeg from the Medibuntu PPA to encode for iPod, since that comes with libfaac support.  I recently updated my distribution to Maverick, and I noticed that the ffmpeg in 10.10 is the basic one - no libfaac.  I have enabled the new Medibuntu PPA, but ffmpeg-extra and the associated codec libaries do not appear to be in the Maverick Medibuntu package listing, and hence I can't install them.  Looking at the PPA page seems to suggest they should be present.

Has anyone else had this problem, or can anyone shed light on how to fix it?

Many thanks,

siren09

---

### Post by andrew.46 on 2010-10-20
Hi siren,

Indeed, the package you are after is [libavcodec-extra-52]("http://packages.medibuntu.org/maverick/libavcodec-extra-52.html"). Perhaps run through the steps again, first add Medibuntu:

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```

Then install ffmpeg and the libavcodec package from Medibuntu:

```

sudo apt-get install ffmpeg libavcodec-extra-52

```

And this should set you up correctly...

Andrew

**Edit:** Mind you looks like you might have to manually 'Force' the Medibuntu libavcodec-extra-52 at the moment :(.

---

### Post by hemna on 2011-04-18
Doesn't work.

---

### Post by Nutria on 2011-04-18
> **siren09 said:**
> I recently updated my distribution to Maverick, and I noticed that the ffmpeg in 10.10 is the basic one - no libfaac.  I have enabled the new Medibuntu PPA, but ffmpeg-extra and the associated codec libaries do not appear to be in the Maverick Medibuntu package listing, and hence I can't install them.  Looking at the PPA page seems to suggest they should be present.

libfaac0 is in the Maverick multiverse.  Presuming that you've installed apt-file, do this:
```
$ apt-file search libfaac.
```

```
$ apt-cache policy libfaac0
libfaac0:
  Installed: 1.26-0.1ubuntu2
  Candidate: 1.26-0.1ubuntu2
  Version table:
 *** 1.26-0.1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by elmicha on 2011-04-21
"ffmpeg -acodec libfaac" seems to be an old syntax. "-acodec aac -strict experimental" works with the Natty ffmpeg.

---

### Post by FakeOutdoorsman on 2011-04-21
> **elmicha said:**
> "ffmpeg -acodec libfaac" seems to be an old syntax. "-acodec aac -strict experimental" works with the Natty ffmpeg.
It is not old syntax, but *-acodec libfaac* and *-acodec aac* are two different AAC encoders. *-acodec aac* is the native FFmpeg AAC encoder. FFmpeg from the Ubuntu repository does not have libfaac support, but Medibuntu provides the **libavcodec-extra-52** package which should enable libfaac support in FFmpeg (I haven't tested this yet in Natty). See Option C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by elmicha on 2011-04-22
Thank you for the clarification and the link to your Howto. Installing the Medibuntu repository also works for Natty now.

libavcodec-extra-52 is also in the original Natty without Medibuntu, so I thought I already had it installed.

---

