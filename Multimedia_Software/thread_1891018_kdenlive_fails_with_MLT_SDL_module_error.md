---
title: "kdenlive fails with MLT SDL module error"
date: 2011-12-04
forum: Multimedia Software
---

### Post by jtappin on 2011-12-04
I've just installed kdenlive on a Kubuntu Oneiric system. But when I start it up, I get a welcome(?) screen that reports:

Fatal Error
MLT's SDL module not found. Please check your MLT 
install. Kdenlive will not work until this issue is fixed.

I assume that there is a missing dependency -- but which?

The relevant package information is below:

```
$ dpkg -l kdenlive
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  kdenlive                          0.8-4build1                       non-linear video editor

$ dpkg -l \*sdl\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  gstreamer0.10-sdl                 0.10.22-2ubuntu4                  GStreamer plugin for SDL output
un  ia32-libs-sdl                     <none>                            (no description available)
un  ia32-libsdl1.2debian-alsa         <none>                            (no description available)
un  libsdl1.2                         <none>                            (no description available)
un  libsdl1.2-all                     <none>                            (no description available)
un  libsdl1.2-arts                    <none>                            (no description available)
un  libsdl1.2-esd                     <none>                            (no description available)
un  libsdl1.2-nas                     <none>                            (no description available)
un  libsdl1.2-oss                     <none>                            (no description available)
ii  libsdl1.2debian                   1.2.14-6.1ubuntu4                 Simple DirectMedia Layer
un  libsdl1.2debian-all               <none>                            (no description available)
ii  libsdl1.2debian-alsa              1.2.14-6.1ubuntu4                 Simple DirectMedia Layer (with X11 and ALSA options)
un  libsdl1.2debian-arts              <none>                            (no description available)
un  libsdl1.2debian-esd               <none>                            (no description available)
un  libsdl1.2debian-nas               <none>                            (no description available)
un  libsdl1.2debian-oss               <none>                            (no description available)
un  libsdl1.2debian-pulseaudio        <none>                            (no description available)

$ dpkg -l \*mlt\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
un  libmlt++0.2                       <none>                            (no description available)
un  libmlt++2                         <none>                            (no description available)
ii  libmlt++3                         0.7.4-3                           MLT multimedia framework C++ wrapper (runtime)
ii  libmlt-data                       0.7.4-3                           multimedia framework (data)
un  libmlt0.2                         <none>                            (no description available)
un  libmlt0.2.5                       <none>                            (no description available)
un  libmlt1                           <none>                            (no description available)
un  libmlt2                           <none>                            (no description available)
un  libmlt3                           <none>                            (no description available)
ii  libmlt4                           0.7.4-3                           multimedia framework (runtime)
un  sgmltools-2                       <none>                            (no description available)

```

---

### Post by MoreOrLess on 2011-12-04
[http://kubuntuforums.net/forums/index.php?topic=3118584.0](http://kubuntuforums.net/forums/index.php?topic=3118584.0)

---

### Post by Serious_Sally on 2011-12-05
[LEFT][http://www.kdenlive.org/forum/ubuntu-1110-wont-run-kdenlive-mlts-sdl-module-not-found](http://www.kdenlive.org/forum/ubuntu-1110-wont-run-kdenlive-mlts-sdl-module-not-found)

sudo add-apt-repository ppa:sunab/kdenlive-svn
sudo apt-get update

*You should notice that you now have new updates available to the mlt module and Kdenlive, so grab those and Kdenlive will run normally.

Here is a YouTube video (in German but you can still see what was done) which solves this issue:

[http://www.youtube.com/watch?v=H-6_evPMdvw](http://www.youtube.com/watch?v=H-6_evPMdvw)

:)


[/LEFT]

---

