---
title: "Trying to run VLC for http streaming - permission denied"
date: 2011-10-07
forum: Multimedia Software
---

### Post by eXcEeDe on 2011-10-07
Hi all!
 
I'm a newbe at Linux and am currently trying to set up VLC to enable web streaming over http on my 10.04 dist. If i start the VLC GUI i can access the page on the local browser with [http://localhost:8080](http://localhost:8080). Although I can't make it list my movie directory. But when i try to start it by command:
 
vlc -I http [--http-src /media/DATA/Film/Film/ --http-host localhost:8081]
 
i get these errors:
 
VLC media player 1.1.11 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x942621c] main interface: creating httpd
[0x942621c] main interface error: socket bind error (Permission denied)
[0x942621c] main interface error: socket bind error (Permission denied)
[0x942621c] main interface error: cannot create socket(s) for HTTP host
[0x942621c] oldhttp interface error: cannot listen on localhost:8081
[0x942621c] main interface error: no suitable interface module
[0x937a67c] main libvlc error: interface "default" initialization failed
 
I tried to change ports and run the vlc-wrapper with sudo, but no luck.
netstat | grep 8080 or 8081 shows nothing. I upgraded VLC to 1.1.11.
Any suggestions?
 
My ultimate goal is to create some kind of start script to automate the VLC http server.

---

