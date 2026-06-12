---
title: "Compile Errors from OpenCV with ffmpeg + x264"
date: 2011-05-29
forum: Multimedia Software
---

### Post by wind_field on 2011-05-29
Dear My Friends,

I am trying to compile OpenCV 2.0 with ffmpeg (with x264) support on my Ubuntu 11.04 64-bit machine. (Since I want to use the binaries provided by other developers, I have to use opencv 2.0 version)

I followed the guide from: [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095") to compile x264 and ffmpeg manually, and succeeded.

Then I followed the guide in the INSTALL file provided by the OpenCV 2.0 package. I use CMake to configure and generate them, and use "make" command to try compiling. However, I got the following error report, which haunted me for almost half a week.

```
[COLOR="Red"]Linking CXX static library ../../lib/libhighgui_pch_dephelp.a[/COLOR]
[ 71%] Built target highgui_pch_dephelp
[COLOR="DarkOrchid"]Scanning dependencies of target pch_Generate_highgui[/COLOR]
[ 71%] [COLOR="RoyalBlue"]Generating _highgui.h[/COLOR]
[ 71%] [COLOR="rgb(65, 105, 225)"]Generating _highgui.h.gch/highgui_Release.gch[/COLOR]
[ 72%] Built target pch_Generate_highgui
[COLOR="rgb(153, 50, 204)"]Scanning dependencies of target highgui[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_images.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/image.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/loadsave.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/precomp.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/utils.o[/COLOR]
[ 74%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/window.o[/COLOR]
[ 74%] [COLOR="SeaGreen"]Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o[/COLOR]
In file included from /usr/local/include/libavutil/avutil.h:119:0,
                 from /usr/local/include/libavutil/samplefmt.h:22,
                 from /usr/local/include/libavcodec/avcodec.h:30,
                 from /usr/local/include/libavformat/avformat.h:42,
                 from /home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:97:
/usr/local/include/libavutil/common.h: In function ‘int32_t av_clipl_int32_c(int64_t)’:
/usr/local/include/libavutil/common.h:170:47: **[COLOR="Red"]error[/COLOR]**: ‘UINT64_C’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvCapture_FFMPEG::open(const char*)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:467:13: **[COLOR="red"]error[/COLOR]**: ‘CODEC_TYPE_VIDEO’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvCapture_FFMPEG::grabFrame()’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:548:54: **[COLOR="red"]error[/COLOR]**: ‘avcodec_decode_video’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In function ‘const char* icvFFMPEGErrStr(int)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:790:10: **[COLOR="red"]error[/COLOR]**: ‘AVERROR_NUMEXPECTED’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:794:10: **[COLOR="red"]error[/COLOR]**: ‘AVERROR_NOFMT’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:796:10: **[COLOR="red"]error[/COLOR]**: ‘AVERROR_IO’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:798:10: **[COLOR="red"]error[/COLOR]**: ‘AVERROR_NOMEM’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In function ‘AVStream* icv_add_video_stream_FFMPEG(AVFormatContext*, CodecID, int, int, int, double, int)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:883:70: **[COLOR="red"]error[/COLOR]**: ‘CODEC_TYPE_VIDEO’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In function ‘int icv_av_write_frame_FFMPEG(AVFormatContext*, AVStream*, uint8_t*, uint32_t, AVFrame*)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:982:22: **[COLOR="red"]error[/COLOR]**: ‘PKT_FLAG_KEY’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1002:30: **[COLOR="red"]error[/COLOR]**: ‘PKT_FLAG_KEY’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual void CvVideoWriter_FFMPEG::close()’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1162:3: warning: ‘int url_fclose(AVIOContext*)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:280)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1162:20: warning: ‘int url_fclose(AVIOContext*)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:280)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvVideoWriter_FFMPEG::open(const char*, int, double, CvSize, bool)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1199:41: [COLOR="red"]**error**[/COLOR]: ‘guess_format’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1213:31: **[COLOR="red"]error[/COLOR]**: ‘av_alloc_format_context’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1270:9: warning: ‘int av_set_parameters(AVFormatContext*, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1334)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1270:35: warning: ‘int av_set_parameters(AVFormatContext*, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1334)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1274:5: warning: ‘void dump_format(AVFormatContext*, int, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1434)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1274:35: warning: ‘void dump_format(AVFormatContext*, int, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1434)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1336:13: warning: ‘int url_fopen(AVIOContext**, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:279)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1336:52: warning: ‘int url_fopen(AVIOContext**, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:279)
make[2]: *** [src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o] Error 1
make[1]: *** [src/highgui/CMakeFiles/highgui.dir/all] Error 2
make: *** [all] Error 2
```

For you further information, I have used the latest code from x264 and ffmpeg git, and opencv2.0 from sourceforge.net

I have googled for a while but just cannot find a right solution to me. I know this similar compiling errors have been posted for many times, but different versions might have different fixes. So I hope any of you could help in this. Thank you in advance.

Regards,
Jingming

---

### Post by wind_field on 2011-05-29
It seems some tags in the code segments are not displayed correctly. Plz ignore the tags like [COLOR="***"][/COLOR]. Thank you.

---

### Post by wind_field on 2011-05-29
Is there anyone who can help on this?

---

### Post by milk3dfx on 2011-05-31
Hi
I have the same error and don't know what to do.

---

### Post by milk3dfx on 2011-06-01
I installed OpenCV on 10.4 with out any errors.

---

### Post by hnkulkarni on 2011-07-28
I am also stuck in the same error. Were you able to solve it ?
Any help or pointers regarding this will be very useful.

Regards, 
Hrushikesh

> **wind_field said:**
> Dear My Friends,

I am trying to compile OpenCV 2.0 with ffmpeg (with x264) support on my Ubuntu 11.04 64-bit machine. (Since I want to use the binaries provided by other developers, I have to use opencv 2.0 version)

I followed the guide from: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) to compile x264 and ffmpeg manually, and succeeded.

Then I followed the guide in the INSTALL file provided by the OpenCV 2.0 package. I use CMake to configure and generate them, and use "make" command to try compiling. However, I got the following error report, which haunted me for almost half a week.

```
[COLOR=Red]Linking CXX static library ../../lib/libhighgui_pch_dephelp.a[/COLOR]
[ 71%] Built target highgui_pch_dephelp
[COLOR=DarkOrchid]Scanning dependencies of target pch_Generate_highgui[/COLOR]
[ 71%] [COLOR=RoyalBlue]Generating _highgui.h[/COLOR]
[ 71%] [COLOR="rgb(65, 105, 225)"]Generating _highgui.h.gch/highgui_Release.gch[/COLOR]
[ 72%] Built target pch_Generate_highgui
[COLOR="rgb(153, 50, 204)"]Scanning dependencies of target highgui[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_images.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/image.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/loadsave.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/precomp.o[/COLOR]
[ 73%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/utils.o[/COLOR]
[ 74%] [COLOR="rgb(46, 139, 87)"]Building CXX object src/highgui/CMakeFiles/highgui.dir/window.o[/COLOR]
[ 74%] [COLOR=SeaGreen]Building CXX object src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o[/COLOR]
In file included from /usr/local/include/libavutil/avutil.h:119:0,
                 from /usr/local/include/libavutil/samplefmt.h:22,
                 from /usr/local/include/libavcodec/avcodec.h:30,
                 from /usr/local/include/libavformat/avformat.h:42,
                 from /home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:97:
/usr/local/include/libavutil/common.h: In function ‘int32_t av_clipl_int32_c(int64_t)’:
/usr/local/include/libavutil/common.h:170:47: **[COLOR=Red]error[/COLOR]**: ‘UINT64_C’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvCapture_FFMPEG::open(const char*)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:467:13: **[COLOR=red]error[/COLOR]**: ‘CODEC_TYPE_VIDEO’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvCapture_FFMPEG::grabFrame()’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:548:54: **[COLOR=red]error[/COLOR]**: ‘avcodec_decode_video’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In function ‘const char* icvFFMPEGErrStr(int)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:790:10: **[COLOR=red]error[/COLOR]**: ‘AVERROR_NUMEXPECTED’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:794:10: **[COLOR=red]error[/COLOR]**: ‘AVERROR_NOFMT’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:796:10: **[COLOR=red]error[/COLOR]**: ‘AVERROR_IO’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:798:10: **[COLOR=red]error[/COLOR]**: ‘AVERROR_NOMEM’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In function ‘AVStream* icv_add_video_stream_FFMPEG(AVFormatContext*, CodecID, int, int, int, double, int)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:883:70: **[COLOR=red]error[/COLOR]**: ‘CODEC_TYPE_VIDEO’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In function ‘int icv_av_write_frame_FFMPEG(AVFormatContext*, AVStream*, uint8_t*, uint32_t, AVFrame*)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:982:22: **[COLOR=red]error[/COLOR]**: ‘PKT_FLAG_KEY’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1002:30: **[COLOR=red]error[/COLOR]**: ‘PKT_FLAG_KEY’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual void CvVideoWriter_FFMPEG::close()’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1162:3: warning: ‘int url_fclose(AVIOContext*)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:280)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1162:20: warning: ‘int url_fclose(AVIOContext*)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:280)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp: In member function ‘virtual bool CvVideoWriter_FFMPEG::open(const char*, int, double, CvSize, bool)’:
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1199:41: [COLOR=red]**error**[/COLOR]: ‘guess_format’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1213:31: **[COLOR=red]error[/COLOR]**: ‘av_alloc_format_context’ was not declared in this scope
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1270:9: warning: ‘int av_set_parameters(AVFormatContext*, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1334)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1270:35: warning: ‘int av_set_parameters(AVFormatContext*, AVFormatParameters*)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1334)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1274:5: warning: ‘void dump_format(AVFormatContext*, int, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1434)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1274:35: warning: ‘void dump_format(AVFormatContext*, int, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avformat.h:1434)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1336:13: warning: ‘int url_fopen(AVIOContext**, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:279)
/home/jimmy/OpenCV-2.0.0/src/highgui/cvcap_ffmpeg.cpp:1336:52: warning: ‘int url_fopen(AVIOContext**, const char*, int)’ is deprecated (declared at /usr/local/include/libavformat/avio.h:279)
make[2]: *** [src/highgui/CMakeFiles/highgui.dir/cvcap_ffmpeg.o] Error 1
make[1]: *** [src/highgui/CMakeFiles/highgui.dir/all] Error 2
make: *** [all] Error 2
```For you further information, I have used the latest code from x264 and ffmpeg git, and opencv2.0 from sourceforge.net

I have googled for a while but just cannot find a right solution to me. I know this similar compiling errors have been posted for many times, but different versions might have different fixes. So I hope any of you could help in this. Thank you in advance.

Regards,
Jingming

---

### Post by Don_Shifty on 2011-08-30
still would like help on this topic!
i have the same error!

---

### Post by tpap on 2011-09-13
I'm having the same problem... Did anyone solve it?

---

### Post by arthursa on 2011-10-03
Had the same problem under Debian. Solved installing the 0.8.x ffmpeg [http://ffmpeg.org/download.html](http://ffmpeg.org/download.html)

[https://code.ros.org/trac/opencv/ticket/1020](https://code.ros.org/trac/opencv/ticket/1020)

---

