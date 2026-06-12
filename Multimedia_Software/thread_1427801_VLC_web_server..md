---
title: "VLC web server."
date: 2010-03-12
forum: Multimedia Software
---

### Post by Neonlights on 2010-03-12
I am unable to get vlc server to function. When I execute the command "vlc -I http" I get a large list of errors. I have edited the .host file but still no luck. I get a forbidden error when attempting to open the page at 8080. here is my error log
 
vlc -I http
 
VLC media player 1.0.2 Goldeneye
[0x8b3d908] inhibit interface error: Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
[0x8b3d908] main interface error: no suitable interface module
[0x8aa2660] main libvlc error: interface "inhibit,none" initialization failed
[0x8b3b1b0] main interface error: no interface module matched "globalhotkeys,none"
[0x8b3b1b0] main interface error: no suitable interface module
[0x8aa2660] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8b3b180] main interface: creating httpd
[0x8b3b180] main interface error: socket bind error (Permission denied)
[0x8b3b180] main interface error: socket bind error (Permission denied)
[0x8b3b180] main interface error: cannot create socket(s) for HTTP host
[0x8b3b180] http interface error: cannot listen on :8080
[0x8b3b180] main interface error: no suitable interface module
[0x8aa2660] main libvlc error: interface "default" initialization failed
 
 
 
here is my .hosts
 
# link-local addresses
#fe80::/64
# private addresses
fc00::/7
fec0::/10
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
169.254.0.0/16
# The world (uncommenting these 2 lines is not quite safe)
::/0
0.0.0.0/0

---

