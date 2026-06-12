---
title: "ffmepeg/avconv cropping issue"
date: 2012-08-18
forum: Multimedia Software
---

### Post by R3M3 on 2012-08-18
I recently updated to 12.04 (from 10.04), and am having issues with transcoding some mpg files. Basically, I want to take a 1280x720, 60fps file and convert it to DVD-compatable format (so 720x480, 30 fps)

I used to be able to do it with a command like

ffmpeg -i in.mpg -cropleft 100 -cropright 100 -target ntsc-dvd -r 29.970 -s 720x480 -aspect 4:3 -map 0:0 -map 0:1 out.mpg

but since ffmpeg has been updated, the -cropleft/-cropright no longer work. (And ffmpeg is deprecated)

I attempted to switch over to avconv and use the new crop filters, but that isn't working

avconv -vf "crop=1080:720,scale=720:480" -i in.mpg -target ntsc-dvd -r 29.970 -s 720x480 -aspect 4:3 -map 0:0 -map 0:1 out.mpg # also tried with ffmpeg - same thing

The problem is that there isn't any cropping going on. The output's dvd format, but the picture has been squashed such that everything's skinnier.

What's the simple and obvious thing I'm getting wrong here?

---

### Post by SeijiSensei on 2012-08-18
Why crop at all?  Just set the horizontal width to 720 and let ffmpeg adjust the height automatically.  You'll have black bars top and bottom, but you'll see the entire width of the frame.  Other than shows produced for broadcast TV, where directors are forced to frame scenes to ensure they will look okay in 4:3 resolution, you will lose content by cropping.  I find black bars a minor price to pay for having the entire frame on screen.

---

### Post by qyot27 on 2012-08-18
A) FFmpeg isn't deprecated.  It only says that because of some nasty politics between forks and Ubuntu (well, probably because it inherits from Debian) taking sides with [the fork](http://libav.org/), not [FFmpeg itself](http://ffmpeg.org/).  FFmpeg is very much alive and kicking.

B) Widescreen content should be made anamorphic when being prepared for DVD (anamorphic = 'Enhanced for 16:9 televisions', or similar, on DVD packaging).  The point is that the width is squished to fit inside the 720x480/576 area DVD uses so as to optimally use the allocated bitrate, but it has a 16:9 aspect flag set so that DVD players display it correctly - on 16:9 TVs it would fill the screen as usual, on 4:3 TVs it appears with letterboxing (some players might have pan-and-scan options to do cropping on the fly, or zoom settings you can use to achieve the same thing).

---

### Post by R3M3 on 2012-08-19
Regarding the ffmpeg/avconv fork - I was not aware of that and certainly explains things. Though the distinction doesn't negate my question, as even the ffmpeg command in 12.04 doesn't support the -cropleft/-cropright flags anymore, and shows similar behavior when the new "-vf crop" filter commands are used.

Regarding why I want to crop in the first place, the input video I have was already (from other sources uncontrollable by me) converted 4:3 -> 16:9, so the parts I'm chopping off are just black bars. Converting the video into letterbox format would mean that I would have a 4:3 aspect video, shrunk on screen, with black bars on all four sides.

---

### Post by qyot27 on 2012-08-19
Oh, the source video is pillarboxed.  Then yes, cropping it first and setting as 4:3 makes sense.

Trying it here with a build of mainline FFmpeg, it does a normal 16:9 720p->4:3 480p crop and resize normally, given the following:

```
ffmpeg -i input -vf scale=848:480,crop=640:480 -target ntsc-dvd -r 29.970 -s 720x480 -aspect 4:3 -map 0:0 -map 0:1 out.mpg
```
Essentially, it resizes to 480p, crops to 4:3, and resizes to 720x480, with a 4:3 aspect flag so it looks correct on the DVD.

If the desired output size really is 1080:720, that's a 3:2 ratio.  720x480 is not proper 4:3, it's 3:2.  With the aspect flag, the slightly wider resolution is then squished a bit because it thinks it needs to be 640x480 (which is proper 4:3).  The reasoning for this is because on old analog TVs, the pixels aren't square like a computer monitor's are.

---

### Post by R3M3 on 2012-08-20
Thanks, that seems to be working. (With the version of ffmpeg installed on my computer, which is listed as 0.8.3, copyright Libav developers)

The 1080 isn't anything significant. What I want to do is take the 1280x720 16:9 input file, and transfer it down to a DVD-compatible format by trimming off the black bars on the left and right side. My original approach was to crop off enough of the left and right so that the video had the correct proportions, and then scale it down. 1080 is to 720 as 720 is to 480, so that was where the 1080 comes from. (As an aside, where does the 848 in your example command come from?) The crop-then-scale approach was so the scaler was dealing with small, whole number ratios, hopefully lessening scaling artifacts. (Looking at the logging output, it seems that for some reason it's doing a 1280x720->720x480 rescaling, then doing the -vf scale and crop. Changing the -vf to be before the -i flag doesn't seem to change anything.)

Stupidly of me, I didn't realize that 720x480 wasn't 4:3. I guess I'm not sure if I want/need the 4:3 or not. What exactly does the "-aspect 4:3" do, and do I need it for (non 16:9) DVD-compatible encoding? Will things play back appropriately if it isn't set?

Thanks.

---

### Post by qyot27 on 2012-08-21
I'm about to get into a bit of technical theory here, and while I've tried to explain as much as I possibly can, it may come off sounding like I'm repeating myself a lot.

> **R3M3 said:**
> The 1080 isn't anything significant. What I want to do is take the 1280x720 16:9 input file, and transfer it down to a DVD-compatible format by trimming off the black bars on the left and right side. My original approach was to crop off enough of the left and right so that the video had the correct proportions, and then scale it down. 1080 is to 720 as 720 is to 480, so that was where the 1080 comes from.
It's true, of course, that 1080x720 is the same ratio as 720x480, but on a DVD there's a disconnect between stored resolution and actual aspect ratio, regardless of being 16:9 or 4:3.  To crop to actual 4:3, you'd actually want 960x720.

Basically, to make it look right, you'd crop off whatever is on the sides, proportionally scale the result down to 480 pixels in height, and then it can get a little hairy if it doesn't scale to exactly 640x480.  If the width is larger than 640, then you can proportionally scale the width to 640 and just letterbox the remaining height.  Or you could crop the excess so it's exactly 640x480.  If the width is less than 640, then you'd either pillarbox it again slightly, or crop the excess off the height after resizing it proportionally to 640 width.

This is all assuming the ratio of the original was correct.  An easy way of telling whether this is the case is to find something in the image that you know is supposed to be a circle (the moon is a really easy one if it's there, but any sort of circle works) - if it's still a circle, you're good.  If it's starting to look like an oval, there's distortion happening.

> (As an aside, where does the 848 in your example command come from?)
It's the closest mod16 resolution to actual 16:9 480p.  Technically, 16:9 480p is 853.3repeating x 480.  But there's a historical tendency to make sure that resolutions for lossy codecs are in mod16, resulting in choosing between 848x480 or 864x480.  848x480 is closer, so it results in less distortion.

This is less of an issue with formats like H.264 (and arguably MPEG-2) or display standards like 1080p, as you'll note that 1080 is not mod16.  But it's still true that you can't store fractional pixels, so you have to round anyway (like to 852x480, which is mod4 and mod6).

> Stupidly of me, I didn't realize that 720x480 wasn't 4:3. I guess I'm not sure if I want/need the 4:3 or not. What exactly does the "-aspect 4:3" do, and do I need it for (non 16:9) DVD-compatible encoding? Will things play back appropriately if it isn't set?
Yes, you want the 4:3, because DVDs don't allow for square pixel resolutions.  The -aspect 4:3 flag tells the playback software/hardware to interpret 720x480 as if it were 4:3 - in other words, on a computer it would resize it on playback to either 640x480 or 720x544 (mod16 again; for playback only it means less, so it could show up as the actual 720x540 instead).

The reason for seemingly going for *both* 640x480 and 720x480 is that 640x480 **is** 4:3, and it's also in square pixels.  On a computer monitor it will look correct (unless there was something wonky going on, like I noted with the circles/ovals thing).  But since DVD works with non-square pixels, you have to compensate, and resize *from* that square pixel resolution (640x480 for 4:3, 848x480 or thereabouts for 16:9) *to* 720x480, and then set the according aspect flag.  If you were dealing with going from 640x480->720x480 in square pixels, it would look fatter than usual.  But if the 720x480 file has the 4:3 flag set, the player knows to squish it back (or expand it vertically) to its proper size.  This is ultimately why things looked squished when you tried it before - you were making the 720x480 resolution look right with square pixels (I would guess), and then because of the flag, it was squishing it back to real 4:3.  In reality, you need to reverse it - make it look correct at real 4:3/640x480, and then resize to 720x480 and set the flag.

Some of the resizing can be omitted in the actual practice of pre-processing the source if you're already familiar with working with aspect ratios and non-square pixels (it is so much simpler to see this with AviSynth's crop and resizing filters), but it's easier to visualize if you think it through all of the steps.

---

### Post by R3M3 on 2012-08-21
And they say watching TV rots your brain ... ;)

Thanks for the help and explanation.

---

### Post by finlay648 on 2013-01-06
> **qyot27 said:**
> Oh, the source video is pillarboxed.  Then yes, cropping it first and setting as 4:3 makes sense.

Trying it here with a build of mainline FFmpeg, it does a normal 16:9 720p->4:3 480p crop and resize normally, given the following:

```
ffmpeg -i input -vf scale=848:480,crop=640:480 -target ntsc-dvd -r 29.970 -s 720x480 -aspect 4:3 -map 0:0 -map 0:1 out.mpg
```
Essentially, it resizes to 480p, crops to 4:3, and resizes to 720x480, with a 4:3 aspect flag so it looks correct on the DVD.

If the desired output size really is 1080:720, that's a 3:2 ratio.  720x480 is not proper 4:3, it's 3:2.  With the aspect flag, the slightly wider resolution is then squished a bit because it thinks it needs to be 640x480 (which is proper 4:3).  The reasoning for this is because on old analog TVs, the pixels aren't square like a computer monitor's are.

Looking at the output of this command (using ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1), it seems that it first scales the 1280x720 to 720x480. Then it scales the 720x480 to 848x480. And then it crops the 848x480 to 640x480.

```
[scale @ 0x100a5e0] w:1280 h:720 fmt:yuv420p -> w:720 h:480 fmt:yuv420p flags:0x4
[scale @ 0x100a6c0] w:720 h:480 fmt:yuv420p -> w:848 h:480 fmt:yuv420p flags:0x4
[crop @ 0x1020140] w:848 h:480 -> w:640 h:480
```


Is there a command line that just crops the 1280x720 to 960x720 and then scales that to 720x480 with an aspect ratio of 4:3?

---

### Post by qyot27 on 2013-01-08
> **finlay648 said:**
> Looking at the output of this command (using ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1), it seems that it first scales the 1280x720 to 720x480. Then it scales the 720x480 to 848x480. And then it crops the 848x480 to 640x480.

```
[scale @ 0x100a5e0] w:1280 h:720 fmt:yuv420p -> w:720 h:480 fmt:yuv420p flags:0x4
[scale @ 0x100a6c0] w:720 h:480 fmt:yuv420p -> w:848 h:480 fmt:yuv420p flags:0x4
[crop @ 0x1020140] w:848 h:480 -> w:640 h:480
```


Is there a command line that just crops the 1280x720 to 960x720 and then scales that to 720x480 with an aspect ratio of 4:3?
You probably just don't see the extra stuff it's doing because you don't have full verbosity enabled.

Despite the fact this is a MinGW build and not a native one, the crop/resize functions should be the same.  It's also really **ffmpeg**, not the 'ffmpeg' in the repositories that's just sitting atop the fork, and it's from git rather than a point release.

```
ffmpeg -v 9 -loglevel 99 -i "[AKROSS_Con_2012]_AimoAio_-_Aevum_alt.mp4" -vf scale=848:480,crop=640:480 -target ntsc-dvd -r 29.970 -s 720x480 -aspect 4:3 -map 0:0 -map 0:1 out.mpg
ffmpeg version r47113 git-ec51b33 Copyright (c) 2000-2012 the FFmpeg developers
  built on Nov 26 2012 17:25:00 with gcc 4.7.2 (GCC)
  configuration: --prefix=/home/qyot27/win32_build --cross-prefix=i686-w64-mingw32- --enable-gpl --enable-version3 --disable-w32threads --enable-memalign-hack --enable-libutvideo --enable-libxvid --enable-libtwolame --enable-libmp3lame --enable-libvorbis --enable-libopus --enable-libvo-aacenc --enable-libvpx --enable-libtheora --enable-avisynth --cpu=pentium3 --extra-cflags='-march=pentium3 -mtune=pentium3 -DPTW32_STATIC_LIB' --target-os=mingw32 --arch=x86
  libavutil      52.  9.102 / 52.  9.102
  libavcodec     54. 77.100 / 54. 77.100
  libavformat    54. 37.100 / 54. 37.100
  libavdevice    54.  3.100 / 54.  3.100
  libavfilter     3. 23.102 /  3. 23.102
  libswscale      2.  1.102 /  2.  1.102
  libswresample   0. 17.101 /  0. 17.101
  libpostproc    52.  2.100 / 52.  2.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] Format mov,mp4,m4a,3gp,3g2,mj2 probed with size=2048 and score=100
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] ISO: File Type Major Brand: isom
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] File position before avformat_find_stream_info() is 115351278
[h264 @ 01ebdb20] Using externally provided dimensions
[h264 @ 01ebdb20] no picture
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] All info found
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] File position after avformat_find_stream_info() is 115453
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '[AKROSS_Con_2012]_AimoAio_-_Aevum_alt.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    creation_time   : 2012-12-13 13:52:45
    artist          : AimoAio
    title           : Aevum
    encoder         : AMVsimple GUI 3.5_deluxe
  Duration: 00:04:08.06, start: 0.000000, bitrate: 3720 kb/s
    Stream #0:0(und), 12, 1/24000: Video: h264 (High) (avc1 / 0x31637661), yuv420p, 1280x720, 1001/48000, 3391 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 47.95 tbc
    Metadata:
      creation_time   : 2012-12-13 12:44:55
      handler_name    : GPAC ISO Video Handler
    Stream #0:1(und), 1, 1/48000: Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 325 kb/s
    Metadata:
      creation_time   : 2012-12-13 13:52:58
      handler_name    : GPAC ISO Audio Handler
[scale @ 01fbd800] Setting 'w' to value '848'
[scale @ 01fbd800] Setting 'h' to value '480'
[scale @ 01fbd800] Setting 'flags' to value '0x4'
[Parsed_scale_0 @ 021b32c0] w:848 h:480 flags:'0x4' interl:0
[buffer @ 01fa7d60] Setting entry with key 'video_size' to value '1280x720'
[buffer @ 01fa7d60] Setting entry with key 'pix_fmt' to value '0'
[buffer @ 01fa7d60] Setting entry with key 'time_base' to value '1/24000'
[buffer @ 01fa7d60] Setting entry with key 'pixel_aspect' to value '0/1'
[buffer @ 01fa7d60] Setting entry with key 'sws_param' to value 'flags=2'
[buffer @ 01fa7d60] Setting entry with key 'frame_rate' to value '24000/1001'
[graph 0 input from stream 0:0 @ 01fa7ca0] w:1280 h:720 pixfmt:yuv420p tb:1/24000 fr:24000/1001 sar:0/1 sws_param:flags=2
[scale @ 01ebc6c0] Setting 'w' to value '720'
[scale @ 01ebc6c0] Setting 'h' to value '480'
[scale @ 01ebc6c0] Setting 'flags' to value '0x4'
[scaler for output stream 0:0 @ 021b3880] w:720 h:480 flags:'0x4' interl:0
[Parsed_scale_0 @ 021b32c0] w:1280 h:720 fmt:yuv420p sar:0/1 -> w:848 h:480 fmt:
yuv420p sar:0/1 flags:0x4
[Parsed_crop_1 @ 01fa7ac0] w:848 h:480 sar:0/1 -> w:640 h:480 sar:0/1
[scaler for output stream 0:0 @ 021b3880] w:640 h:480 fmt:yuv420p sar:0/1 -> w:720 h:480 fmt:yuv420p sar:0/1 flags:0x4
[abuffer @ 01ebc640] Setting entry with key 'time_base' to value '1/48000'
[abuffer @ 01ebc640] Setting entry with key 'sample_rate' to value '48000'
[abuffer @ 01ebc640] Setting entry with key 'sample_fmt' to value 'fltp'
[abuffer @ 01ebc640] Setting entry with key 'channel_layout' to value '0x3'
[graph 1 input from stream 0:1 @ 0211bfa0] tb:1/48000 samplefmt:fltp samplerate:48000 chlayout:0x3
[aformat @ 020f5e80] Setting entry with key 'sample_fmts' to value 'fltp'
[aformat @ 020f5e80] Setting entry with key 'sample_rates' to value '48000'
[aformat @ 020f5e80] Setting entry with key 'channel_layouts' to value '0x4,0x3,
0x103,0x7,0x603,0x33,0x107,0x607,0x37,0xc,0xb,0x10b,0xf,0x60b,0x3b,0x10f,0x60f,0x3f'
[mpeg2video @ 01fe66a0] detected 1 logical cores
[mpeg2video @ 01fe66a0] intra_quant_bias = 96 inter_quant_bias = 0
[h264 @ 01ebdb20] detected 1 logical cores
```
Taking note of the actual crop and resize operations:
```
[scale @ 01fbd800] Setting 'w' to value '848'
[scale @ 01fbd800] Setting 'h' to value '480'
[scale @ 01fbd800] Setting 'flags' to value '0x4'
[Parsed_scale_0 @ 021b32c0] w:848 h:480 flags:'0x4' interl:0
...
[graph 0 input from stream 0:0 @ 01fa7ca0] w:1280 h:720 pixfmt:yuv420p tb:1/24000 fr:24000/1001 sar:0/1 sws_param:flags=2
[scale @ 01ebc6c0] Setting 'w' to value '720'
[scale @ 01ebc6c0] Setting 'h' to value '480'
[scale @ 01ebc6c0] Setting 'flags' to value '0x4'
[scaler for output stream 0:0 @ 021b3880] w:720 h:480 flags:'0x4' interl:0
[Parsed_scale_0 @ 021b32c0] w:1280 h:720 fmt:yuv420p sar:0/1 -> w:848 h:480 fmt:
yuv420p sar:0/1 flags:0x4
[Parsed_crop_1 @ 01fa7ac0] w:848 h:480 sar:0/1 -> w:640 h:480 sar:0/1
[scaler for output stream 0:0 @ 021b3880] w:640 h:480 fmt:yuv420p sar:0/1 -> w:720 h:480 fmt:yuv420p sar:0/1 flags:0x4
```
The parsed_scale and parsed_crop illustrate that it is doing it in the right order.


But in any case, the corresponding crop/scale command would be:
```
-vf crop=960:720,scale=720:480
```
and you'd leave out the '-s 720x480', although that's probably harmless.

---

### Post by finlay648 on 2013-01-08
> **qyot27 said:**
> You probably just don't see the extra stuff it's doing because you don't have full verbosity enabled.

Despite the fact this is a MinGW build and not a native one, the crop/resize functions should be the same.  It's also really **ffmpeg**, not the 'ffmpeg' in the repositories that's just sitting atop the fork, and it's from git rather than a point release.

```
ffmpeg -v 9 -loglevel 99 -i "[AKROSS_Con_2012]_AimoAio_-_Aevum_alt.mp4" -vf scale=848:480,crop=640:480 -target ntsc-dvd -r 29.970 -s 720x480 -aspect 4:3 -map 0:0 -map 0:1 out.mpg
ffmpeg version r47113 git-ec51b33 Copyright (c) 2000-2012 the FFmpeg developers
  built on Nov 26 2012 17:25:00 with gcc 4.7.2 (GCC)
  configuration: --prefix=/home/qyot27/win32_build --cross-prefix=i686-w64-mingw32- --enable-gpl --enable-version3 --disable-w32threads --enable-memalign-hack --enable-libutvideo --enable-libxvid --enable-libtwolame --enable-libmp3lame --enable-libvorbis --enable-libopus --enable-libvo-aacenc --enable-libvpx --enable-libtheora --enable-avisynth --cpu=pentium3 --extra-cflags='-march=pentium3 -mtune=pentium3 -DPTW32_STATIC_LIB' --target-os=mingw32 --arch=x86
  libavutil      52.  9.102 / 52.  9.102
  libavcodec     54. 77.100 / 54. 77.100
  libavformat    54. 37.100 / 54. 37.100
  libavdevice    54.  3.100 / 54.  3.100
  libavfilter     3. 23.102 /  3. 23.102
  libswscale      2.  1.102 /  2.  1.102
  libswresample   0. 17.101 /  0. 17.101
  libpostproc    52.  2.100 / 52.  2.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] Format mov,mp4,m4a,3gp,3g2,mj2 probed with size=2048 and score=100
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] ISO: File Type Major Brand: isom
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] File position before avformat_find_stream_info() is 115351278
[h264 @ 01ebdb20] Using externally provided dimensions
[h264 @ 01ebdb20] no picture
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] All info found
[mov,mp4,m4a,3gp,3g2,mj2 @ 01ebcfa0] File position after avformat_find_stream_info() is 115453
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '[AKROSS_Con_2012]_AimoAio_-_Aevum_alt.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    creation_time   : 2012-12-13 13:52:45
    artist          : AimoAio
    title           : Aevum
    encoder         : AMVsimple GUI 3.5_deluxe
  Duration: 00:04:08.06, start: 0.000000, bitrate: 3720 kb/s
    Stream #0:0(und), 12, 1/24000: Video: h264 (High) (avc1 / 0x31637661), yuv420p, 1280x720, 1001/48000, 3391 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 47.95 tbc
    Metadata:
      creation_time   : 2012-12-13 12:44:55
      handler_name    : GPAC ISO Video Handler
    Stream #0:1(und), 1, 1/48000: Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 325 kb/s
    Metadata:
      creation_time   : 2012-12-13 13:52:58
      handler_name    : GPAC ISO Audio Handler
[scale @ 01fbd800] Setting 'w' to value '848'
[scale @ 01fbd800] Setting 'h' to value '480'
[scale @ 01fbd800] Setting 'flags' to value '0x4'
[Parsed_scale_0 @ 021b32c0] w:848 h:480 flags:'0x4' interl:0
[buffer @ 01fa7d60] Setting entry with key 'video_size' to value '1280x720'
[buffer @ 01fa7d60] Setting entry with key 'pix_fmt' to value '0'
[buffer @ 01fa7d60] Setting entry with key 'time_base' to value '1/24000'
[buffer @ 01fa7d60] Setting entry with key 'pixel_aspect' to value '0/1'
[buffer @ 01fa7d60] Setting entry with key 'sws_param' to value 'flags=2'
[buffer @ 01fa7d60] Setting entry with key 'frame_rate' to value '24000/1001'
[graph 0 input from stream 0:0 @ 01fa7ca0] w:1280 h:720 pixfmt:yuv420p tb:1/24000 fr:24000/1001 sar:0/1 sws_param:flags=2
[scale @ 01ebc6c0] Setting 'w' to value '720'
[scale @ 01ebc6c0] Setting 'h' to value '480'
[scale @ 01ebc6c0] Setting 'flags' to value '0x4'
[scaler for output stream 0:0 @ 021b3880] w:720 h:480 flags:'0x4' interl:0
[Parsed_scale_0 @ 021b32c0] w:1280 h:720 fmt:yuv420p sar:0/1 -> w:848 h:480 fmt:
yuv420p sar:0/1 flags:0x4
[Parsed_crop_1 @ 01fa7ac0] w:848 h:480 sar:0/1 -> w:640 h:480 sar:0/1
[scaler for output stream 0:0 @ 021b3880] w:640 h:480 fmt:yuv420p sar:0/1 -> w:720 h:480 fmt:yuv420p sar:0/1 flags:0x4
[abuffer @ 01ebc640] Setting entry with key 'time_base' to value '1/48000'
[abuffer @ 01ebc640] Setting entry with key 'sample_rate' to value '48000'
[abuffer @ 01ebc640] Setting entry with key 'sample_fmt' to value 'fltp'
[abuffer @ 01ebc640] Setting entry with key 'channel_layout' to value '0x3'
[graph 1 input from stream 0:1 @ 0211bfa0] tb:1/48000 samplefmt:fltp samplerate:48000 chlayout:0x3
[aformat @ 020f5e80] Setting entry with key 'sample_fmts' to value 'fltp'
[aformat @ 020f5e80] Setting entry with key 'sample_rates' to value '48000'
[aformat @ 020f5e80] Setting entry with key 'channel_layouts' to value '0x4,0x3,
0x103,0x7,0x603,0x33,0x107,0x607,0x37,0xc,0xb,0x10b,0xf,0x60b,0x3b,0x10f,0x60f,0x3f'
[mpeg2video @ 01fe66a0] detected 1 logical cores
[mpeg2video @ 01fe66a0] intra_quant_bias = 96 inter_quant_bias = 0
[h264 @ 01ebdb20] detected 1 logical cores
```
Taking note of the actual crop and resize operations:
```
[scale @ 01fbd800] Setting 'w' to value '848'
[scale @ 01fbd800] Setting 'h' to value '480'
[scale @ 01fbd800] Setting 'flags' to value '0x4'
[Parsed_scale_0 @ 021b32c0] w:848 h:480 flags:'0x4' interl:0
...
[graph 0 input from stream 0:0 @ 01fa7ca0] w:1280 h:720 pixfmt:yuv420p tb:1/24000 fr:24000/1001 sar:0/1 sws_param:flags=2
[scale @ 01ebc6c0] Setting 'w' to value '720'
[scale @ 01ebc6c0] Setting 'h' to value '480'
[scale @ 01ebc6c0] Setting 'flags' to value '0x4'
[scaler for output stream 0:0 @ 021b3880] w:720 h:480 flags:'0x4' interl:0
[Parsed_scale_0 @ 021b32c0] w:1280 h:720 fmt:yuv420p sar:0/1 -> w:848 h:480 fmt:
yuv420p sar:0/1 flags:0x4
[Parsed_crop_1 @ 01fa7ac0] w:848 h:480 sar:0/1 -> w:640 h:480 sar:0/1
[scaler for output stream 0:0 @ 021b3880] w:640 h:480 fmt:yuv420p sar:0/1 -> w:720 h:480 fmt:yuv420p sar:0/1 flags:0x4
```
The parsed_scale and parsed_crop illustrate that it is doing it in the right order.


But in any case, the corresponding crop/scale command would be:
```
-vf crop=960:720,scale=720:480
```
and you'd leave out the '-s 720x480', although that's probably harmless.

That doesn't work for me because it throws an error both with and without the -s 720x480:

```
[buffer @ 0x181ecc0] w:1280 h:720 pixfmt:yuv420p
[scale @ 0x17f9600] w:1280 h:720 fmt:yuv420p -> w:720 h:480 fmt:yuv420p flags:0x4
[crop @ 0x17f9e40] w:720 h:480 -> w:960 h:720
[crop @ 0x17f9e40] Invalid too big or non positive size for width '960' or height '720'
```

It seems to scale the input to 720x480 first and then tries to crop it to 960x720.

If I add "-s 1280x720" then the "-vf crop=960x720,scale=720x480" filter works as expected.

---

