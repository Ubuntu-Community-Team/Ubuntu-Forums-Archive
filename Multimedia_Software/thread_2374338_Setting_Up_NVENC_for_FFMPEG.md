---
title: "Setting Up NVENC for FFMPEG"
date: 2017-10-14
forum: Multimedia Software
---

### Post by duetschbag on 2017-10-14
I'll start off by saying that I'm a Linux noob but I've been researching and still haven't been able to figure this out. I'm using Ubuntu 16.04 LTS.

I am trying to use NVENC with FFMPEG and can't seem to get past this specific step over at [https://developer.nvidia.com/ffmpeg](https://developer.nvidia.com/ffmpeg).

- Download the latest FFmpeg or libav source code, by cloning the corresponding GIT repositories (**DONE**)
- Download and install the compatible driver from NVIDIA web site (**DONE**)
- Download and install the CUDA Toolkit (**DONE**)
- Use the following configure command (Use correct CUDA library path in config command below) ([COLOR=#ff0000]**STUCK**[/COLOR])

The problem is that it's asking me to run the following command and I don't know where to run it. I know it says use the correct CUDA library path, but I don't know where that is (I just used defaults when installing everything). I also don't know where configure is located.

```
./configure --enable-cuda --enable-cuvid --enable-nvenc --enable-nonfree --enable-libnpp --extra-cflags=-I/usr/local/cuda/include --extra-ldflags=-L/usr/local/cuda/lib64
```

I've even looked at a couple of forum post here but couldn't pull anything out of it that was useful. Again, probably due to the noobishness. 

If anyone can assist, I would greatly appreciate it!

---

### Post by mc4man on 2017-10-14
Basically with any recent ffmpeg source nvenc & cuvid are going to be enabled in a ffmpeg build without you doing or specifying anything
(- the needed parts of the sdk are now in the ffmpeg source.
Ex. - I run a configure on ffmpeg - 
```
.....

Enabled hwaccels:
h263_vaapi		 hevc_vdpau		  mpeg2_cuvid		   mpeg4_vaapi		    vp8_cuvid
h264_cuvid		 mjpeg_cuvid		  mpeg2_vaapi		   mpeg4_vdpau		    vp9_cuvid
h264_vaapi		 mpeg1_cuvid		  mpeg2_vdpau		   vc1_cuvid		    vp9_vaapi
h264_vdpau		 mpeg1_vdpau		  mpeg2_xvmc		   vc1_vaapi		    wmv3_vaapi
hevc_cuvid		 mpeg1_xvmc		  mpeg4_cuvid		   vc1_vdpau		    wmv3_vdpau
hevc_vaapi

.....
```
```
....

Enabled encoders:
a64multi		 dvdsub			  mpeg4			   pcm_u16be		    sunrast
a64multi5		 dvvideo		  msmpeg4v2		   pcm_u16le		    svq1
aac			 eac3			  msmpeg4v3		   pcm_u24be		    targa
ac3			 ffv1			  msvideo1		   pcm_u24le		    text
ac3_fixed		 ffvhuff		  nellymoser		   pcm_u32be		    tiff
adpcm_adx		 flac			  nvenc			   pcm_u32le		    truehd
adpcm_g722		 flashsv		  nvenc_h264		   pcm_u8		    tta
adpcm_g726		 flashsv2		  nvenc_hevc	

.....
```

At this point "--enable-cuda --enable-cuvid --enable-nvenc" are no longer valid configure options for ffmpeg, the current configure options for those are only disable. 
Ex. from ffmpeg's ./configure --help

```
.......
The following libraries provide various hardware acceleration features:
  --disable-audiotoolbox   disable Apple AudioToolbox code [autodetect]
  --disable-cuda           disable dynamically linked Nvidia CUDA code [autodetect]
  --enable-cuda-sdk        enable CUDA features that require the CUDA SDK [no]
  --disable-cuvid          disable Nvidia CUVID support [autodetect]
  --disable-d3d11va        disable Microsoft Direct3D 11 video acceleration code [autodetect]
  --disable-dxva2          disable Microsoft DirectX 9 video acceleration code [autodetect]
  --enable-libmfx          enable Intel MediaSDK (AKA Quick Sync Video) code via libmfx [no]
  --enable-libnpp          enable Nvidia Performance Primitives-based code [no]
  --enable-mmal            enable Broadcom Multi-Media Abstraction Layer (Raspberry Pi) via MMAL [no]
  --disable-nvenc          disable Nvidia video encoding code [autodetect]
......................


```
you'll notice that only cuda-sdk is an enable option (& likely not what you want?

As far as your specific question, - the ./configure is run from the ffmpeg source, i.e. you'd cd to the ffmpeg source in a terminal
(or if using 16.04 or later just right click on the ffmpeg folder > open in terminal.

If you want a prebuilt ffmpeg to try out nvenc let me know,  I'd point you to one of my ppa's for a packaged ffmpeg build.
Or read thru here for build instructions, some steps aren't need, i.e. don't build yasm or nasm, just install them from ubuntu repos

---

### Post by duetschbag on 2017-10-14
Thank you for the quick response! 

So I think this is both good and bad. Good in that I shouldn't need to do anything more in order to use NVENC encoding. Bad in that I clearly don't understand how to use it. lol

To give a better idea of what I am trying to do, I am using NGINX to output multiple livestreams to YouTube, Twitch, ect. When I do this using the CPU for encoding, I use the following line and everything works great. I can open VLC and view the stream on my server and also view the stream on whichever site(s) I am pushing to.

```
exec ffmpeg -i "rtmp://127.0.0.1/live/mylivestreamkey" -vb 6000k -minrate 6000k -maxrate 6000k -bufsize 6000k -s 1600x900 -c:v libx264 -preset veryfast -r 60 -g 120 -keyint_min 60 -x264opts "keyint=60:min-keyint=60:no-scenecut" -sws_flags lanczos -pix_fmt yuv420p -c:a copy -f flv -threads 8 -strict normal "rtmp://127.0.0.1/liveout/mylivestreamkey";
```

I'm trying to encode the same stream on my GPU in order to take some load of off the CPU and also to encode at a slightly lower quality at 30FPS. This is for Facebook live since you can't do more than 720p and 30fps. When I try to view using VLC, it's just a black screen. No error messages surprisingly, but it's not working. Can you take a look below and let me know what I'm doing wrong? Apparently not many people use hardware encoding for this so I've been finding it difficult to get the information I'm looking for.

```
exec ffmpeg -hwaccel cuvid "rtmp://127.0.0.1/live/mylivestreamkey" -vb 4000k -minrate 4000k -maxrate 4000k -bufsize 6000k -s 1280x720 -c:v h264_cuvid -preset veryfast -r 30 -g 60 -keyint_min 30 -x264opts "keyint=60:min-keyint=60:no-scenecut" -sws_flags lanczos -pix_fmt yuv420p -c:a copy -f flv -threads 8 -strict normal "rtmp:127.0.0.1/liveout2/mylivestreamkey";
```

---

### Post by mc4man on 2017-10-14
Let me see if I can track down some encoding examples for ffmpeg with nvenc. Keep in mind cuvid is hardware decoding, not encoding. nvenc is for encoding. 
(- so if searching use nvenc if encoding is what your after. One can use both at the same time but generally not that much gained on the decoding side

edit: you could look here for basic & a little info
[https://trac.ffmpeg.org/wiki/HWAccelIntro](https://trac.ffmpeg.org/wiki/HWAccelIntro)

A bit more here 
[https://gist.github.com/Brainiarc7/4b49f463a08377530df6cecb8171306a](https://gist.github.com/Brainiarc7/4b49f463a08377530df6cecb8171306a)

(- here atm I've just a couple of older nvidia laptops that have minimal nvenc support so never paid much attention..

---

### Post by duetschbag on 2017-10-14
Woooo!!!! You did it!!!! If I could hug you right now, I would!!!! :D 

For anyone else who happens to stumble across this, i'd like to point out the following things:

From the link mc4man posted ([https://trac.ffmpeg.org/wiki/HWAccelIntro](https://trac.ffmpeg.org/wiki/HWAccelIntro)) I found the following command: ```
ffmpeg -h encoder=h264_nvenc
```

The preset I was using (veryfast) doesn't appear to be valid preset for NVENC. So I changed it to slow. The other changes I had to make were in blue. So I kept ffmpeg -i as I had it originally (well, before this post), updated the encoder to h264_nvenc and used the slow preset. See the line below to see what the final result was.

```
exec **[COLOR=#0000ff]ffmpeg -i[/COLOR]** "rtmp://127.0.0.1/live/mylivestreamkey" -vb 4000k -minrate 4000k -maxrate 4000k -bufsize 4000k -s 1280x720 -c:v **[COLOR=#0000ff]h264_nvenc[/COLOR]** -preset [COLOR=#0000ff]**slow **[/COLOR]-r 30 -g 60 -keyint_min 30 -x264opts "keyint=60:min-keyint=60:no-scenecut" -sws_flags lanczos -pix_fmt yuv420p -c:a copy -f flv -threads 8 -strict normal "rtmp:127.0.0.1/liveout2/mylivestreamkey";
```

I have been struggling with this for many many hours. Thank you so much for your posts!

---

