---
title: "libav developmental files conflicts"
date: 2012-11-12
forum: Multimedia Software
---

### Post by monkeybrain2012 on 2012-11-12
Hi,

I am on Ubuntu 12.10. I have added the medibuntu ppa and installed the "extra" version of libav files (libavcodecs-extra libavfilter-extra etc) but when I try to install the dev files (libavcodecs-dev, etc for compiling stuffs) synaptic insists on removing the extra versions and installs the vanilla versions instead (i.e remove libavcodecs-extra and install libavcodecs etc) 

I have never had this problem with previous releases of Ubuntu. I thought that it was a temporary post release mixed up but it has been almost a month after QQ release and it has not been fixed,does anyone know what is going on?

---

### Post by andrew.46 on 2012-11-12
You could save yourself a world of pain and build FFmpeg yourself:

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

The author of this guide lurks on these Forums as well...

---

### Post by monkeybrain2012 on 2012-11-12
deleted for double posting

---

### Post by monkeybrain2012 on 2012-11-12
> **andrew.46 said:**
> You could save yourself a world of pain and build FFmpeg yourself:

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

The author of this guide lurks on these Forums as well...

I do compile ffmpeg myself sometimes but I don't always feel like doing it, nonetheless this issue needs to be resolved.

---

### Post by mc4man on 2012-11-12
See here (the blocker is libavutil
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1038781](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1038781)

What will likely happen is this will be fix-released in 13.04 then maybe backported to 12.10

---

### Post by monkeybrain2012 on 2012-11-12
> **mc4man said:**
> See here (the blocker is libavutil
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1038781](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1038781)

What will likely happen is this will be fix-released in 13.04 then maybe backported to 12.10

Thanks for the info, so I guess I am going to install 12.04 instead. 

If what you say about fix release is true,it would be rather ridiculous that instead of fixing it for the current stable release they will fix it first for something six months down the road and "may" backport it to the current stable release. Six month down there will be other new bugs, that is  a major reason why Ubuntu doesn't go mainstream IMO. With this approach of always pushing the fixes to the next release Ubuntu would inevitable always appear somewhat buggy for users who are using the "current" release. End rant.

---

### Post by andrew.46 on 2012-11-12
By the time any fix is backported the FFmpeg in Quantal will be hopelessly outdated in terms of both features and bugfixes.

---

### Post by mc4man on 2012-11-13
> **monkeybrain2012 said:**
> Thanks for the info, so I guess I am going to install 12.04 instead. 

If what you say about fix release is true,...
After release sources only get security upgrades unless an SRU is applied for & approved.

In the case of libav security updates are fairly common so in this case they could slip in the change needed to the control file to fix this as it doesn't involve any source changes.

As it was there was a security update to libav about 11 hrs. ago but the fix was not included. (too bad I guess

So I guess in the next security update or possibly they could just upload/upgrade to fix this without an SRU, personally don't know what they have in mind
There have been instances where a bug in a release is never fixed in the release, only in the dev+ & in least one instance specific to libav
(one Ubuntu release, 11.10, the ffaudio.so plugin never was included in audacious-plugins due to some nonsense from the libav boys

---

