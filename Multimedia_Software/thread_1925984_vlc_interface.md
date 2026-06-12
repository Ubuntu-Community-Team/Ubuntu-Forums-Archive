---
title: "vlc interface"
date: 2012-02-15
forum: Multimedia Software
---

### Post by manox on 2012-02-15
Hi I have tried to enable HTTP interface for VLC which is running on my HTPC
and now I'm not able to run vlc at all 
I'm getting this error
```
manox@htpc:~/.config/vlc$ vlc
VLC media player 1.1.12 The Luggage (revision exported)
[0x9ec585c] main interface: creating httpd
[0x9ec585c] main interface error: socket bind error (Permission denied)
[0x9ec585c] main interface error: cannot create socket(s) for HTTP host
[0x9ec585c] oldhttp interface error: cannot listen on 192.168.1.14:8080
[0x9ec585c] main interface error: no suitable interface module
Remote control interface initialized. Type `help' for help.
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9ec48e4] main interface: creating httpd
[0x9ec48e4] main interface error: socket bind error (Permission denied)
[0x9ec48e4] main interface error: cannot create socket(s) for HTTP host
[0x9ec48e4] oldhttp interface error: cannot listen on 192.168.1.14:8080
[0x9ec48e4] main interface error: no suitable interface module
[0x9e05164] main libvlc error: interface "default" initialization failed
status change: ( stop state: 0 )
status change: ( quit )

```

---

### Post by mc4man on 2012-02-15
if you haven't already you can open vlc in the default qt4 interface and fix your settings till you figure out how to set up the HTTP interface if so possible

In terminal
```
vlc -Iqt4
```

---

