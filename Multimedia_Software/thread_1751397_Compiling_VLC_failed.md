---
title: "Compiling VLC failed"
date: 2011-05-06
forum: Multimedia Software
---

### Post by Throne777 on 2011-05-06
(I'm running 10.04, hence I'm having to compile VLC)

After finally getting all the dependencies for ```
sudo ./configure
``` I tried running the make command, which threw a hissy fit.

Anyway, here's what the end chunk of text said (which I assume is the most relevant bit):

```

make[7]: Leaving directory `/home/throne777/vlc-1.1.9/modules/audio_filter/resampler'
make[6]: Leaving directory `/home/throne777/vlc-1.1.9/modules/audio_filter/resampler'
make[5]: Leaving directory `/home/throne777/vlc-1.1.9/modules/audio_filter/resampler'
Making install in spatializer
make[5]: Entering directory `/home/throne777/vlc-1.1.9/modules/audio_filter/spatializer'
make  install-am
make[6]: Entering directory `/home/throne777/vlc-1.1.9/modules/audio_filter/spatializer'
  CXX    libspatializer_plugin_la-spatializer.lo
../../../libtool: line 1133: g++: command not found
make[6]: *** [libspatializer_plugin_la-spatializer.lo] Error 1
make[6]: Leaving directory `/home/throne777/vlc-1.1.9/modules/audio_filter/spatializer'
make[5]: *** [install] Error 2
make[5]: Leaving directory `/home/throne777/vlc-1.1.9/modules/audio_filter/spatializer'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/home/throne777/vlc-1.1.9/modules/audio_filter'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/home/throne777/vlc-1.1.9/modules/audio_filter'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/throne777/vlc-1.1.9/modules'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/throne777/vlc-1.1.9'
make: *** [install] Error 2

```

Anyone happen to know how I can fix this issue?

---

### Post by ebasa on 2011-05-06
Ummm, install it from the repositories?

---

### Post by OGpmpdog on 2011-05-06
> **ebasa said:**
> Ummm, install it from the repositories?

That's great advice!!

OP, is there a reason why you want to compile VLC?

Version 1.1.7 is available in the Lucid repositories, and can be downloaded CORRECTLY about 1.5 hours faster than compiled.

I dont know of any glaring differences between 1.1.7 and 1.1.9, besides "wanting to have the latest version"...fyi, I have both versions, and 1.1.9 has crashed twice, 1.1.7 - never.

Good luck.

---

### Post by andrew.46 on 2011-05-06
Indeed you can install vlc from the Ubuntu Repository or from a PPA. If there is a special reason to compile (perhaps for the fun of it or to enable an option not otherwise available) you could perhaps have a glance at this guide:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

which includes a small section on compiling the release version as well. This is for Natty but I suspect will work with a few adjustments for earlier releases. Mind you I am curious about your reason for compiling?

---

### Post by Yellow Pasque on 2011-05-06
```
line 1133: g++: command not found
```
...
```
sudo apt-get install build-essential 
```

---

