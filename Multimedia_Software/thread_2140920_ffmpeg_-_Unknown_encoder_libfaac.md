---
title: "ffmpeg - Unknown encoder libfaac"
date: 2013-05-01
forum: Multimedia Software
---

### Post by cibalo on 2013-05-01
Recently, I have freshly installed Ubuntu 12.04.2 i386 on my computer. I follow the instructions from FFmpeg, Community Ubuntu Documentation, [https://help.ubuntu.com/community/FFmpeg#Precise_Configurations](https://help.ubuntu.com/community/FFmpeg#Precise_Configurations), to enable Universe/Medibuntu repos and to install ffmpeg. And this instruction reads as, "the following additional libraries will be downloaded: apport-hooks-medibuntu, libfaac0, libopencore-amrnb0, libopencore-amrwb0"

I tried to convert avi video using libfaac codec, then I got the following error message:
Unknown encoder 'libfaac'

Where is the codec location for ffmpeg in Precise/Natty? Can I just copy the libfaac codec from Natty to Precise. I had Natty installed on my computer in another partition, and the same ffmpeg command, that converted avi video using libfaac codec, worked alright with me.

I try not to compile-install ffmpeg. Is there any idea to add libfaac to my ffmpeg? Can you please let me know what I'm missing?

Thank you very much in advance!!! 

Best Regards,
cibalo

---

### Post by andrew.46 on 2013-05-01
Seems a little odd, I suspect that you need * libavcodec-extra-53* but this is given on the wiki page...

---

### Post by cibalo on 2013-05-01
Hello andrew.46,

Thank you very much for replying to my post.

> **andrew.46 said:**
> I suspect that you need * libavcodec-extra-53* 

Yes, I do have libavcodec-extra-53 installed. I do have all packages installed/dist-upgraded as suggested by the Help Wiki Page.

Best Regards,
cibalo

---

### Post by mc4man on 2013-05-01
Could you run this to check what version is installed (currently the Ubuntu repo version is higher than mediabuntu's
```
apt-cache policy libavcodec-extra-53
```

---

### Post by cibalo on 2013-05-02
Hello mc4man,

Thank you very much for replying to my post.
> **mc4man said:**
> Could you run this to check what version is installed
libavcodec-extra-53 version outputs as follows:
$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
  Installed: 4:0.8.6ubuntu0.12.04.1
  Candidate: 4:0.8.6ubuntu0.12.04.1
  Version table:
 *** 4:0.8.6ubuntu0.12.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe i386 Packages
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security/universe i386 Packages
        100 /var/lib/dpkg/status
     4:0.8.5ubuntu0.12.04.1+medibuntu1 0
        500 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise/non-free i386 Packages
     4:0.8.1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
$ ffmpeg -codecs|grep -in "libxvid\|libx264\|libfaac\|libmp3lame"
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:00:59 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
139:  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
148:  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
149:  EV    libxvid         libxvidcore MPEG-4 part 2
$ uname -a
Linux host12042 3.5.0-28-generic #48~precise1-Ubuntu SMP Wed Apr 24 21:43:05 UTC 2013 i686 i686 i386 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

---

### Post by andrew.46 on 2013-05-02
So the Ubuntu package:

[http://packages.ubuntu.com/precise/libavcodec-extra-53](http://packages.ubuntu.com/precise/libavcodec-extra-53)

vs the Medibuntu package:

[http://packages.medibuntu.org/precise/libavcodec-extra-53.html](http://packages.medibuntu.org/precise/libavcodec-extra-53.html)

Always easier to compile your own :)

---

### Post by cibalo on 2013-05-08
Hello andrew.46,

Thank you very much for replying to my post.

> **andrew.46 said:**
> Always easier to compile your own 

I have no other choice but to compile my own.

Thank you any way.

---

### Post by andrew.46 on 2013-05-08
This is nearly always the best course of action for FFmpeg, the rewards for using the most recent version are great. Doubtless you have seen this page:

[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Best place to go to for such a guide...

---

### Post by ron999 on 2013-05-08
> **cibalo said:**
> 
I have no other choice but to compile my own.

Hi
You can add the medibuntu repository to enable libfaac with Ubuntu Precise.
**[SIZE=4]Adding the Repository[/SIZE]**
Look here ---> [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")
Then 
```
sudo apt-get install libavcodec-extra-53
```

(medibuntu was updated to 4:0.8.[COLOR="#FF0000"]6[/COLOR]ubuntu0.12.04.1+medibuntu1 on/after Thu, 02 May 2013)



```
xubuntu@xubuntu:~$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
  Installed: 4:0.8.6ubuntu0.12.04.1+medibuntu1
  Candidate: 4:0.8.6ubuntu0.12.04.1+medibuntu1
  Version table:
 *** 4:0.8.6ubuntu0.12.04.1+medibuntu1 0
        500 http://packages.medibuntu.org/ precise/non-free i386 Packages
        100 /var/lib/dpkg/status
     4:0.8.6ubuntu0.12.04.1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe i386 Packages
     4:0.8.1ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
```

---

### Post by cibalo on 2013-05-09
Hi,

> **ron999 said:**
> You can add the medibuntu repository to enable libfaac with Ubuntu Precise

Yes, I do have libavcodec-extra-53 installed. I do have all packages installed/dist-upgraded as suggested in the Help Wiki Page,
[https://]("https://help.ubuntu.com/community/FFmpeg#Precise_Configurations")[help.ubuntu.com/community/FFmpeg#Precise_Configurations]("https://help.ubuntu.com/community/FFmpeg#Precise_Configurations").

---

### Post by ron999 on 2013-05-09
> **cibalo said:**
> Hi,
Yes, I do have libavcodec-extra-53 installed.
Same version as this?
```
xubuntu@xubuntu:~$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
  [COLOR="#FF0000"]Installed: 4:0.8.6ubuntu0.12.04.1+medibuntu1[/COLOR]
  Candidate: 4:0.8.6ubuntu0.12.04.1+medibuntu1
  Version table:
 *** 4:0.8.6ubuntu0.12.04.1+medibuntu1 0
        500 http://packages.medibuntu.org/ precise/non-free i386 Packages
        100 /var/lib/dpkg/status
     4:0.8.6ubuntu0.12.04.1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/universe i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe i386 Packages
     4:0.8.1ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
```

---

### Post by cibalo on 2013-05-10
Hi,
> **ron999 said:**
> Same version as this?

Yes, I have the followings, but coming from us.archive.

```
$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
Installed: 4:0.8.6ubuntu0.12.04.1
Candidate: 4:0.8.6ubuntu0.12.04.1
Version table:
*** 4:0.8.6ubuntu0.12.04.1 0
500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe i386 Packages
500 http://us.archive.ubuntu.com/ubuntu/ precise-security/universe i386 Packages
100 /var/lib/dpkg/status
4:0.8.5ubuntu0.12.04.1+medibuntu1 0
500 http://packages.medibuntu.org/ precise/non-free i386 Packages
4:0.8.1ubuntu1 0
500 http://us.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
```

---

### Post by ron999 on 2013-05-10
> **cibalo said:**
> ... but coming from us.archive.

```
$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
[COLOR="#FF0000"]Installed: 4:0.8.6ubuntu0.12.04.1[/COLOR]

```

> You can add the medibuntu repository to enable libfaac with Ubuntu Precise.

```
xubuntu@xubuntu:~$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
 [COLOR="#FF0000"] Installed: 4:0.8.6ubuntu0.12.04.1+medibuntu1[/COLOR]
```

```
xubuntu@xubuntu:~$ ffmpeg -codecs | grep libfaac
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:00:59 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
  EA    libfaac         libfaac AAC (Advanced Audio Codec)

```

---

### Post by cibalo on 2013-05-23
Hello,
> **ron999 said:**
> xubuntu@xubuntu:~$ apt-cache policy libavcodec-extra-53
libavcodec-extra-53:
 [COLOR=#FF0000] Installed: 4:0.8.6ubuntu0.12.04.1+medibuntu1[/COLOR]

I get tired of installing this libavcodec-extra-53 again. I have installed/removed many times.

Finally, I have compiled my ffmpeg, as detailed in [https://gist.github.com/faleev/3435377](https://gist.github.com/faleev/3435377).
```
$ ffmpeg -version
ffmpeg version N-37664-gfbd0f91
built on May 23 2013 19:00:42 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
configuration: --enable-gpl --enable-nonfree --enable-version3 --enable-libfaac --enable-libmp3lame --enable-libx264 --enable-libxvid
$ ffmpeg -codecs 2>/dev/null|grep -n --color=auto "libxvid\|libx264\|libfaac\|libmp3lame"
73: DEV.LS h264     H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (decoders: h264 h264_vdpau ) (encoders: libx264 libx264rgb )
101: DEV.L. mpeg4   MPEG-4 part 2 (decoders: mpeg4 mpeg4_vdpau ) (encoders: mpeg4 libxvid )
210: [COLOR=#ff0000]DEA.L. aac     AAC (Advanced Audio Coding) (encoders: aac libfaac )[/COLOR]
279: DEA.L. mp3     MP3 (MPEG audio layer 3) (decoders: mp3 mp3float ) (encoders: libmp3lame )
```
Now, I have libfaac!

---

### Post by FakeOutdoorsman on 2013-05-23
> **cibalo said:**
> Finally, I have compiled my ffmpeg, as detailed in [https://gist.github.com/faleev/3435377](https://gist.github.com/faleev/3435377).

That's an outdated ripoff of [Compile FFmpeg on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

---

### Post by andrew.46 on 2013-05-23
Mind you faac is not the best aac encoder to use anyway :)

---

### Post by cibalo on 2013-05-23
Hello,
> **FakeOutdoorsman said:**
> That's an outdated ripoff of [Compile FFmpeg on Ubuntu]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide").

Basically, there is no big difference between your CompilationGuide and my CompilationGuide. But, take note that your UbuntuCompilationGuide will "make install" your ffmpeg into your $HOME/ffmpeg_build. It is for your own use. And I prefer to "sudo checkinstall" the ffmpeg for all users.

---

### Post by monkeybrain2012 on 2013-05-24
> **cibalo said:**
> Hello,


Basically, there is no big difference between your CompilationGuide and my CompilationGuide. But, take note that your UbuntuCompilationGuide will "make install" your ffmpeg into your $HOME/ffmpeg_build. It is for your own use. And I prefer to "sudo checkinstall" the ffmpeg for all users.

Actually that is his compilation guide, he only changed it recently to install everything in $HOME, see discussions here. [http://ubuntuforums.org/showthread.php?t=786095&page=225](http://ubuntuforums.org/showthread.php?t=786095&page=225)

---

### Post by mc4man on 2013-05-24
> **andrew.46 said:**
> Mind you faac is not the best aac encoder to use anyway :)

What are you using (if any?).
Here fdk-aac, also in the ./configure using --enable-example to build aac-enc for checking out direct encoding

---

### Post by andrew.46 on 2013-05-24
> **mc4man said:**
> What are you using (if any?).

When I use aac encoding I spend some extra time and use NeroAacEnc, I am not what you would call an audiophile and my speakers etc are not the best but I can hear the difference with NeroAacEnc over faac...

---

### Post by FakeOutdoorsman on 2013-05-24
> **mc4man said:**
> What are you using (if any?)

I've been using libfdk-aac. Windows users and Winos should also consider [qaac](https://sites.google.com/site/qaacpage/).

Also see [FFmpeg and AAC Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide).

---

### Post by mc4man on 2013-05-26
> **mc4man said:**
> What are you using (if any?)
Here fdk-aac, also in the ./configure using --enable-example to build aac-enc for checking out direct encoding
drifting way off-topic so just a short note (not sure about interest anyway.
Born slightly from the ffmpeg note about vbr with libfdk_aac, 'unsupported, ect.'

Put up  a shared build of fdk-aac & instead of using the source's encoder (aac-enc),  went with a cli frontend that's quite interesting - 
[https://github.com/nu774/fdkaac](https://github.com/nu774/fdkaac)

Options are in attached file, what interested me was to use ffprobe to create a 'Tag' file (JSON) & encode/tag with 'fdkaac'
It, (fdkaac), also works with pipes so can use ffmpeg to pipe an audio file like flac to fdkaac & tag, ect.

(maybe someday a thread if there is interest in exploring...

---

