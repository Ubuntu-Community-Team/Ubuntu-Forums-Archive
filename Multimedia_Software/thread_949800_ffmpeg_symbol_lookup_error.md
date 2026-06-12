---
title: "ffmpeg: symbol lookup error"
date: 2008-10-16
forum: Multimedia Software
---

### Post by JoaoCarlosCorreia on 2008-10-16
Hi everybody, 
I was trying to compile ffmpeg with libx264 enabled and when it finished I get this error everytime I try to use ffmpeg:

"ffmpeg:symbol lookup error: /usr/local/lib/libavcodec.so.51: undefined symbol: av_crc04C11DB7"

Do you know what is happening?
How can I solve this?


thansk for any help,

João Correia

---

### Post by cor2y on 2008-10-16
was this a svn build of ffmpeg?
If yes then the solution could be to completely remove the repo version of libx264 and libx264-dev and compile those from the git repo or daily tar ball on the videolan site
[http://www.videolan.org/developers/x264.html](http://www.videolan.org/developers/x264.html)
See if that works, i recommend this guide for ffmpeg and x264 compiling from source
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If you still get the error after this then i would recommend you unistall the compiled ffmpeg and libx264 , add the medibuntu repos and install both libx264 and ffmpeg from there, ffmpeg is compiled with most of the codecs/ibraries the main ubuntu repo one is not compiled with and it should work then.

---

### Post by JoaoCarlosCorreia on 2008-10-16
Yes, is the svn build of ffmpeg.

How can I completely remove libx264-dev?

I'm trying to follow the tutorial but I have a lot of mess in my ffmpeg folders...
I have a folder "ffmpeg" and another "ffmpeg-0.cvs20060823" and inside this "ffmpeg" I have another folder "ffmpeg" and another "ffmpeg-0.cvs20060823". How can I remove every ffmpeg and start installing it from the scratch?

thanks, 


João

---

### Post by FakeOutdoorsman on 2008-10-16
> **JoaoCarlosCorreia said:**
> How can I completely remove libx264-dev?
You can remove it like any package if you installed it from the Ubuntu repository.  You can use Synaptic Package Manager, apt-get, or aptitude:
```
sudo aptitude purge libx264-dev
```
> I have a folder "ffmpeg" and another "ffmpeg-0.cvs20060823" and inside this "ffmpeg" I have another folder "ffmpeg" and another "ffmpeg-0.cvs20060823". How can I remove every ffmpeg and start installing it from the scratch?
This depends if you used checkinstall or not.  If you used checkinstall then you can remove all of these packages just like you removed libx264-dev.  Otherwise you can go into each ffmpeg folder that contains a "configure" file and uninstall with:
```
sudo make uninstall
```
Once you uninstall everything, backup, move, or rename these folders and start over using the tutorial mentioned by cor2y.

---

### Post by JoaoCarlosCorreia on 2008-10-17
I solved the problem but I'm not sure it was the best way.

I manually removed every file and folder I found that was related to ffmpeg, fetched it from svn and ran ./configure again ant it is working now.
But I configured it without libx264 I still have my initial problem (can't encode to h264)

I'll keep work on that.

Thanks for every posts,

João

---

### Post by cor2y on 2008-10-17
JaoaCarlosCorreia unless you require the latest bleeding edge version of X264, which requires you compile it.
Then i recommend you remove your compiled version of ffmpeg.
Add the medibuntu repos ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) and install both ffmpeg and X264 from there.
The medibuntu version has all the needed libraries and they are up to date , unlike the version found in ubuntu multiverse.

---

