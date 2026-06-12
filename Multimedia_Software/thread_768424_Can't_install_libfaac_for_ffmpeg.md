---
title: "Can't install libfaac for ffmpeg"
date: 2008-04-26
forum: Multimedia Software
---

### Post by aaronvegh on 2008-04-26
Hi there,
I'm trying to get libfaac working with ffmpeg, but having no luck! In multiple places I've found that I should use this command, but here's the result:

$ sudo apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package quilt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package quilt has no installation candidate
E: Failed to satisfy Build-Depends dependency for ffmpeg: quilt

I have universe and multiverse enabled on my feisty installation. Can anyone suggest a solution?

Thanks,
Aaron.

---

### Post by omicrondelta on 2008-04-26
Download the source... Don't be too reliant on packages... Or GCC... lmao...

---

### Post by mc4man on 2008-04-26
Quilt is from main repo, ck. if it's enabled 
```
Get:7 http://us.archive.ubuntu.com feisty/main quilt 0.45-6
```
or [http://packages.ubuntu.com/feisty/quilt](http://packages.ubuntu.com/feisty/quilt)    - ck. depends

---

### Post by aaronvegh on 2008-04-26
Got it to work! I added these lines to my /etc/apt/sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main

Not sure why main wasn't enabled before...?

---

