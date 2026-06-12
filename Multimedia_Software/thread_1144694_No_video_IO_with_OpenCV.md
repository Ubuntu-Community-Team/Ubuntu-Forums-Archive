---
title: "No video I/O with OpenCV"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Sjeti on 2009-05-01
I have either downloaded from the repositories, or compiled from source almost anything related to xine, gstreamer, or ffmpeg.

However, no matter what I do I can not for the life of me get the configure on OpenCV to recognize any of these formats.  I have downloaded all the dev files and/or installed the package from source, yet I can still not get any to work.

Anyone have any suggestions? How can I get my openCV to read .avi files?

Edit: I am compiling opencv-1.1.0.  1.0 also did not recognize anything.

---

### Post by Sjeti on 2009-05-01
So I bothered to read through the config file and it seems I need to specify --with-gstreamer.  Trying this now.

---

### Post by Sjeti on 2009-05-01
It still doesn't seem read my .avi files....maybe the code is wrong? :

```

int main( int argc, char** argv ) {
    cvNamedWindow( "Example3", CV_WINDOW_AUTOSIZE );
    g_capture = cvCreateFileCapture(argv[1]);
    int frames = (int)cvGetCaptureProperty(g_capture,CV_CAP_PROP_FRAME_COUNT);
    if (frames != 0) {
      cvCreateTrackbar("Position","Example3",&g_slider_position,frames,onTrackbarSlide);
    }
    IplImage* frame;
    while(1) {
	frame=cvQueryFrame(g_capture);
        if( !frame ) break;
        cvShowImage( "Example3", frame );
        char c = cvWaitKey(33);
        if( c == 27 ) break;
    }
    cvReleaseCapture( &g_capture );
    cvDestroyWindow( "Example3" );
    return(0);
}

```
Just some stuff out of the OpenCV tutorial.

---

### Post by Sjeti on 2009-05-01
No luck.  I tried using xine but there is an error in OpenCV's code converting int to const *char.  It won't include quicktime even if I specify it.

---

### Post by dieklaue on 2009-05-01
It's a know bug, see [https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/311188](https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/311188)

The problem is that the location of the ffmpeg headers has changed in Jaunty; OpenCV's ./configure-script just outputs a warning (see your config.log an grep for 'ffmpeg') an compiles without ffmpeg support.

HTH, Johannes

---

### Post by Sjeti on 2009-05-02
Thanks, I'm trying to install it with ffmpeg now, it recongnized it on ./configure.

---

### Post by Sjeti on 2009-05-02
It worked, I'm just getting an error doing the make install and I can't seem to figure it out. 

I've used -fPIC to install my ffmpeg files as well as the openCV files, yet I still get this error:

```

libtool: install: warning: relinking `libhighgui.la'
(cd /home/del/Source/opencv-1.1.0/otherlibs/highgui; /bin/bash ../../libtool  --tag=CXX --mode=relink g++ -Wall -fno-rtti -pipe -O3 -g -msse2 -no-undefined -version-info 2:0:0 -o libhighgui.la -rpath /usr/local/lib dummy.lo lib_highgui.la ../../cxcore/src/libcxcore.la ../../cv/src/libcv.la -pthread -lgthread-2.0 -lrt -lglib-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lpng12 -ljpeg -lz -lm -ltiff -ljasper -lavcodec -lavformat -lswscale -lavformat -lavcodec -lpthread -ldl -lm )  
g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../../lib/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.3.3/crtbeginS.o  .libs/dummy.o -Wl,--whole-archive ./.libs/lib_highgui.a -Wl,--no-whole-archive  -L/usr/local/lib -lcxcore -lcv -L/usr/lib -lgthread-2.0 -lrt -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgdk_pixbuf-2.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lpng12 -ljpeg -lz -ltiff -ljasper -lswscale -lavformat -lavcodec -lpthread -ldl -L/usr/lib/gcc/x86_64-linux-gnu/4.3.3 -L/usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../.. -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.3.3/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../../lib/crtn.o  -msse2 -pthread -Wl,-soname -Wl,libhighgui.so.2 -o .libs/libhighgui.so.2.0.0
/usr/bin/ld: /usr/local/lib/libavformat.a(allformats.o): relocation R_X86_64_32 against `aac_demuxer' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavformat.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
libtool: install: error: relink `libhighgui.la' with the above command before installing it
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/del/Source/opencv-1.1.0/otherlibs/highgui'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/del/Source/opencv-1.1.0/otherlibs/highgui'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/del/Source/opencv-1.1.0/otherlibs'
make: *** [install-recursive] Error 1

```

Not entirely sure what I changed up because I've been able to install this before.

---

### Post by gijzelaerr on 2009-05-03
hi everyone,

I sort of fixed the problem.

Bug report:
* [https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/311188](https://bugs.launchpad.net/ubuntu/+source/opencv/+bug/311188)

patch:
* [http://launchpadlibrarian.net/26284558/400_fix_latest_ffmpeg.diff](http://launchpadlibrarian.net/26284558/400_fix_latest_ffmpeg.diff)

PPA with working packages:
* [https://launchpad.net/~gijzelaar/+archive/opencv](https://launchpad.net/~gijzelaar/+archive/opencv)

Easy installation instructions
* [http://gijs.pythonic.nl/blog/2009/may/3/getting-video-io-working-opencv-and-ubuntu-jaunty-/](http://gijs.pythonic.nl/blog/2009/may/3/getting-video-io-working-opencv-and-ubuntu-jaunty-/)

I also moved my opencv python ctypes packages to this repository. Note that the PPA build queue is quite long today so it can take some time before the packages show up.

If you have any questions let me know,

--
Gijs Molenaar
[http://gijs,pythonic.nl](http://gijs,pythonic.nl)

---

### Post by Sjeti on 2009-05-04
....I think I love you.


It works perfectly, thanks for the patch.

---

### Post by guja on 2009-07-03
Can you please send me how to install openCV on Ubuntu Jaunty?

I am totally depressed and haven't manage for 2 days to make it work.

Please give some step-by-step tutorial!

Thanks in advance!

---

