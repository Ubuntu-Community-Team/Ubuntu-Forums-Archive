---
title: "NVidia problems (libglu1-mesa)"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by Grant McConville on 2006-08-07
Hey all,

I am trying to get the NVidia drivers working for my GeForce FX6600. When I type in 'sudo apt-get install nvidia-glx' it comes up with errors such as

The following packages have unmet dependencies:
  nvidia-glx: Depends: libglu1-mesa but it is not going to be installed or
                       libglu1

If I type 'sudo apt-get install libglu1-mesa' it says that it has already installed it.

I have gone through the Ubuntu guide on how to do it but can't seem to overcome this. My experience level is about 20%.

Any ideas?
Grant

---

### Post by tseliot on 2006-08-07
1) Which version of Ubuntu do you use (dapper, edgy, breezy, etc.)?

2) can you post the content of your /etc/apt/sources.list ?

---

### Post by Grant McConville on 2006-08-07
I got it working, I found another guide on how to do it and it is working great.

Thanks
Grant

---

### Post by tseliot on 2006-08-07
> **Grant McConville said:**
> I got it working, I found another guide on how to do it and it is working great.

Thanks
Grant

For any other doubt you can use my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

