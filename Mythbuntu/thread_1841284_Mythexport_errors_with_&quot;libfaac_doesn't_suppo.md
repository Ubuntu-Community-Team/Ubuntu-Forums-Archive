---
title: "Mythexport errors with &quot;libfaac doesn't support this output format!&quot;"
date: 2011-09-09
forum: Mythbuntu
---

### Post by ransae on 2011-09-09
I'm running my mythbuntu backend on a Lucid server. (10.04.3). Myth version 0.24.1

It all works well. However, I've had problems getting mythexport to work.

When I first  tried it, I got video with no sound. After a bit of reading, I installed the Medibuntu repository.

Since then, it completes the first pass and fails on the second, with the following log entry: 

```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:59:37, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpegts, from '/mythtv/recordings/1012_20110906212800.mpg':
  Duration: 00:42:55.13, start: 30242.840300, bitrate: 5371 kb/s
  Program 1 
    Stream #0.0[0x204]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 9000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x2a9](eng): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
Output #0, ipod, to '/data/sabnzb/ELEVEN-Wilfred-Doubt-20110906212800.m4v':
    Stream #0.0: Video: libx264, yuv420p, 800x480 [PAR 16:15 DAR 16:9], q=10-51, pass 2, 1500 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: libfaac, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x253ba90]using SAR=16/15
[libx264 @ 0x253ba90]using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x253ba90]profile Baseline, level 3.0
[libfaac @ 0x2559f30]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
```A problem with incompatible libraries?

Have researched. This is a pretty common problem ... one that I can't fix.

Any ideas?

---

### Post by andrew.46 on 2011-09-09
I am not familiar with Mythexport but if there is a place to put in some extra settings to pass to FFmpeg perhaps you could add *-ar 44100* to the settings for the output file. That is a pretty old version of FFmpeg btw but perhaps you are stuck with this?

---

### Post by ransae on 2011-09-09
Thanks, Andrew. It worked! 

I'm not sure why as the man page says that setting is a default value, however, I've got video *and* sound now.

---

### Post by andrew.46 on 2011-09-10
Great news!

---

### Post by s_g_robertson on 2011-12-21
I'm getting almost exactly the same error message.  However adding "-ar 44100" as suggested doesn't seem to help me.

Does anyone have any suggestions?
Thanks
Stephen


```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep 16 2011 17:04:18, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpegts, from '/media/disk/Recordings/1071_20111220132800.mpg':
  Duration: 00:13:58.02, start: 18065.152689, bitrate: 4200 kb/s
  Program 1 
    Stream #0.0[0x191]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x192](eng): Audio: mp2, 48000 Hz, stereo, s16, 256 kb/s
    Stream #0.2[0x196](eng): Audio: mp3, 0 channels, s16
    Stream #0.3[0x195](eng): Subtitle: dvbsub
Output #0, ipod, to '/var/lib/mythtv/mythexport/CBeebies-Raa_Raa_the_Noisy_Lion-Raa_Raa_s_Great_Big_Noise-2.m4v':
    Stream #0.0: Video: libx264, yuv420p, 800x480 [PAR 16:15 DAR 16:9], q=10-51, pass 2, 1500 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: libfaac, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x8712630]using SAR=16/15
[libx264 @ 0x8712630]using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.1 Cache64
[libx264 @ 0x8712630]profile Baseline, level 3.0
[libfaac @ 0x8712cb0]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
```


The content of the Mythexport configuration file is as below.  I have added "-ar 44100" as mentioned earlier in this thread into both the first and second pass parameters.


Ubuntu 10.04
Mythexport version : 2.2.3-0ubuntu1~ppa3

```
Package: libfaac0
Versions:
1.26-0.1ubuntu2 (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: en_GB
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_i18n_Translation-en%5fGB
                  MD5: a58d1daad7eabcd0b98d35635a35d6eb
 Description Language:
                 File: /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-i386_Packages
                  MD5: a58d1daad7eabcd0b98d35635a35d6eb


Reverse Depends:
  libavcodec1d,libfaac0 1.26
  libmyth-0.21-0,libfaac0 1.26
  mplayer-gui,libfaac0 1.26
  mplayer,libfaac0 1.26
  mencoder,libfaac0 1.26
  libavcodec-extra-52,libfaac0 1.26
  libfaac-dev,libfaac0 1.26-0.1ubuntu2
  gstreamer0.10-plugins-bad-multiverse,libfaac0 1.26
  faac,libfaac0 1.26
  avidemux-plugins-common,libfaac0 1.26
Dependencies:
1.26-0.1ubuntu2 - libc6 (2 2.4)
Provides:
1.26-0.1ubuntu2 -
Reverse Provides:

```

```
#!/usr/bin/perl 

package PortableH264HighRes;

use ExportBase;

our @ISA = qw(ExportBase);

my $description = "High Resolution (800x400) Portable H264 Settings.";
my $devices = "High Resolution Android Devices (example Droid, Evo, N1), iPod Touch, iPhone, iPad";
my $notes = "Requires AAC, <a href=\"https://help.ubuntu.com/community/Medibuntu\">activate Medibuntu</a>";
my $version = "1.0";

sub new{
    my $class = shift;
    my $self = $class->SUPER::new(shift, shift, $description, $devices, $notes, $version);
    bless $self, $class;
    return $self;
}

sub export{
    my( $self ) = @_;

    system("ffmpeg -i \'$self->{_inputFile}\' -y -pass 1 -an -vcodec libx264 -ar 44100 -vpre slowfirstpass -vpre ipod640 -b 1500kb -bt 1000kb -threads 0 -s 800x480 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\' && ffmpeg -i \'$self->{_inputFile}\' -y -pass 2 -vcodec libx264 -vpre hq -vpre ipod640 -b 1500kb -bt 1000kb -threads 0 -s 800x480 -acodec libfaac -ab 192kb -ar 44100 -ac 2 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\'");

}
```

---

### Post by andrew.46 on 2011-12-21
I am handicapped more than a little by the fact I know nothing about Mythexport but certainly you need to omit the following change:

```

    system("ffmpeg -i \'$self->{_inputFile}\' -y -pass 1 -an -vcodec libx264 **[COLOR="Red"]-ar 44100[/COLOR]** -vpre slowfirstpass

```

which FFmpeg may be ignoring anyway, the -an option disables encoding of the audio stream in the first pass. Otherwise I am not completely sure what is happening there.

---

