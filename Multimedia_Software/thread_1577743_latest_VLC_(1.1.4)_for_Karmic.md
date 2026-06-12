---
title: "latest VLC (1.1.4) for Karmic?"
date: 2010-09-19
forum: Multimedia Software
---

### Post by bsmith1051 on 2010-09-19
I'm still running 9.10 (Karmic) on my main box and I'm trying to find a newer version of VLC.  But almost all the recent blog posts re VLC 1.1.4 point to PPAs that only support Lucid and/or Maverick.

For instance, all these PPAs ignore Karmic:
[LIST]
[*]ppa:nilarimogard/webupd8
[*]ppa:lucid-bleed/ppa
[*]ppa:ferramroberto/vlc
[*]ppa:n-muench/vlc  (this one specifically supports VA-API)
[/LIST]
The version of VLC in the Ubuntu depositories is 1.0.2 which is not only old but has a security leak; the VLC homepage warns against using it!

I suspect the problem here is that VLC is in the middle of rolling-out hardware acceleration and there's a bunch of different versions of it now (with and without the new VA-API enabled ffmpeg).  So it's a moving target. But surely there's a better alternative for Karmic users than just 1.0.2?

The best I've been able to come up with is the 'Nvidia Cutting Edge Multimedia' PPA which has VLC 1.1.0
[LIST]
[*]ppa:nvidia-vdpau/cutting-edge-multimedia
[/LIST]

---

### Post by ron999 on 2010-09-19
Hi
I'm still using Karmic.
I wasn't able to find a suitable PPA for VLC either.

I now have VLC-1.1.4 installed.
Originally I compiled VLC-1.1.2, and since then I've used the same method to compile VLC-1.1.4.
I got a lot of help from this forum.
It starts here at around post # 5:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1552476]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1552476")
Then continues here at around post # 131:-[http://ubuntuforums.org/showthread.php?p=9721410#post9721410]("http://ubuntuforums.org/showthread.php?p=9721410#post9721410")
I had previously compiled good versions of ffmpeg and x264 using the tutorial here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")

I found it hard going because I am new to compiling programs.
Maybe you have more experience here.
Good luck
:guitar:

[IMG]http://img819.imageshack.us/img819/7326/vlc114.png[/IMG]

---

### Post by cchhrriiss121212 on 2010-09-19
Try the debian package archive:
[http://packages.debian.org/experimental/vlc]("http://packages.debian.org/experimental/vlc")
A deb is easier to install than compiling from source, but you may have several dependencies to update.

---

### Post by ron999 on 2010-09-19
> **cchhrriiss121212 said:**
> Try the debian package archive:
[http://packages.debian.org/experimental/vlc]("http://packages.debian.org/experimental/vlc")
A deb is easier to install than compiling from source, but you may have several dependencies to update.

Yes, if the deb works, it's easier than compiling.
I don't think that one was available previously.

Now that I have the instructions, it's not difficult for me to compile new versions.:)

---

### Post by andrew.46 on 2010-09-19
Perhaps an even easier option is to run Maverick when it comes out in 20 days or so, it will have 1.1.4 in the Ubuntu repository.

Andrew

---

### Post by suseno on 2010-09-25
@ron: would you please send me compiled version (.deb) of VLC 1.1.4? I also run Ubuntu 9.04 and using VLC 1.0.2 and have the same problems with thread starter.

You can sent it to My E-mail: [IMG]http://i9.photobucket.com/albums/a62/oogenesis/MyYahooMail.jpg[/IMG]

---

### Post by richard k belew on 2010-11-04
> **cchhrriiss121212 said:**
> Try the debian package archive:
[http://packages.debian.org/experimental/vlc]("http://packages.debian.org/experimental/vlc")
A deb is easier to install than compiling from source, but you may have several dependencies to update.

also working from karmic, i tried starting from this .deb, but got stumped by being unable
to resolve the dependencies:

```
vlc_1.1.4-1:	->

vlc-nox	->

libass4: (SubStation Alpha (SSA) is a subtitle file format ... !) ->

libfontconfig1 (>= 2.8.0)

Error: Breaks existing package 'libfontconfig1-dev' dependency libfontconfig1 (= 2.6.0-1ubuntu12)

```

and about here i started to worry about polluting my karmic dependencies.
(and for subtitles?!)

did you have a different experience?

 - rik

---

