---
title: "VLC Streaming"
date: 2009-11-11
forum: Multimedia Software
---

### Post by theweirdone on 2009-11-11
Hey,
I've been trying for a while now to get VLC to stream videos from my server. I've read everything I could find on the subject with no result. I think it might be a problem with the hosts file.

So, the command I'm using on the server to stream is 
```
vlc --sout '#standard{access=http,mux=ts,dst:=8081}' --extraintf http /path/to/video.avi
```

The first problem I'm getting is that VLC itself seems to fail, with these messages:
```

VLC media player 1.0.2 Goldeneye
[0x9ca8698] main interface: creating httpd
[0x9cc5640] inhibit interface error: Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0x9cc5640] main interface error: no suitable interface module
[0x9c13140] main libvlc error: interface "inhibit,none" initialization failed
[0x9cc8d18] main interface error: no interface module matched "globalhotkeys,none"
[0x9cc8d18] main interface error: no suitable interface module
[0x9c13140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9c13140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9cc8dc0] qt4 interface error: Could not connect to X server
[0x9cc8dc0] skins2 interface error: Cannot open display
[0x9cc8dc0] skins2 interface error: cannot initialize OSFactory
Remote control interface initialized. Type `help' for help.
[0x9cd96b0] access_output_http access out error: cannot add stream /
[0x9cc4438] stream_out_standard stream out error: no suitable sout access module for `http/ts://(null)'
[0x9cc4300] main stream output error: stream chain failed for `standard{access=http,mux=ts,dst:=8081}'
[0x9cc9348] main input error: cannot start stream output instance, aborting
```

Does that mean I installed vlc incorrectly?

Just for general info, my server's running Ubuntu 9.10 Server Edition. This is what the hosts file contains:
```

127.0.0.1       localhost
127.0.1.1       blue-server.lan blue-server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

And I'm trying to pick up the stream on a netbook running Ubuntu Desktop 9.10. It's host file reads:
```

127.0.0.1       localhost
127.0.1.1       theweirdone-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Do I have to change anything in the hosts file? To be honest, I don't really understand what the hosts file is...

Any help is appreciated,
Thanks

---

### Post by theweirdone on 2009-11-15
So now I realise it has nothing to do with the host files. Did I not install VLC correctly?

---

### Post by rodreegez on 2009-12-06
Hey, so I've just bumped into this problem and found your post. I think it is to do with the fact that VLC wants to display the film on the machine you are calling it on. Seeing as it's a server, there is no screen. Somehow I need to pump the display out to the network...

Will hack away and report back.

---

### Post by sdowney717 on 2009-12-06
why are you trying to stream files and to what device?

you can use upnp and stream video etc...

check out minidlna
[http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)

this works very well and with little effort on your part and the pc's brain

---

