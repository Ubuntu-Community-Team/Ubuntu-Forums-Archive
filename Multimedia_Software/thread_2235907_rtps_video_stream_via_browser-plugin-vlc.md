---
title: "rtps video stream via browser-plugin-vlc"
date: 2014-07-23
forum: Multimedia Software
---

### Post by masonje2 on 2014-07-23
I'm trying to get the latest vlc (2.0.8-0ubuntu0.12.04.1) to work on HP ThinPro 4.4 image based on Ubuntu 12.04.1 and Firefox 24.  I install vlc and the browser plugin via apt-get and all seems to install as expected.  This is to support video streaming via Qumu web streaming.  Somehow Qumu got us a package that worked running vlc 2.0.5 and firefox 12 for our ThinPro 4.0 image.  Totem is not in any way.

Here is what I'm seeing. I open the web page and click on the stream.  The plugin looks like it's going to run, then states "Program Finished".  I'm told by the web server owners that I can open the same exact stream by opening vlc, and entering in the path to the network stream like this:

rtsp://[server]/[stream].sdp

...and that works perfect. For some reason the browser plugin just acts like it's going to run it, then quits.  All the other flash based steams work fine from the server, just the live streams flake out.  This same stream works fine on our ThinPro 4.0 image with FF 12 and vlc 2.0.5 and browser plugin.

I'm hoping/thinking the core problem may be missing links for the plugin to work with FF, but I'm not sure where to start.  Any hints on where to start?

Thanks in advance!

---

