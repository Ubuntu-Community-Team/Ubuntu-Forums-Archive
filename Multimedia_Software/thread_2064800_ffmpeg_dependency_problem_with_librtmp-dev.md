---
title: "ffmpeg dependency problem with librtmp-dev"
date: 2012-09-30
forum: Multimedia Software
---

### Post by stevebu56 on 2012-09-30
I am on xubuntu 12.04 trying to install ffmpeg via the [Ubuntu Compilation Guide]("http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide").  I am getting the following error when I try to install the packages with apt.  

Any thoughts on what I can do at this point? 

```
sburke@ht-pc:~$ sudo apt-get -y install autoconf build-essential checkinstall git libfaac-dev libgpac-dev   libjack-jackd2-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev   librtmp-dev libsdl1.2-dev libtheora-dev libtool libva-dev libvdpau-dev libvorbis-dev   libx11-dev libxfixes-dev pkg-config texi2html yasm zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 librtmp-dev : Depends: libgnutls-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by jerrrys on 2012-09-30
The [package]("http://packages.ubuntu.com/precise/libgnutls-dev") is available.

What happens if you apt-get install libgnutls-dev ?

Have you tried install -f ?

---

### Post by stevebu56 on 2012-09-30
I tried with -f and I get the same error.  

For installing libgnutls-dev I get another dependency issue. 
```

sburke@ht-pc:~$ sudo apt-get install -f libgnutls-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgnutls-dev : Depends: libtasn1-3-dev (>= 0.3.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by jerrrys on 2012-09-30
Looks like you entered dependency hell

Don't know if this is any help or not, but [check here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ffmpeg+dependency+hell&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

Good luck

---

### Post by ron999 on 2012-09-30
> **stevebu56 said:**
> I am on xubuntu 12.04 trying to install ffmpeg via the [Ubuntu Compilation Guide]("http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide").  I am getting the following error when I try to install the packages with apt.  

Any thoughts on what I can do at this point? 


Hi
There's a dedicated thread for compiling FFmpeg with Ubuntu.
That's where to ask your question.
Here ---> [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by mc4man on 2012-09-30
There's no real dep issue, likely just with your sources
Open up software sources (software-properties-gtk
Make sure that under the "Ubuntu Software" tab the 1st 4 are checked, under the "Updates" tab the 1st 2 are checked.
Then close out S-C & run 
sudo apt-get update 
Then try again

(the version of libtasn1-3-dev avail. should be - (2.10-1ubuntu1.1)
If still issue what does this show

apt-cache policy libtasn1-3-dev

---

### Post by spookybathtub on 2013-02-26
I had the same problem as the OP when trying to install rtorrent.  I'm running 12.04.  I noticed the librtmp-dev version installed was labelled luicd.  So I forced it to install the precise version, which it warned was a downgrade, and then everything worked after that.  Hopefully that will work for others too.

---

