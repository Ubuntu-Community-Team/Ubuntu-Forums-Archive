---
title: "WebcamStudio install fails"
date: 2012-06-06
forum: Multimedia Software
---

### Post by neuman1812 on 2012-06-06
System: Ubuntu 12.4  64bit


I first attempted to install using the .deb file from
[http://www.ws4gl.org/download/installing-on-ubuntu]("http://www.ws4gl.org/download/installing-on-ubuntu")

But in Gdebi it get the error 
```

Error: Dependency is not satisfiable: gstreamer0.10-plugins-ugly-multiverse

```
So I go to install that..but its not available
```
$ sudo apt-get install gstreamer0.10-
gstreamer0.10-alsa
gstreamer0.10-buzztard
gstreamer0.10-buzztard-doc
gstreamer0.10-crystalhd
gstreamer0.10-doc
gstreamer0.10-ffmpeg
gstreamer0.10-ffmpeg-dbg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-plugins-mp3-partner
gstreamer0.10-gconf
gstreamer0.10-gnomevfs
gstreamer0.10-gnonlin
gstreamer0.10-gnonlin-dbg
gstreamer0.10-gnonlin-doc
gstreamer0.10-hplugins
gstreamer0.10-nice
gstreamer0.10-packagekit
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-dbg
gstreamer0.10-plugins-bad-doc
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-bad-multiverse-dbg
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-base-dbg
gstreamer0.10-plugins-base-doc
gstreamer0.10-plugins-cutter
gstreamer0.10-plugins-good
gstreamer0.10-plugins-good-dbg
gstreamer0.10-plugins-good-doc
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-dbg
gstreamer0.10-plugins-ugly-doc
gstreamer0.10-pocketsphinx
gstreamer0.10-pulseaudio
gstreamer0.10-qapt
gstreamer0.10-sdl
gstreamer0.10-tools
gstreamer0.10-vaapi
gstreamer0.10-vaapi-doc
gstreamer0.10-x

```

Then I try from the PPA
```

The following NEW packages will be installed:
  webcamstudio
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/11.3 MB of archives.
After this operation, 12.4 MB of additional disk space will be used.
Selecting previously unselected package webcamstudio.
(Reading database ... 236902 files and directories currently installed.)
Unpacking webcamstudio (from .../webcamstudio_0.56-1~getdeb2_all.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Setting up webcamstudio (0.56-1~getdeb2) ...
update-rc.d: warning: webcamstudio stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
Removing the webcamstudio module from memory
ERROR: Module webcamstudio does not exist in /proc/modules
Removing webcamstudio.ko from the modules
Restating the webcamstudio service to update the module
 * Stopping WebcamStudio kernel module webcamstudio                     [ OK ] 
 * Starting WebcamStudio kernel module webcamstudio                            make -C /lib/modules/3.2.0-25-generic/build SUBDIRS=/tmp/webcamstudio-src modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  CC [M]  /tmp/webcamstudio-src/webcamstudio.o
/tmp/webcamstudio-src/webcamstudio.c:191:2: error: #error "need CONFIG_VIDEO_V4L1_COMPAT"
/tmp/webcamstudio-src/webcamstudio.c:215:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/webcamstudio-src/webcamstudio.o] Error 1
make[1]: *** [_module_/tmp/webcamstudio-src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
make: *** [all] Error 2
install -d /lib/modules/3.2.0-25-generic/kernel/drivers/misc
install -m 644 -c webcamstudio.ko /lib/modules/3.2.0-25-generic/kernel/drivers/misc
install: cannot stat `webcamstudio.ko': No such file or directory
make: *** [install] Error 1

```

The two lines that seem to be causing the error are 
```

/tmp/webcamstudio-src/webcamstudio.c:191:2: error: #error "need CONFIG_VIDEO_V4L1_COMPAT"
/tmp/webcamstudio-src/webcamstudio.c:215:28: fatal error: linux/videodev.h: No such file or directory

``` 

A google search finds that  videodev.h was removed from the 2.6.38 kernal and replaced with videodev2.h  

 Since Im running the 3.2.0-25   is there anyway around this error?

---

