---
title: "How to rotate a .mov file 180 deg"
date: 2015-08-03
forum: Multimedia Software
---

### Post by satimis on 2015-08-03
Hi all,

I tried to flip a .MOV file, to rotate it 180 deg and encountered following problem;

mencoder input.mov -oac copy -ovc lavc -flip -o output.mov```

...
...
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  640x480  24bpp   -nan fps  3521.1 kbps (429.8 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:640x480  fps: -nan  ftime:=  -nan
libavcodec version 54.35.0 (external)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio format 0x4134504d is incompatible with '-oac copy', please try '-oac pcm' instead or use '-fafmttag' to override it.

```

Please advise how to fix the problem.

Thanks

Regards
satimis

---

### Post by SeijiSensei on 2015-08-03
Mencoder is really old and unsupported at this point. Try using ffmpeg instead.  
[http://ubuntuforums.org/showthread.php?t=2289299&p=13332215&viewfull=1#post13332215](http://ubuntuforums.org/showthread.php?t=2289299&p=13332215&viewfull=1#post13332215)

---

### Post by satimis on 2015-08-03
> **SeijiSensei said:**
> Mencoder is really old and unsupported at this point. Try using ffmpeg instead.  
[http://ubuntuforums.org/showthread.php?t=2289299&p=13332215&viewfull=1#post13332215](http://ubuntuforums.org/showthread.php?t=2289299&p=13332215&viewfull=1#post13332215)
Hi,

Thanks for your advice and link.  Performed following steps;

~&#10219; sudo add-apt-repository ppa:mc3man/trusty-media```

K9copy -
Mainly for ripping, as far as encoding there are better apps. If inclined to use for encoding then use mencoder as ffmpeg support is quite limited

For rhythmbox users a wide range of plugins can be found here -
https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins

Abcde -
ck. Suggested in synaptic for add. useful packages
A guide to config is here -
http://www.andrews-corner.org/abcde.html

An excellent  audio recorder is available here -
https://launchpad.net/~osmoma/+archive/audio-recorder

A good blender ppa is here -
*https://launchpad.net/~irie/+archive/blender

To further extend this ppa to libav11 check here -
https://launchpad.net/~mc3man/+archive/ubuntu/testing6

To repeat -
*Please note that if using this ppa I would *not* try upgrading to 14.10/15.04, ect. Do a fresh install instead. The intent here is just for users wishing to stay on 14.04*
If upgrading anyway use ppa-purge first -
sudo ppa-purge  ppa:mc3man/trusty-media

Also note that with apt-get a sudo apt-get dist-upgrade is needed for initial setup & with some package upgrades
 More info: https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmphql1zbhx/secring.gpg' created
gpg: keyring `/tmp/tmphql1zbhx/pubring.gpg' created
gpg: requesting key ED8E640A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmphql1zbhx/trustdb.gpg: trustdb created
gpg: key ED8E640A: public key "Launchpad PPA for Doug McMahon" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

```

~&#10219; sudo apt-get update
~&#10219; sudo apt-get install ffmpeg```

.....
Unpacking libass5:amd64 (0.12.2-1~trusty) ...
Selecting previously unselected package libfdk-aac0:amd64.
Preparing to unpack .../libfdk-aac0_0.1.3.1_amd64.deb ...
Unpacking libfdk-aac0:amd64 (0.1.3.1) ...
Selecting previously unselected package libsoxr0:amd64.
Preparing to unpack .../libsoxr0_0.1.1-1_amd64.deb ...
Unpacking libsoxr0:amd64 (0.1.1-1) ...
Selecting previously unselected package libx265-59:amd64.
Preparing to unpack .../libx265-59_1.7-1~trusty_amd64.deb ...
Unpacking libx265-59:amd64 (1.7-1~trusty) ...
Selecting previously unselected package libvidstab1.0.
Preparing to unpack .../libvidstab1.0_2%3a1.0~trusty1.3_amd64.deb ...
Unpacking libvidstab1.0 (2:1.0~trusty1.3) ...
Selecting previously unselected package ffmpeg.
Preparing to unpack .../ffmpeg_7%3a2.7.2+git1~trusty_amd64.deb ...
Unpacking ffmpeg (7:2.7.2+git1~trusty) ...
Setting up libass5:amd64 (0.12.2-1~trusty) ...
Setting up libfdk-aac0:amd64 (0.1.3.1) ...
Setting up libsoxr0:amd64 (0.1.1-1) ...
Setting up libx265-59:amd64 (1.7-1~trusty) ...
Setting up libvidstab1.0 (2:1.0~trusty1.3) ...
Setting up ffmpeg (7:2.7.2+git1~trusty) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...

```

~&#10219; ffmpeg -i input.mov -vf vflip output.MOV ```

....
....
[aac @ 0x2602cc0] Input buffer exhausted before END element found
kB time=00:01:13.44 bitrate= 882.3kbits/frame= 1107 fps= 40 q=27.0 size=    8027kB time=00:01:14.72 bitrate= 880.0kbits/frame= 1124 fps= 39 q=27.0 size=    8119kB time=00:01:15.88 bitrate= 876.5kbits/frame= 1143 fps= 39 q=27.0 size=    8227kB time=00:01:17.11 bitrate= 873.9kbits/frame= 1161 fps= 39 q=27.0 size=    8337kB time=00:01:18.36 bitrate= 871.5kbits/[aac @ 0x2602cc0] Input buffer exhausted before END element found
Error while decoding stream #0:1: Invalid data found when processing input
frame= 1180 fps= 39 q=27.0 size=    8442kB time=00:01:19.24 bitrate= 872.7kbits/frame= 1191 fps= 38 q=-1.0 Lsize=    8875kB time=00:01:19.29 bitrate= 916.8kbits/s dup=0 drop=81    
video:7902kB audio:932kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.466518%
[libx264 @ 0x2614200] frame I:11    Avg QP:19.65  size: 27472
[libx264 @ 0x2614200] frame P:576   Avg QP:23.01  size: 10810
[libx264 @ 0x2614200] frame B:604   Avg QP:25.86  size:  2586
[libx264 @ 0x2614200] consecutive B-frames:  7.4% 66.8% 24.4%  1.3%
[libx264 @ 0x2614200] mb I  I16..4: 22.5% 50.3% 27.2%
[libx264 @ 0x2614200] mb P  I16..4:  2.0%  3.8%  1.3%  P16..4: 51.8% 21.6% 12.3%  0.0%  0.0%    skip: 7.3%
[libx264 @ 0x2614200] mb B  I16..4:  0.1%  0.1%  0.0%  B16..8: 51.9%  5.6%  1.0%  direct: 3.0%  skip:38.3%  L0:41.1% L1:52.4% BI: 6.5%
[libx264 @ 0x2614200] 8x8 transform intra:52.5% inter:60.7%
[libx264 @ 0x2614200] coded y,uvDC,uvAC intra: 69.9% 86.2% 60.8% inter: 27.2% 44.6% 12.7%
[libx264 @ 0x2614200] i16 v,h,dc,p: 16% 25% 25% 34%
[libx264 @ 0x2614200] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 17% 20% 24%  5%  7%  6%  8%  5%  8%
[libx264 @ 0x2614200] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 21% 27% 20%  5%  6%  5%  5%  4%  5%
[libx264 @ 0x2614200] i8c dc,h,v,p: 56% 22% 16%  6%
[libx264 @ 0x2614200] Weighted P-Frames: Y:11.3% UV:6.1%
[libx264 @ 0x2614200] ref P L0: 63.7% 14.2% 15.4%  6.3%  0.3%
[libx264 @ 0x2614200] ref B L0: 88.2% 11.0%  0.9%
[libx264 @ 0x2614200] ref B L1: 96.2%  3.8%
[libx264 @ 0x2614200] kb/s:815.16

```

Very strange, the output file is not rotated 180deg

Regards
satimis

---

### Post by SeijiSensei on 2015-08-03
Some of the suggestions in that stackoverflow link I included referenced the "transpose" command which does 90 degree rotations.  Apparently you can achieve 180 degree rotations with 
```
ffmpeg -vf "transpose=2,transpose=2" -i input.mov output.mov
```
Maybe you can give that a try?

---

### Post by satimis on 2015-08-03
> **SeijiSensei said:**
> Some of the suggestions in that stackoverflow link I included referenced the "transpose" command which does 90 degree rotations.  Apparently you can achieve 180 degree rotations with 
```
ffmpeg -vf "transpose=2,transpose=2" -i input.mov output.mov
```
Maybe you can give that a try?

&#10219; ffmpeg -vf "transpose=2,transpose=2" -i IMG_0667.MOV IMG_0667_vflip.MOV ```

....
....
Option vf (set video filters) cannot be applied to input file IMG_0667.MOV -- you are trying to apply an input option to an output file or vice versa. Move this option before the file it belongs to.
Error parsing options for input file IMG_0667.MOV.
Error opening input files: Invalid argument

```
Still failed

satimis

---

### Post by mc4man on 2015-08-03
> **satimis said:**
> &#10219; ffmpeg -vf "transpose=2,transpose=2" -i IMG_0667.MOV IMG_0667_vflip.MOV ```

....
....
Option vf (set video filters) cannot be applied to input file IMG_0667.MOV -- you are trying to apply an input option to an output file or vice versa. Move this option before the file it belongs to.
Error parsing options for input file IMG_0667.MOV.
Error opening input files: Invalid argument

```
Still failed

satimis
Well just fix your command,  ffmpeg -i input.mov -vf  "transpose=2,transpose=2"  output.mov

It's also possible that .mov can just have the metadata changed, no reencoding. (.mp4 can, don't think .mkv can
> ffmpeg -i input.mov -c copy -metadata:s:v:0 rotate=180 output.mov

---

### Post by FakeOutdoorsman on 2015-08-03
[Download](http://ffmpeg.org/download.html) a recent build, then:
```
ffmpeg -i input -c:a copy output.mp4
```
ffmpeg will automatically rotate if there is rotation metadata (refer to ffmpeg console output). If not, then use one of the many filters and clear the metadata:
```
ffmpeg -i input -vf "hflip,vflip" -metadata:s:v rotate=0 -c:a copy output.mp4
```
Or simply rotate upon playback. ffplay will auto-rotate if there is metadata. VLC will also let you rotate however you like, and probably any other player worth using.

---

### Post by satimis on 2015-08-03
> **mc4man said:**
> Well just fix your command,  ffmpeg -i input.mov -vf  "transpose=2,transpose=2"  output.mov

It's also possible that .mov can just have the metadata changed, no reencoding. (.mp4 can, don't think .mkv can

&#10219; ffmpeg -i IMG_0667.MOV -vf "transpose=2,transpose=2" IMG_0667_vflip.MOV ```

...
[aac @ 0x3248cc0] Input buffer exhausted before END element found
Error while decoding stream #0:1: Invalid data found when processing input
....

```
The output file is not rotated 180deg, same as original file


&#10219; ffmpeg -i IMG_0667.MOV -c copy -metadata:s:v:0 rotate=180 IMG_0667_vflip.MOV```

....
[mov @ 0x3557dc0] Codec for stream 0 does not use global headers but container format requires global headers
[mov @ 0x3557dc0] Codec for stream 1 does not use global headers but container format requires global headers
....

```
The output file is still not rotated 180deg, same as original file

satimis

---

### Post by satimis on 2015-08-03
> **FakeOutdoorsman said:**
> [Download](http://ffmpeg.org/download.html) a recent build, then:
Whether you meant "uninstall ffmpeg" (it was installed on repo) and reinstall it from the download tarball?

> 
```
ffmpeg -i input -c:a copy output.mp4
```
ffmpeg will automatically rotate if there is rotation metadata (refer to ffmpeg console output). If not, then use one of the many filters and clear the metadata:
```
ffmpeg -i input -vf "hflip,vflip" -metadata:s:v rotate=0 -c:a copy output.mp4
```

The input file is .mov.  Will it be automatically converted to .mp4 on the output file?

> 
Or simply rotate upon playback. ffplay will auto-rotate if there is metadata. VLC will also let you rotate however you like, and probably any other player worth using.
On terminal run;
&#10219; /usr/bin/ffplay IMG_0667.MOV 

It is very strange.  I don't need to rotate it 180deg.  If right-click the file -> Open With Videos.  The video is upside down.

satimis

---

### Post by FakeOutdoorsman on 2015-08-03
> **satimis said:**
> Whether you meant "uninstall ffmpeg" (it was installed on repo) and reinstall it from the download tarball?
You can have both the repo ffmpeg and the downloaded one. You just need to properly execute the desired binary. One method is to provide the full path to the binary (/home/satimis/ffmpeg -i ...).

> **satimis said:**
> The input file is .mov.  Will it be automatically converted to .mp4 on the output file?
Yes, if you use .mp4 as output file name. You can use .mov if you prefer, instead.

> **satimis said:**
> It is very strange.  I don't need to rotate it 180deg.  If right-click the file -> Open With Videos.  The video is upside down.
Can you provide the file? If not, then provide the complete console output of:
```
ffmpeg -i input.mov
```
...preferably using the most recent downloaded build.

---

### Post by satimis on 2015-08-03
> **FakeOutdoorsman said:**
>  - snip -

Can you provide the file? If not, then provide the complete console output of:
```
ffmpeg -i input.mov
```
- snip - 
&#10219; ffmpeg -i IMG_0667.MOV ```

ffmpeg version N-74248-g107026e Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libdcadec --enable-libfreetype --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvo-aacenc --enable-libvidstab
  libavutil      54. 30.100 / 54. 30.100
  libavcodec     56. 56.101 / 56. 56.101
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 32.100 /  5. 32.100
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'IMG_0667.MOV':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2015-07-14 10:56:55
    model           : iPhone 3GS
    model-eng       : iPhone 3GS
    date            : 2015-07-14T18:56:55+0800
    date-eng        : 2015-07-14T18:56:55+0800
    encoder         : 3.1.2
    encoder-eng     : 3.1.2
    location        : +22.3373+114.1533/
    location-eng    : +22.3373+114.1533/
    make            : Apple
    make-eng        : Apple
  Duration: 00:01:19.25, start: 0.000023, bitrate: 3593 kb/s
    Stream #0:0(und): Video: h264 (Baseline) (avc1 / 0x31637661), yuv420p(tv, smpte170m/smpte170m/bt709), 640x480, 3521 kb/s, 16.04 fps, 15 tbr, 600 tbn, 1200 tbc (default)
    Metadata:
      rotate          : 180
      creation_time   : 2015-07-14 10:56:55
      handler_name    : Core Media Data Handler
      encoder         : H.264
    Side data:
      displaymatrix: rotation of -180.00 degrees
    Stream #0:1(und): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, mono, fltp, 63 kb/s (default)
    Metadata:
      creation_time   : 2015-07-14 10:56:55
      handler_name    : Core Media Data Handler
At least one output file must be specified

```
Command closed.

Other advice noted and thank.  The .MOV file exceeds 35M

satimis

---

### Post by satimis on 2015-08-03
I have the .MOV file rotated twice (90deg -> 90deg) online and saved as .mp4 file.  It can be right-clicked -> "Open With Video" without the problem of being automatically rotated 180deg.

On Terminal

&#10219; ffmpeg -i IMG_0667_180_rotated.mp4 ```

ffmpeg version N-74248-g107026e Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libdcadec --enable-libfreetype --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvo-aacenc --enable-libvidstab
  libavutil      54. 30.100 / 54. 30.100
  libavcodec     56. 56.101 / 56. 56.101
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 32.100 /  5. 32.100
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'IMG_0667_180_rotated.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    date            : 2015-07-14T18:56:55+0800
    encoder         : Lavf56.4.101
  Duration: 00:01:19.53, start: 0.000000, bitrate: 1010 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 640x480, 878 kb/s, 15 fps, 15 tbr, 15360 tbn, 30 tbc (default)
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: aac (LC) (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 127 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
At least one output file must be specified

```

satimis

---

### Post by FakeOutdoorsman on 2015-08-04
The problem is that some players will utilize the rotation metadata and others won't. What is your end goal for these videos? Personally, I probably wouldn't do anything to them and just use a sane player, but of course it depends on what you want to do, intended audience/playback devices, etc.

---

### Post by satimis on 2015-08-04
> **FakeOutdoorsman said:**
> - snip -
What is your end goal for these videos? - snip - 
Thanks for your advice.

Just for curiosity.

satimis

---

