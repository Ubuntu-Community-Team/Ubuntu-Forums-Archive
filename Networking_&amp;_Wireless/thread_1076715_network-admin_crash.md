---
title: "network-admin crash"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by oubaas on 2009-02-21
Have fully updated 8.10/Ibex amd64, wireless card and built-in wired ethernet on this machine.
Have removed network-manager and network-manager-gnome, and installed wicd.
At least now I seem to have some measure of control.

I need to be able to connect to office wireless network and to various industrial stuff at the same time, 'stuff' are normally just an FTP direct fixed-IP address cross-over-cable connection that I push/pull code to/from with FileZilla.
So I tried to set up a selection of 'locations' in /myHome/.gnome2/network-admin-locations. When I run network-admin and click 'save current as location' button it shuts down. Then in /log/messages I find
```
Feb 21 16:44:23 LanBox kernel: [ 8418.826337] network-admin[27714]: segfault at 0 ip 00007f34a4886110 sp 00007fffb0f48308 error 4 in libglib-2.0.so.0.1800.2[7f34a481d000+c3000].
```

I can create an empty file in /network-admin-locations, and can see it in network-admin's location pull-down menu. When I try to save/overwrite it I get the same crash. I've looked at file permissions and it should be able to write to the file.

Is 'network-admin' or libglib the problem? 

If I had some idea of what a 'location' file should look like I could write my own, but I can't seed the folder with anything to use as a template. Any idea of what it should contain?
Thanks

---

