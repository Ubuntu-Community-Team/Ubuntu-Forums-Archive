---
title: "Ubuntu VLC Player Stream"
date: 2011-05-09
forum: Multimedia Software
---

### Post by rameshma on 2011-05-09
[SIZE=2]Streaming using VLC:  the catpure device is a CAM.  I'm really struck with this problem.

I really appreciate if some one could help me out.

I have installed all the dependencies like FFMPEG

vlc v4l2:///dev/video0 --sout  '#duplicate{dst=display,dst=rtp{dst=192.168.104.82,port=5004},dst=rtp{dst=192.168.120.105,port=5004},dst=rtp{dst=192.168.105.54,port=5004,sdp=rtsp://192.168.101.185:8080/test.sdp}}'
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9226914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb75920d4, 0xb7592048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1305163245)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:557): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[0x95386ec] main stream out: creating httpd
[0x9536c2c] stream_out_rtp stream out error: cannot add this stream (unsupported codec: YUY2)
[0x95373bc] stream_out_rtp stream out error: cannot add this stream (unsupported codec: YUY2)
[0x95386ec] stream_out_rtp stream out error: cannot add this stream (unsupported codec: YUY2)[/SIZE]

---

