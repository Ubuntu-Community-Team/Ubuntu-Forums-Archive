---
title: "Songbird glibc error"
date: 2009-07-23
forum: Multimedia Software
---

### Post by lduperval on 2009-07-23
I'm trying to get Songbird 1.2.0 to work on Jaunty. When I start it I get:

```
*** glibc detected *** ././songbird-bin: munmap_chunk(): invalid pointer: 0x00007f559ab6a940 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f55d59c8cb8]
/usr/lib/tls/libnvidia-tls.so.1[0x7f5594387a3b]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:04 7766807                            /usr/local/Songbird/songbird-bin
00608000-00609000 rw-p 00008000 08:04 7766807                            /usr/local/Songbird/songbird-bin
41559000-4155b000 rwxp 00000000 00:0f 725                                /dev/zero
7f5594387000-7f5594388000 r-xp 00000000 08:04 9585372                    /usr/lib/tls/libnvidia-tls.so.180.44
7f5594388000-7f5594488000 ---p 00001000 08:04 9585372                    /usr/lib/tls/libnvidia-tls.so.180.44
7f5594488000-7f5594489000 rw-p 00001000 08:04 9585372                    /usr/lib/tls/libnvidia-tls.so.180.44
7f5594489000-7f559522b000 r-xp 00000000 08:04 8936199                    /usr/lib/libGLcore.so.180.44
7f559522b000-7f559532a000 ---p 00da2000 08:04 8936199                    /usr/lib/libGLcore.so.180.44
7f559532a000-7f5595761000 rwxp 00da1000 08:04 8936199                    /usr/lib/libGLcore.so.180.44
7f5595761000-7f5595773000 rwxp 7f5595761000 00:00 0 
7f5595773000-7f5595818000 r-xp 00000000 08:04 8936198                    /usr/lib/libGL.so.180.44
7f5595818000-7f5595917000 ---p 000a5000 08:04 8936198                    /usr/lib/libGL.so.180.44
7f5595917000-7f559594f000 rwxp 000a4000 08:04 8936198                    /usr/lib/libGL.so.180.44
7f559594f000-7f5595965000 rwxp 7f559594f000 00:00 0 
7f5595965000-7f559596b000 r-xp 00000000 08:04 8934426                    /usr/lib/gstreamer-0.10/libgstglimagesink.so
7f559596b000-7f5595b6a000 ---p 00006000 08:04 8934426                    /usr/lib/gstreamer-0.10/libgstglimagesink.so
7f5595b6a000-7f5595b6b000 rw-p 00005000 08:04 8934426                    /usr/lib/gstreamer-0.10/libgstglimagesink.so
7f5595b6b000-7f5595b7a000 r-xp 00000000 08:04 4866744                    /lib/libbz2.so.1.0.4
7f5595b7a000-7f5595d7a000 ---p 0000f000 08:04 4866744                    /lib/libbz2.so.1.0.4
7f5595d7a000-7f5595d7b000 r--p 0000f000 08:04 4866744                    /lib/libbz2.so.1.0.4
7f5595d7b000-7f5595d7c000 rw-p 00010000 08:04 4866744                    /lib/libbz2.so.1.0.4
7f5595d7c000-7f5595d81000 r-xp 00000000 08:04 8933357                    /usr/lib/gstreamer-0.10/libgstbz2.so
7f5595d81000-7f5595f80000 ---p 00005000 08:04 8933357                    /usr/lib/gstreamer-0.10/libgstbz2.so
7f5595f80000-7f5595f81000 r--p 00004000 08:04 8933357                    /usr/lib/gstreamer-0.10/libgstbz2.so
7f5595f81000-7f5595f82000 rw-p 00005000 08:04 8933357                    /usr/lib/gstreamer-0.10/libgstbz2.so
7f5595f82000-7f5595f8c000 r-xp 00000000 08:04 8932600                    /usr/lib/gstreamer-0.10/libgstdtmf.so
7f5595f8c000-7f559618b000 ---p 0000a000 08:04 8932600                    /usr/lib/gstreamer-0.10/libgstdtmf.so
7f559618b000-7f559618c000 r--p 00009000 08:04 8932600                    /usr/lib/gstreamer-0.10/libgstdtmf.so
7f559618c000-7f559618d000 rw-p 0000a000 08:04 8932600                    /usr/lib/gstreamer-0.10/libgstdtmf.so
7f559618d000-7f5596196000 r-xp 00000000 08:04 8936788                    /usr/lib/gstreamer-0.10/libgstladspa.so
7f5596196000-7f5596395000 ---p 00009000 08:04 8936788                    /usr/lib/gstreamer-0.10/libgstladspa.so
7f5596395000-7f5596396000 r--p 00008000 08:04 8936788                    /usr/lib/gstreamer-0.10/libgstladspa.so
7f5596396000-7f5596397000 rw-p 00009000 08:04 8936788                    /usr/lib/gstreamer-0.10/libgstladspa.so
7f5596397000-7f559639f000 r-xp 00000000 08:04 8932588                    /usr/lib/gstreamer-0.10/libgstjrtp.so
7f559639f000-7f559659f000 ---p 00008000 08:04 8932588                    /usr/lib/gstreamer-0.10/libgstjrtp.so
7f559659f000-7f55965a0000 r--p 00008000 08:04 8932588                    /usr/lib/gstreamer-0.10/libgstjrtp.so
7f55965a0000-7f55965a2000 rw-p 00009000 08:04 8932588                    /usr/lib/gstreamer-0.10/libgstjrtp.so
7f55965a2000-7f55965ac000 r-xp 00000000 08:04 8933887                    /usr/lib/gstreamer-0.10/libgstliveadder.so
7f55965ac000-7f55967ab000 ---p 0000a000 08:04 8933887                    /usr/lib/gstreamer-0.10/libgstliveadder.so
7f55967ab000-7f55967ac000 r--p 00009000 08:04 8933887                    /usr/lib/gstreamer-0.10/libgstliveadder.so
7f55967ac000-7f55967ad000 rw-p 0000a000 08:04 8933887                    /usr/lib/gstreamer-0.10/libgstliveadder.so
7f55967ad000-7f55967b6000 r-xp 00000000 08:04 8932592                    /usr/lib/gstreamer-0.10/libgstrtpjitterbuffer.so
7f55967b6000-7f55969b5000 ---p 00009000 08:04 8932592                    /usr/lib/gstreamer-0.10/libgstrtpjitterbuffer.so
7f55969b5000-7f55969b6000 r--p 00008000 08:04 8932592                    /usr/lib/gstreamer-0.10/libgstrtpjitterbuffer.so
7f55969b6000-7f55969b7000 rw-p 00009000 08:04 8932592                    /usr/lib/gstreamer-0.10/libgstrtpjitterbuffer.so
7f55969b7000-7f55969fc000 r-xp 00000000 08:04 4866243                    /lib/libncursesw.so.5.7
7f55969fc000-7f5596bfb000 ---p 00045000 08:04 4866243                    /lib/libncursesw.so.5.7
7f5596bfb000-7f5596bff000 r--p 00044000 08:04 4866243                    /lib/libncursesw.so.5.7
7f5596bff000-7f5596c00000 rw-p 00048000 08:04 4866243                    /lib/libncursesw.so.5.7
7f5596c00000-7f5596c1e000 r-xp 00000000 08:04 5145089                    /usr/lib/libcaca.so.0.99.16
7f5596c1e000-7f5596e1e000 ---p 0001e000 08:04 5145089                    /usr/lib/libcaca.so.0.99.16
7f5596e1e000-7f5596e1f000 r--p 0001e000 08:04 5145089                    /usr/lib/libcaca.so.0.99.16
7f5596e1f000-7f5596ea6000 rw-p 0001f000 08:04 5145089                    /usr/lib/libcaca.so.0.99.16
7f5596ea6000-7f5596eaa000 rw-p 7f5596ea6000 00:00 0 
7f5596eaa000-7f5596ead000 r-xp 00000000 08:04 8932844                    /usr/lib/gstreamer-0.10/libgstcacasink.so
7f5596ead000-7f55970ac000 ---p 00003000 08:04 8932844                    /usr/lib/gstreamer-0.10/libgstcacasink.so
7f55970ac000-7f55970ad000 r--p 00002000 08:04 8932844                    /usr/lib/gstreamer-0.10/libgstcacasink.so
7f55970ad000-7f55970ae000 rw-p 00003000 08:04 8932844                    /usr/lib/gstreamer-0.10/libgstcacasink.so
7f55970ae000-7f55970dc000 r-xp 00000000 08:04 8929946                    /usr/lib/libdc1394.so.22.1.0
7f55970dc000-7f55972db000 ---p 0002e000 08:04 8929946                    /usr/lib/libdc1394.so.22.1.0
7f55972db000-7f55972dc000 rw-p 0002d000 08:04 8929946                    /usr/lib/libdc1394.so.22.1.0
7f55972dc000-7f559731c000 rw-p 7f55972dc000 00:00 0 
7f559731c000-7f5597324000 r-xp 00000000 08:04 8934429                    /usr/lib/gstreamer-0.10/libgstdc1394.so
7f5597324000-7f5597523000 ---p 00008000 08:04 8934429                    /usr/lib/gstreamer-0.10/libgstdc1394.so
7f5597523000-7f5597524000 r--p 00007000 08:04 8934429                    /usr/lib/gstreamer-0.10/libgstdc1394.so
7f5597524000-7f5597525000 rw-p 00008000 08:04 8934429                    /usr/lib/gstreamer-0.10/libgstdc1394.so
7f5597525000-7f559752b000 r-xp 00000000 08:04 8936794                    /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f559752b000-7f559772a000 ---p 00006000 08:04 8936794                    /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f559772a000-7f559772b000 r--p 00005000 08:04 8936794                    /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f559772b000-7f559772c000 rw-p 00006000 08:04 8936794                    /usr/lib/gstreamer-0.10/libgstmpegvideoparse.so
7f559772c000-7f5597731000 r-xp 00000000 08:04 8936786                    /usr/lib/gstreamer-0.10/libgsth264parse.so
7f5597731000-7f5597930000 ---p 00005000 08:04 8936786                    /usr/lib/gstreamer-0.10/libgsth264parse.so
7f5597930000-7f5597931000 r--p 00004000 08:04 8936786                    /usr/lib/gstreamer-0.10/libgsth264parse.so
7f5597931000-7f5597932000 rw-p 00005000 08:04 8936786                    /usr/lib/gstreamer-0.10/libgsth264parse.so
7f5597932000-7f559794b000 r-xp 00000000 08:04 8930453                    /usr/lib/libbluetooth.so.3.2.1
7f559794b000-7f5597b4a000 ---p 00019000 08:04 8930453                    /usr/lib/libbluetooth.so.3.2.1
7f5597b4a000-7f5597b4b000 r--p 00018000 08:04 8930453                    /usr/lib/libblueCould not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

I don't have the libvisual-0.4-plugins package installed. I'm on an amd64 system.

Any ideas?

Thanks,

L

---

### Post by xc3RnbFO8P on 2009-07-23
Read this:
[http://ubuntuforums.org/showthread.php?t=1005356]("http://ubuntuforums.org/showthread.php?t=1005356")

---

### Post by lduperval on 2009-07-23
OK, I finally fixed it by removing all traces of the Jaunty NVidia device driver and installing the 185.18 version from the NVidia site.

I'm not sure what I did right, but my graphics are flying now! Oh, and Songbird works.

L

---

