---
title: "X2Go Desktop Sharing Denied Access to User"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2011-11-25
Hi,

I installed X2Go Server and Destop Sharing yesterday, and **successfully** connected to the "connect to remote desktop" (shadow) session via X2Go client. 

All was great!

*However, after the first reboot of the server, I've now received the error "access denied from user" in the X2Go Client.*

I use SSH Key Auth and can access the server in a regular session. 

I can still connect fine to a regular Gnome/KDE/etc session, however trying the custom session of "connect to remote destop" now gives this error. 

I'm assuming it's a permission issue on the server with X2Go desktop sharing.

Here is the X2Go Client terminal log....

[HTML] read  1  sessions from config file 
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
Have key, starting session 

start new ssh connection 

setting SSH DIR to  "/home/####/ssh" 
ssh connection ok 

continue normal x2go session 

"x2gostartagent 800x600 wan 16m-jpeg-9 unix-kde-depth_24 us pc4/us 1 S 1XSHADnameXSHAD:0" 

Agent output: "starting x2godesktopsharing in client mode, cmd: ###.###.##.### 800x600 wan 16m-jpeg-9 unix-kde-depth_24 us pc4/us 1 S 1XSHADnameXSHAD:0 800x6000
Unable to connect: /tmp/x2godesktopsharing_@name@:0
ACCESS DENIED
" 
close event 
  [/HTML]

Thanks for any help!

*Server restart solved the issue.

---

