---
title: "Problem installing MPEG4IP"
date: 2008-06-25
forum: Multimedia Software
---

### Post by frankki on 2008-06-25
Hi

For my work, I have to use this software, but when I'm trying to install it, I have this error :
```
./bootstrap
....
Mp4live encoder report:
 *** ffmpeg encoder is not installed
 *** xvid encoder is not installed
 *** x264 encoder is not installed
 *** lame encoder is not installed
 *** faac encoder is not installed
 ready to make

```
I tried installing the different packages by hand but without success. Can anyone help me about this? (or telling me about another way to encode an avi video into an uncompressed yuv video....)

Thanks
Frankki

---

### Post by cenze on 2009-03-18
Hi!

I know this is an old thread, but I'm having the same problem trying to get mpeg4ip going on Debian.

Did you, by chance, ever get beyond this issue?

Thanks,
Cenze

---

### Post by mactfines on 2010-04-23
I am not using Ubuntu, but CentOS.  Still, I ran into and found a solution to this same dependency problem so I think it might help you.

Installation of lame-devel and ffpmeg-devel was the
solution to the following errors:
*** ffmpeg encoder is not installed
*** xvid encoder is not installed
*** x264 encoder is not installed
*** lame encoder is not installed
*** faac encoder is not installed

Other dependency problems / packages that fixed them:
esd-config is provided by the "esound-devel" package

gtk2-devel fixes the "You do not have GTK libraries installed; there will be no mp4live gui" warning

Once I got all those installed, the warnings disappeared and I was able to make/make install.

Hope this helps,
Ted

---

