---
title: "projectm-pulseaudio M.I.A."
date: 2020-04-28
forum: Multimedia Software
---

### Post by bug67 on 2020-04-28
I'd really like to update to Fossa from Beaver however, one piece of software I rely on is missing from the 20.04 repos.  That would be the stand alone music visualizer, projectm-pulseaudio.  I do know from looking here ([https://www.ubuntuupdates.org/package/core/focal/universe/base/projectm](https://www.ubuntuupdates.org/package/core/focal/universe/base/projectm)) that the version listed there is woefully outdated and, like I said, the pulseaudio derivative doesn't even appear in the repos.  Can someone point me in the direction I need to go to get a version of projectm-pulseaudio up and running on 20.04?

---

### Post by Yellow Pasque on 2020-04-29
It got removed in Debian because it still depended on Qt4.  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=875112](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=875112)
It looks like upstream has moved to Qt5 and they're working on the packaging now: [https://salsa.debian.org/multimedia-team/projectm](https://salsa.debian.org/multimedia-team/projectm)

---

### Post by bug67 on 2020-04-30
Ah, thanks for the info.  Does that mean I'm going to have to wait until whatever version of Ubuntu or Debian officially supports those changes before I can use projectm-pulseaudio again?

---

### Post by Yellow Pasque on 2020-05-01
You can always build your own local copy: [https://github.com/projectM-visualizer/projectm/blob/master/BUILDING.md](https://github.com/projectM-visualizer/projectm/blob/master/BUILDING.md)

---

### Post by bug67 on 2020-05-07
Meh, I'll stick with 18.04.  It'll be good for another 3 years or until such a time and I don't have to compile.  I'm lazy and don't like frustration.  :p

---

### Post by Yellow Pasque on 2020-05-07
> I'm lazy and don't like frustration
Heh, me too.
Bear with me and I can probably package one for you.

---

### Post by bug67 on 2020-05-09
> **Yellow Pasque said:**
> Heh, me too.
Bear with me and I can probably package one for you.

Wow!  That would be super amazing of you!

---

### Post by Yellow Pasque on 2020-05-09
[https://launchpad.net/~dtl131/+archive/ubuntu/mediahacks2/+packages](https://launchpad.net/~dtl131/+archive/ubuntu/mediahacks2/+packages)

I tested it out. Seemed okay.

---

### Post by Yellow Pasque on 2020-05-09
Actually, there may be an issue if you try to install projectm-pulseaudio alone, so make sure you:
```
sudo apt-get install projectm-pulseaudio projectm-data
```
to get the presets.
I think projectm-pulseaudio should recommend projectm-data, but that's another story since I copied a good part of the packaging from Debian...

---

### Post by bug67 on 2020-05-10
Wow, can't say thank you enough.  I don't have 20.04 installed yet.  I am fortunate enough, however, to have a spare drive I can install 20.04 to and leave my current 18.04 intact.  As soon as I am up and running on 20.04, I will try your package and report back.  Thanks again.

---

### Post by bug67 on 2020-05-31
I suppose in the interest of closure, I should mention that I have decided to skip Ubuntu until they include the packages I require in the repositories.  I am up and running on a different distro all together.  Thanks, Yellow Pasque, for your time and effort.

---

### Post by Yellow Pasque on 2020-05-31
Unh-huh...

---

### Post by tomfbush on 2020-10-14
Yellow Pasque, thanks very much for this!

---

### Post by MartyBuntu on 2020-10-14
What possible bleeding-edge update would you require from a *visualizer*...that would cause you to step back from a distro?

I'm genuinely curious.

---

### Post by Yellow Pasque on 2020-10-14
> **MartyBuntu said:**
> What possible bleeding-edge update would you require from a *visualizer*...that would cause you to step back from a distro?

No one said they needed a bleeding edge update. The program did need to be moved to Qt5 and python3 so it could properly build, though.

[QUOTE=tomfbush]Yellow Pasque, thanks very much for this! [/QUOTE]

You're welcome. I guess I have to get on Ubuntu to pull the new version into Ubuntu 20.10 or I'll end up having to package it there too.

---

### Post by mocha on 2020-12-05
I'm also an old fan of projectM.  Recently I compiled the latest git pull with these options, this is on Ubuntu 20.10

```
./configure --enable-sdl --enable-threading --enable-gles --enable-qt --enable-pulseaudio
```

This produced a projectMSDL and projectM-pulseaudio binaries.  The pulseaudio version has the standard interface that I was used to with the Qt menus that can be accessed with the 'm' key.  On the other hand, the SDL binary only responds to a few Ctrl key combos, has no menus, and also I cannot use Ctrl-I to select my pulseaudio monitor device.  I get an error like this:

```
INFO: Opened audio capture device index=0 devId=2: Built-in Audio Analog Stereo
INFO: There is only one audio capture device. There is nothing to toggle at this time.
```

I can't change it in the pulseaudio GUI either.  Any suggestions?  Did I build the SDL version incorrectly?

---

### Post by Yellow Pasque on 2020-12-05
You can try a build for 20.10 in my PPA if that helps.

---

### Post by mocha on 2020-12-05
What options did you use to build it?

---

### Post by Yellow Pasque on 2020-12-07
After thinking about it a little more, I'm going to guess your issue is with pulseaudio rather than the build options.

> **mocha said:**
> What options did you use to build it?

Just about the same as you did.

```
projectM v3.1.7
=====

prefix:                 /usr
sysconfdir:             /etc
libdir:                 ${prefix}/lib/x86_64-linux-gnu
includedir:             ${prefix}/include

compiler:               gcc
cflags:                  -lpthread -g -O2 -fdebug-prefix-map=/<<PKGBUILDDIR>>=. -fstack-protector-strong -Wformat -Werror=format-security -pthread -Wall -Wchar-subscripts -Wformat-security -Wpointer-arith -Wshadow -Wsign-compare -Wtype-limits -DDATADIR_PATH=\""$(pkgdatadir)\"" -I"$(top_srcdir)/vendor" -DGL_SILENCE_DEPRECATION
cxxflags:               -g -O2 -fdebug-prefix-map=/<<PKGBUILDDIR>>=. -fstack-protector-strong -Wformat -Werror=format-security -pthread -std=c++11
libs:                   -lGL  -ldl  -pthread -lQt5Gui -lQt5OpenGL
ldflags:                -lpthread -Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now

- - -

Applications:
=====

libprojectM:            yes
Threading:              yes
SDL:                    yes
Qt:                     yes
Pulseaudio:             yes
Jack:                   yes
OpenGLES:               yes
Emscripten:             no
llvm:                   no
```

---

### Post by mocha on 2020-12-09
It's very strange.  I installed the debs from your PPA and get the same result.  No problem with the projectm-pulseaudio binary, but the projectmsdl has trouble with finding my pulseaudio monitor source for some reason...  I deleted my config.inp and get the same results.

```
$ projectMSDL 
INFO: GL_VERSION: OpenGL ES 3.2 NVIDIA 450.80.02
INFO: GL_SHADING_LANGUAGE_VERSION: OpenGL ES GLSL ES 3.20
INFO: GL_VENDOR: NVIDIA Corporation
INFO: Using data directory: /usr/share/projectM
[projectM] config file: /home/xxxx/.projectM/config.inp
INFO: Using config from /home/xxxx/.projectM/config.inp
INFO: Opened audio capture device index=0 devId=2: Built-in Audio Analog Stereo
fps: 35
INFO: There is only one audio capture device. There is nothing to toggle at this time.
```

---

