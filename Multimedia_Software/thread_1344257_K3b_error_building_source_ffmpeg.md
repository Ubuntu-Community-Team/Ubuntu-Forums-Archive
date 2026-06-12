---
title: "K3b error building source: ffmpeg"
date: 2009-12-02
forum: Multimedia Software
---

### Post by giorgio.65 on 2009-12-02
Hi there,

I'm a very newby in Linux. I'm trying to compile K3b from source because installing it from repository it miss ripping functions.
Unfortunately it returns an error:

[  0%] Built target k3bdevice_automoc
[  3%] Built target k3bdevice
[  3%] Built target k3b_automoc
[ 44%] Built target k3b
[ 44%] Built target k3b_bin_automoc
[ 92%] Built target k3b_bin
[ 92%] Built target kio_videodvd_automoc
[ 93%] Built target kio_videodvd
[ 93%] Built target k3bwavedecoder_automoc
[ 93%] Built target k3bwavedecoder
[ 93%] Built target k3bffmpegdecoder_automoc
Linking CXX shared module ../../../lib/k3bffmpegdecoder.so
CMakeFiles/k3bffmpegdecoder.dir/k3bffmpegwrapper.o: In function `K3bFFMpegWrapper':
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:350: undefined reference to `av_register_all'
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:350: undefined reference to `av_register_all'
CMakeFiles/k3bffmpegdecoder.dir/k3bffmpegwrapper.o: In function `K3bFFMpegFile::seek(K3b::Msf const&)':
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:337: undefined reference to `av_seek_frame'
CMakeFiles/k3bffmpegdecoder.dir/k3bffmpegwrapper.o: In function `K3bFFMpegFile::readPacket()':
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:271: undefined reference to `av_init_packet'
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:273: undefined reference to `av_read_frame'
CMakeFiles/k3bffmpegdecoder.dir/k3bffmpegwrapper.o: In function `K3bFFMpegFile::close()':
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:152: undefined reference to `av_close_input_file'
CMakeFiles/k3bffmpegdecoder.dir/k3bffmpegwrapper.o: In function `K3bFFMpegFile::open()':
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:81: undefined reference to `av_open_input_file'
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:88: undefined reference to `av_find_stream_info'
/home/gcestaro/Scrivania/k3b-1.69.0/plugins/decoder/ffmpeg/k3bffmpegwrapper.cpp:130: undefined reference to `dump_format'
collect2: ld returned 1 exit status
make[2]: *** [lib/k3bffmpegdecoder.so] Errore 1
make[1]: *** [plugins/decoder/ffmpeg/CMakeFiles/k3bffmpegdecoder.dir/all] Errore 2
make: *** [all] Errore 2

----------------------------------------

My distro's Kubuntu 9.10


Anybody can help me?


Thanks.

---

### Post by TuxLove on 2010-01-09
The error appears to be in ffmpeg. I'm still trying to track it down, but the quickest way around it here is to exclude the ffmpeg decoder plugin when you do the cmake. ie:

[COLOR=Blue]cmake -DK3B_BUILD_FFMPEG_DECODER_PLUGIN=OFF[/COLOR]

Worked for me!  ;)

---

### Post by andrew.46 on 2010-01-10
Hi giorgio.65,

k3b has an optional dependency of FFmpeg if you wish to use the ffmpeg audio decoding plugin. Have a look here for all the k3b dependencies:

K3b 1.0 Requirement
[http://k3b.plainblack.com/requirements](http://k3b.plainblack.com/requirements)

All the best,

Andrew

---

