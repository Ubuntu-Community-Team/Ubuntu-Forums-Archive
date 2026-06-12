---
title: "Compiling ffmpeg with fdk-aac support"
date: 2014-12-27
forum: Multimedia Software
---

### Post by plazman30 on 2014-12-27
I am trying to compile ffmpeg with fdk-aac support using this guide off the ffmpeg site:

[https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

I am running Ubuntu Server 14.04.1

I'm running into a couple of problems:

1. libfdk-aac doesn't seem to install.  When I run the 'make install' command it runs and exits with a 1.  When I do an 'sudo updatedb' followed by a 'locate *aac*, it only finds files in the source folder.
2. When I try and compile libvpx the recommended install process it ends with "make[1]: Nothing to be done for `all'".

I'm trying to compile an encoder that uses fdk-aac to encode flac files.  By default I think ffmpeg uses faac, which seems to substandard when compored to fdk-aac.

Any help anyone could provide would be greatly appreciated.

---

### Post by andrew.46 on 2014-12-27
> **plazman30 said:**
> 1. libfdk-aac doesn't seem to install.  When I run the 'make install' command it runs and exits with a 1.  When I do an 'sudo updatedb' followed by a 'locate *aac*, it only finds files in the source folder.

This guide installs the files in $HOME/ffmpeg_build not to /usr or /usr/local as you might perhaps be expecting. Perhaps run something like the following to find your files:

```

find $HOME -iname *fdk*

```

and something similar for your lost vpx files :).

> **plazman30 said:**
>  By default I think ffmpeg uses faac, which seems to substandard when compored to fdk-aac.

For FFmpeg it certainly does seem to default to libfaac if it is present. But there is a choice of faac or libfdk-aac if compiled against these external libraries or it can use its own internal aac. From my own copy:

```

andrew@ilium~$ **[COLOR="#FF0000"]ffmpeg -encoders 2>/dev/null | grep aac[/COLOR]**
 A..X.. aac                  AAC (Advanced Audio Coding)
 A..... libfaac              libfaac AAC (Advanced Audio Coding) (codec aac)
 A..... libfdk_aac           Fraunhofer FDK AAC (codec aac)
andrew@ilium~$ 

```

Hopefully I have answered a few of your queries?

---

### Post by plazman30 on 2014-12-27
Did you compile ffmpeg yourself?

---

### Post by FakeOutdoorsman on 2014-12-28
> **plazman30 said:**
> 1. libfdk-aac doesn't seem to install.  When I run the 'make install' command it runs and exits with a 1.

I don't know what caused that.

> **plazman30 said:**
> 2. When I try and compile libvpx the recommended install process it ends with "make[1]: Nothing to be done for `all'".

Seems like configure was skipped:
```
cd ~/ffmpeg_sources/libvpx-v1.3.0
make clean
PATH="$HOME/bin:$PATH" ./configure --prefix="$HOME/ffmpeg_build" --disable-examples
PATH="$HOME/bin:$PATH" make
make install
```
Note the "make clean".

I won't be able to test the guide until Monday because I'm usually away from my nerd machine on the weekends.

---

### Post by steeldriver on 2014-12-28
Sorry if this is a dumb question but did you actually enable the feature? it appears to be disabled by default

```

$ ./configure --help | grep fdk
  --enable-libfdk-aac      enable AAC de/encoding via libfdk-aac **[no]**

```

---

### Post by andrew.46 on 2014-12-29
> **plazman30 said:**
> Did you compile ffmpeg yourself?

Is there any other way? :)

---

