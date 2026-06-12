---
title: "Need demuxer plugin for xine"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by _Herb_ on 2007-06-01
Just installed Xubuntu Feisty and tried to watch a movie on DVD with gxine (libdvdcss2 is installed). This is the resulting error message:

  The xine engine failed to start.
  No demuxer found - stream format not recognized.

Anyone know which plugin is needed, where it can be found and how to install it?

I don't see anything like this with Synaptic and can't figure it out from the help files or forums.

Thanks.

---

### Post by espresso on 2007-06-03
Hey there,

I've had this problem too. I fixed it by installing the following in the Synaptic Package Manager: -

libxine1-ffmpeg

Further details about this bug can be found here: -

[https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/83083](https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/83083)

Hope this has helped you,

espresso.

---

### Post by _Herb_ on 2007-06-03
The library libxine1-ffmpeg doesn't show up for me in Synaptic. Suggestions?

---

### Post by espresso on 2007-06-03
Try typing the following in the terminal: -

```
sudo apt-get install libxine1-ffmpeg
```


espresso.

---

### Post by _Herb_ on 2007-06-04
Thanks for the suggestion. Here's the result:

```
$ sudo apt-get install libxine1-ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine1-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine1-ffmpeg has no installation candidate

```

This seems to agree with the Synaptic result, that is, the library can't be found.

---

### Post by espresso on 2007-06-05
Ok, it sounds like you may need to enable more repositories. Try using the instructions on the following page: -

[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

Hope this helps!

espresso.

---

### Post by _Herb_ on 2007-06-05
Many thanks for the pointer, the problem is FIXED.

I changed from the US to MAIN repositories in Synaptic, updated and the missing libxinel1-ffmpeg then appeared in the package list. Installed it and now DVDs play in gxine.

Great!

---

### Post by espresso on 2007-06-07
Great to hear the problems fixed and you can now view DVDs.

espresso.

---

### Post by Don Keeton on 2007-06-10
espresso: Hey thanks for the help - I had the exact same problem and it fixed the issue.

---

### Post by motoperpetuo on 2007-06-20
> **espresso said:**
> Hey there,

I've had this problem too. I fixed it by installing the following in the Synaptic Package Manager: -

libxine1-ffmpeg

Further details about this bug can be found here: -

[https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/83083](https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/83083)

Hope this has helped you,

espresso.


I'm a Windows guy, trying to move to Ubuntu. After about a day of banging my head against the wall trying to get a DVD to play in Ubuntu, getting libxine1-ffmpeg proved to be the last piece of the puzzle. Thanks very, very much. My condolences to anyone else who's struggling with this. You might try the instructions at:

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

I used these to get libdvdcss2 and the w32codecs installed, which I think was the other piece of the puzzle I needed.

Anyway, thanks very much for the help.

---

