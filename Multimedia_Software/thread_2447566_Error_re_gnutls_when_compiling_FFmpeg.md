---
title: "Error re gnutls when compiling FFmpeg"
date: 2020-07-21
forum: Multimedia Software
---

### Post by johnaaronrose on 2020-07-21
Tried to compile FFmpeg (on Ubuntu 18.04) using instructions at: [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)


Source was obtained from link [https://johnvansickle.com/ffmpeg/builds/ffmpeg-git-amd64-static.tar.xz](https://johnvansickle.com/ffmpeg/builds/ffmpeg-git-amd64-static.tar.xz)


All well until "ERROR: gnutls not found using pkg-config".


Terminal output would be attached if Forum software would let me attach the 50kB .zip file: I choose the file & click the upload button but nothing happens. 

Error line is "ERROR: gnutls not found using pkg-config". I installed the [COLOR=#000000]libgnutls28-dev package before attempting the compile.[/COLOR]

---

### Post by CelticWarrior on 2020-07-22
Terminal output should be in code tags. Go Advanced > click "#" and paste inside.

---

### Post by johnaaronrose on 2020-07-22
Appropriate parts of Terminal output:

```

john@JohnPC:~$ sudo apt-get update -qq && sudo apt-get -y install autoconf automake build-essential cmake git-core libass-dev libfreetype6-dev libgnutls28-dev libsdl2-dev libtool libva-dev libvdpau-dev libvorbis-dev libxcb1-dev libxcb-shm0-dev libxcb-xfixes0-dev pkg-config texinfo wget yasm zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done

ffmpeg/libpostproc/version.h
ERROR: gnutls not found using pkg-config

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
[EMAIL="ffmpeg-user@ffmpeg.org"]ffmpeg-user@ffmpeg.org[/EMAIL] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "ffbuild/config.log" produced by configure as this will help
solve the problem.

```

Unfortunately, I've deleted the above mentioned log file.

---

### Post by Yellow Pasque on 2020-07-22
I don't understand. If you're using the static version, it's already built. :?

---

### Post by johnaaronrose on 2020-07-24
Not sure what you mean. ffmpeg (just upgraded from 3.4.6 to) 3.4.8 is version supplied by Ubuntu repos. I've been trying to compile ffmpeg from git source. The compilation procedure (s detailed by trac.ffmpeg.org i.e. the developers of ffmpeg) gave the gnutls error. However, trac.ffmpeg.org don't reply to my reporting this error!

---

### Post by SeijiSensei on 2020-07-24
Try running
```
sudo apt-get build-dep ffmpeg
```
then compiling. Any better?

---

### Post by Yellow Pasque on 2020-07-24
> **johnaaronrose said:**
> Not sure what you mean. I've been trying to compile ffmpeg from git source.

The link you gave for the source is a pre-built static linked version. What exactly are you trying to do here? Are you trying to build statically or dynamically (i.e. with system libs)?

---

### Post by johnaaronrose on 2020-07-26
> **Yellow Pasque said:**
> The link you gave for the source is a pre-built static linked version. What exactly are you trying to do here? Are you trying to build statically or dynamically (i.e. with system libs)?
I understand at last. I downloaded (release version amd64) ffmpeg (version 4.3.1) from that link I specified. When I ran it, it gave a problem "Unknown input format: 'pulse'". I think that this is due to libpulse not being enabled as part of the creation of that ffmpeg version. I've recorded it as a bug (#8817) at [https://trac.ffmpeg.org/ticket/8817](https://trac.ffmpeg.org/ticket/8817)
So unless I get a helpful reply from there, I will have to compile ffmpeg. I therefore have to solve the gnutls problem,
I don't understand the difference between a static and a dynamic build. I'm not a developer.

---

### Post by SeijiSensei on 2020-07-26
> **johnaaronrose said:**
> II think that this is due to libpulse not being enabled as part of the creation of that ffmpeg version. I've recorded it as a bug (#8817) at [https://trac.ffmpeg.org/ticket/8817](https://trac.ffmpeg.org/ticket/8817)
Why aren't you using the version in the Ubuntu repositories? It has support for PulseAudio already built-in. In general, I see few reasons to compile applications unless there's some unique thing that's missing in the repository version that you need. That's pretty rare in my experience.

```

sudo apt update
sudo apt install ffmpeg

```

---

### Post by shantiq on 2020-08-04
> **johnaaronrose said:**
> Tried to compile FFmpeg (on Ubuntu 18.04) using instructions at: [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) .....

the fix is here
do not ask me why you need this but it fixed my recent install using [THE GUIDE]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu")


```
[FONT=Consolas]sudo apt-get install libunistring-dev[/FONT][FONT=inherit]
[/FONT]

```

... and then try again


read further[ here]("https://askubuntu.com/questions/1252997/unable-to-compile-ffmpeg-on-ubuntu-20-04") you might get it personally I just know it removed the obstacle

---

### Post by david11629 on 2021-04-09
Thanks for your comment. This helped me with the error.

---

### Post by mc4man on 2021-04-10
> **shantiq said:**
> the fix is here
do not ask me why you need this but it fixed my recent install using [THE GUIDE]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu")


```
[FONT=Consolas]sudo apt-get install libunistring-dev[/FONT][FONT=inherit]
[/FONT]

```

... and then try again


read further[ here]("https://askubuntu.com/questions/1252997/unable-to-compile-ffmpeg-on-ubuntu-20-04") you might get it personally I just know it removed the obstacle
 The need for that dev package is from this ffmpeg configure option, (which provides no discernable value
--pkg-config-flags="--static

---

