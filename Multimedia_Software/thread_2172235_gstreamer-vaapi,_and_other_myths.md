---
title: "gstreamer-vaapi, and other myths"
date: 2013-09-03
forum: Multimedia Software
---

### Post by quequotion on 2013-09-03
How is it that no matter what version of the gstreamer-vaapi package I download and install from launchpad I never have vaapidecode / vaapisink etc gstreamer elements?

I have gstreamer0.10-vaapi=0.4.0-0ubuntu1~xup (from x-swat/x-updates PPA) installed. The description states:> This package contains GStreamer plugins for VA-API support:
- `vaapiconvert': converts from YUV pixels to VA surfaces
- `vaapisink': a VA-API based video sinkHowever, there are no vaapi elements available to gstreamer at all. I have tried other (lower) versions of the package and had no further luck.

---

### Post by rai_shu2 on 2013-09-03
You do still need the driver backend to implement VAAPI, and those are somewhat limited at the moment, I think.

See [http://www.freedesktop.org/wiki/Software/vaapi/](http://www.freedesktop.org/wiki/Software/vaapi/)

---

### Post by quequotion on 2013-10-23
> **rai_shu2 said:**
> You do still need the driver backend to implement VAAPI, and those are somewhat limited at the moment, I think.  See [http://www.freedesktop.org/wiki/Software/vaapi/](http://www.freedesktop.org/wiki/Software/vaapi/)   Thank you!  Actually, I've been there. I haven't had much more luck compiling from git than I have from anything else.  The driver backend I am using is nvidia's vdpau, which is installed and "working" (nvidia's driver supposedly fully enables this feature, but provides no userspace tools to make use of it...)  After compiling and installing both libva and gstreamer-vaapi from git, no vaapi plugins are available.  gst-inspect reveals that some plugins are being blacklisted (there's no documented way to find out what is on gstreamer's blacklist)  gst-inspect on any of the libraries that gstreamer-vappi installed reveals linking errors that make no sense (none of the libraries can find each other although they all appear to be in the right place)   There was a time, about a year ago, when I was able to install all of this from git and even use the included debian packaging scripts to make it easy. I'm not sure exactly what version I was using at the time, but as far as I can tell it was the last version to be installable (no attempts to upgrade have been sucessful since and I do this about every two months)

---

### Post by Yellow Pasque on 2013-10-23
You do have vdpau-va-driver package install, correct? What is output of vainfo? Should be something like:
```
$ vainfo 
libva info: VA-API version 0.33.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.33 (libva 1.1.1)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```

---

### Post by quequotion on 2013-11-14
> **Temüjin said:**
> You do have vdpau-va-driver package install, correct? What is output of vainfo? Should be something like:Here's mine (note, failing to use version 0.34 at the moment):```
vainfo: VA-API version: 0.34 (libva 1.2.2.pre1)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.5.pre1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG4Simple            :    VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD


```

---

