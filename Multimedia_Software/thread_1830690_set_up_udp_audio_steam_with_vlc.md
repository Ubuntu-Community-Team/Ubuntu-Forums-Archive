---
title: "set up udp audio steam with vlc"
date: 2011-08-22
forum: Multimedia Software
---

### Post by mulllhausen on 2011-08-22
i am trying to stream audio using udp from my home server so i can listen at work. i will control the audio that plays over ssh - i have already ssh set up fine so that's no problem. i tried the following command:

```
cvlc -v /tmp/gotye1.mp3 --sout '#rtp{dst=192.168.1.152,port=9009,sdp=rtsp://myhostname.org:9009/test.sdp}'
```

but i get lots of errors (actually i turned the verbosity down since the output was really long - i can turn it up and post the output if anybody needs to see it though):

```
VLC media player 1.0.2 Goldeneye
[0x988a5a8] main demux warning: no access_demux module matching "file" could be loaded
[0x9889150] inhibit interface error: Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0x9889150] main interface warning: no interface module matching "inhibit,none" could be loaded
[0x9889150] main interface error: no suitable interface module
[0x97f3140] main libvlc error: interface "inhibit,none" initialization failed
[0x9894268] screensaver interface warning: failed to connect to the D-BUS daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0x9889a80] main interface warning: no interface module matching "globalhotkeys,none" could be loaded
[0x9889a80] main interface error: no suitable interface module
[0x97f3140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9889a80] dummy interface: using the dummy interface module...
[0x98a0028] main stream out: creating httpd
[0x98a0028] main stream out error: socket bind error (Permission denied)
[0x98a0028] main stream out error: cannot create socket(s) for HTTP host
[0x98a0028] stream_out_rtp stream out error: cannot export SDP as RTSP

```

any ideas?

---

