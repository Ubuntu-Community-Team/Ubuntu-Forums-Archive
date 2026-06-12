---
title: "VLC transcoding"
date: 2011-07-01
forum: Multimedia Software
---

### Post by allwise on 2011-07-01
Hello!

I'm trying to transcode my Dreambox DM500 signal to be able to see it on my phone, wherever I am. But i've got some problems when trying to transcode the stream (see the log provided). Does anyone know whats wrong? I'm running the vlc transcode on Ubuntu 11.04 from putty in the terminal.

Thanks!!

```
cvlc -I http http://192.168.0.104:31344 --sout='#transcode{acodec=mpga,vcodec=DIV3,ab=60,vb=150,scale=0.50,deinterlace,fps=15,channels=1,width=382,height=288}:std{access=http,mux=ts,url=192.168.0.102:8888} '
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xb3ddc0] inhibit interface error: Failed to connect to the D-Bus session daemon: //bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0xb3ddc0] main interface error: no suitable interface module
[0xb406d0] main interface error: no suitable interface module
[0xa23120] main libvlc error: interface "globalhotkeys,none" initialization failed
[0xb406d0] main interface: creating httpd
[0xb693a0] access_output_http access out error: cannot add stream /
[0x7eff30001bb0] stream_out_standard stream out error: no suitable sout access module for `http/ts://(null)'
[0x7eff30001310] main stream output error: stream chain failed for `transcode{acodec=mpga,vcodec=DIV3,ab=60,vb=150,scale=0.50,deinterlace,fps=15,channels=1,width=382,height=288}:std{access=http,mux=ts,url=192.168.0.102:8888} '
[0x7eff30000c10] main input error: cannot start stream output instance, aborting

```

---

