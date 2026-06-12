---
title: "Broken video hardware acceleration on Ubuntu 20.04"
date: 2021-11-17
forum: Multimedia Software
---

### Post by bomc68000 on 2021-11-17
Hi everyone!

I have a problem with hardware video decoding with mpv. It was working more or less effectively but some time ago it just broke. My guess was to install a new version of mpv, but it didn't help. I have installed VAAPI and VDPAU, but both deny to work in somehow similar manner. I'm not a nerd at all, I don't have a clue if I could do something to fix it.
I have an old AMD A6-5200 APU (with KABINI graphics). The outputs of both 'vainfo' and 'vdpauinfo' seem just fine, for example vainfo reports:

libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.7 (libva 2.6.0)
vainfo: Driver version: Mesa Gallium driver 21.0.3 for AMD KABINI (DRM 2.50.0, 5.11.0-051100-generic, LLVM 12.0.0)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileNone                   :    VAEntrypointVideoProc

But when I run mpv, the hardware decoding (in this case VAAPI) is apparently not used and mpv reports:
...
[ffmpeg] AVHWFramesContext: Failed to create surface: 2 (resource allocation failed).
[ffmpeg] AVHWFramesContext: Unable to allocate a surface from internal buffer pool.
Failed to allocate hw frames.
AO: [pulse] 48000Hz stereo 2ch float
VO: [gpu] 1280x688 yuv420p
...

Does anybody have an idea what could be done to get it working again?

Thanks in advance,
Bo

---

### Post by monkeybrain20122 on 2021-11-17
I don't know if this applies,same errors but seems the guy is using vaapi with vdpau backend.
[https://github.com/mpv-player/mpv/issues/4408](https://github.com/mpv-player/mpv/issues/4408)

---

### Post by bomc68000 on 2021-11-17
> **monkeybrain20122 said:**
> I don't know if this applies,same errors but seems the guy is using vaapi with vdpau backend.
[https://github.com/mpv-player/mpv/issues/4408](https://github.com/mpv-player/mpv/issues/4408)

Thanks, but VDPAU also doesn't work. 'vdapauinfo' gives some reasonable result but mpv (or rather ffmpeg?) reports errors:

[ffmpeg] AVHWFramesContext: Failed to create surface: 2 (resource allocation failed).
[ffmpeg] AVHWFramesContext: Unable to allocate a surface from internal buffer pool.

---

### Post by monkeybrain20122 on 2021-11-17
Ubuntu and mpv versions? Adm doesn't do vdpau unless you install libvdpau-va-gl but it is not needed since mpv should work with vaapi.

---

### Post by bomc68000 on 2021-11-17
> **monkeybrain20122 said:**
> Ubuntu and mpv versions? Adm doesn't do vdpau unless you install libvdpau-va-gl but it is not needed since mpv should work with vaapi.

Ubuntu 20.04.3 LTS

mpv 0.34.0 Copyright © 2000-2021 mpv/MPlayer/mplayer2 projects
 built on Sun Nov 14 19:37:55 UTC 2021
FFmpeg library versions:
   libavutil       56.70.100
   libavcodec      58.134.100
   libavformat     58.76.100
   libswscale      5.9.100
   libavfilter     7.110.100
   libswresample   3.9.100
FFmpeg version: 4.4.1

---

### Post by monkeybrain20122 on 2021-11-17
Did you build mpv and ffmpeg yourself? Or is it a snap?

---

### Post by bomc68000 on 2021-11-17
> **monkeybrain20122 said:**
> Did you build mpv and ffmpeg yourself? Or is it a snap?

I've installed mpv from a deb package downloaded from [https://non-gnu.uvt.nl/debian](https://non-gnu.uvt.nl/debian) (it is listed on [https://mpv.io/installation/](https://mpv.io/installation/) web page).
It behaves however (in this regard) exactly as my previous version of mpv (which was installed by default while installing Ubuntu).

---

### Post by monkeybrain20122 on 2021-11-17
I don't know if there is a ffmpeg version mismatch since ffmpeg should be at version 4.1 for Ubuntu 20.4 and yours says ffmpeg  4.4.1, Where did you get ffmpeg?

---

### Post by bomc68000 on 2021-11-17
> **monkeybrain20122 said:**
> I don't know if there is a ffmpeg version mismatch since ffmpeg should be at version 4.1 for Ubuntu 20.4 and yours says ffmpeg  4.4.1, Where did you get ffmpeg?

I've read somewhere it is statically linked with this version of mpv. I don't fully understand whats going on. I didn't install it separately.

---

### Post by monkeybrain20122 on 2021-11-17
So  can you check your ffmpeg version (just type ffmpeg in terminal) and then to rule out possibilities, uninstall mpv and reinstall it from [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)
and test?

---

### Post by bomc68000 on 2021-11-17
> **monkeybrain20122 said:**
> So  can you check your ffmpeg version (just type ffmpeg in terminal) and then to rule out possibilities, uninstall mpv and reinstall it from [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)
and test?

Thank you, I will reinstall and test it tomorrow.

Output of ffmpeg:

ffmpeg version 4.2.4-1ubuntu0.1 Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 9 (Ubuntu 9.3.0-10ubuntu2)
  configuration: --prefix=/usr --extra-version=1ubuntu0.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --arch=amd64 --enable-gpl --disable-stripping --enable-avresample --disable-filter=resample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libjack --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librsvg --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-lv2 --enable-omx --enable-openal --enable-opencl --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-nvenc --enable-chromaprint --enable-frei0r --enable-libx264 --enable-shared
  libavutil      56. 31.100 / 56. 31.100
  libavcodec     58. 54.100 / 58. 54.100
  libavformat    58. 29.100 / 58. 29.100
  libavdevice    58.  8.100 / 58.  8.100
  libavfilter     7. 57.100 /  7. 57.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  5.100 /  5.  5.100
  libswresample   3.  5.100 /  3.  5.100
  libpostproc    55.  5.100 / 55.  5.100

---

### Post by monkeybrain20122 on 2021-11-17
When you uninstall mpv makes sure you also do 

```
sudo apt autoremove
```

To remove dependencies installed along with it.

Then we can hopefully find out what the culprit might be.

---

### Post by bomc68000 on 2021-11-18
I have purged mpv (and did 'sudo apt autoremove') and installed mpv from the PPA. 
Absolutely no change in mpv playing a video (the same error messages).
vainfo output seems fine.

mpv --version:

mpv 0.33.0 Copyright © 2000-2020 mpv/MPlayer/mplayer2 projects
 built on Thu Nov 26 06:59:44 UTC 2020
FFmpeg library versions:
   libavutil       56.60.100
   libavcodec      58.112.103
   libavformat     58.64.100
   libswscale      5.8.100
   libavfilter     7.90.100
   libswresample   3.8.100
FFmpeg version: git-2020-11-22-9208b72

For me it seems like the problem is in ffmpeg. But why it can't get hw acceleration working on my system, I have no idea. vainfo sees no problem.
Maybe I should just accept the fact (of no more vaapi hw acceleration).

---

### Post by monkeybrain20122 on 2021-11-18
So what -vo and -hwdec options do you use when invoking mpv (or do you have a config file in ~/.config/mpv)?

---

### Post by bomc68000 on 2021-11-18
> **monkeybrain20122 said:**
> So what -vo and -hwdec options do you use when invoking mpv (or do you have a config file in ~/.config/mpv)?

I use smplayer which sets the flags for mpv as follows: 
--vo=gpu --hwdec=vaapi

I was experimenting a bit with different media files and when I play old movies with low resolution or older codecs (like MPEG4 part2), then there are no error messages. I don't know what factor is that exactly because they both tend to appear simultaneously. On the other hand I see literally no difference in performance and there is no indication that hw decoding is actually used. So there is probably no hw acceleration even in this case.

---

### Post by monkeybrain20122 on 2021-11-18
I don't know anything about amd cards, but maybe you can  try to update the graphic drivers. You are using the open source driver, you can upgrade mesa with this[ ppa]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers"). According to link below:
"This PPA provides updated free graphics drivers X (2D) and table (3D). The update packages provide:    

Vulkan 1.1+    
OpenGL 4.5+ support and new OpenGL extensions 
OpenCL support with libclc support     
Gallium -nine updated     
VDPAU and VAAPI Gallium3D Accelerated Video Drivers"

If you are more adventurous you can try the amdgpu proprietary driver, but it seems that there is no easy "sudo apt install" way to install it, you have to get it from amd. [https://ubunlog.com/en/como-instalar-los-drivers-amd-ati-en-ubuntu-18-04/](https://ubunlog.com/en/como-instalar-los-drivers-amd-ati-en-ubuntu-18-04/)

---

### Post by bomc68000 on 2021-11-18
> **monkeybrain20122 said:**
> I don't know anything about amd cards, but maybe you can  try to update the graphic drivers. You are using the open source driver, you can upgrade mesa with this[ ppa]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers"). According to link below:
"This PPA provides updated free graphics drivers X (2D) and table (3D). The update packages provide:    

Vulkan 1.1+    
OpenGL 4.5+ support and new OpenGL extensions 
OpenCL support with libclc support     
Gallium -nine updated     
VDPAU and VAAPI Gallium3D Accelerated Video Drivers"

If you are more adventurous you can try the amdgpu proprietary driver, but it seems that there is no easy "sudo apt install" way to install it, you have to get it from amd. [https://ubunlog.com/en/como-instalar-los-drivers-amd-ati-en-ubuntu-18-04/](https://ubunlog.com/en/como-instalar-los-drivers-amd-ati-en-ubuntu-18-04/)

Hmmm I'll try to update mesa (and see what happens), but I definitely won't mess with amdgpu proprietary driver. Thanks.

---

### Post by QIII on 2021-11-18
The AMD driver modules are present already in the kernel.  On installation, one of the two open source drivers, radeon and amdgpu, is loaded and used depending on which supports your hardware.  There is nothing more to do.  

Despite the fact that people may want their PPAs and such to be meaningful and relevant, they are not any longer.  amdgpu is the open source driver module created by AMD and radeon is maintained by the community by cards not supported by amdgpu.  The more advanced AMDGPU-PRO capabilities can be added for cards that are supported by amdgpu.  Nothing, again, *nothing*, further is needed.  And yes, the AMDGPU-PRO module is very simple to install if you follow AMD's instructions from their website and not some random blog.

---

### Post by bomc68000 on 2021-11-19
> **QIII said:**
> The AMD driver modules are present already in the kernel.  On installation, one of the two open source drivers, radeon and amdgpu, is loaded and used depending on which supports your hardware.  There is nothing more to do.  

Despite the fact that people may want their PPAs and such to be meaningful and relevant, they are not any longer.  amdgpu is the open source driver module created by AMD and radeon is maintained by the community by cards not supported by amdgpu.  The more advanced AMDGPU-PRO capabilities can be added for cards that are supported by amdgpu.  Nothing, again, *nothing*, further is needed.  And yes, the AMDGPU-PRO module is very simple to install if you follow AMD's instructions from their website and not some random blog.

Thanks, QIII. I was able to bring h/w video decoding back again. It turns out all I had to do is switch to amdgpu module (which is not selected by default for KABINI chipset in my A6-5200), I don't know actually why, since it should theoretically also support video h/w acceleration. The difference in performance is quite noticeable (about 40-50%) and is similar to what I remember.

Do you think I could benefit even more from installing AMDGPU-PRO?

---

