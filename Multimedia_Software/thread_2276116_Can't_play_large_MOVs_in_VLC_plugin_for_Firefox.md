---
title: "Can't play large MOVs in VLC plugin for Firefox"
date: 2015-04-30
forum: Multimedia Software
---

### Post by jmoellers on 2015-04-30
Hi,

As gwenview has problems with quicktime files from our cameras (they are either not shown at all or shown in some nice blueish tint),
I'm trying to write a custom web server (using microhttps) to view multimedia files in a split firefox on Kubuntu 14.04:
the top frame ("presentation") is the view frame
the bottom frame ("browse") is the browse frame.
(This is to mimic a picture/movie viewer from WinXP my wife is used to).

Viewing pictures is OK, I just load them into the top frame:
<a href=\"XXXXXXXX\" target=\"presentation\"><img src=\"YYYYYYYY\"></a>

To view a MOVie, I use browser-plugin-vlc Version: 2.0.6-2 as follows:
<embed type="application/x-vlc-plugin"
 pluginspage="http://www.videolan.org" version="VideoLAN.VLCPlugin.2"  width="100%"
 height="100%" id="vlc" loop="no" autoplay="yes" target="XXXXXXXX" />

This works OK for a small-ish file (my smallest available MOV is 2249665 bytes), but fails on anything larger, the next larger file is 3277126bytes.
I do see my web backend send the file just fine but the player only shows the cone. The smaller MOV plays fine.
When I click on the "play" button, the file is re-requested, but still not played.
I cannot see anything special about these two values, they are not on opposite sides of some "natural" boundary (e.g. 1MB, 16MB, 2GB, 4GB).

I have tried several techniques within the backend to upload the file:
open the file, then call MHD_create_response_from_fd()
slurp the file, then call MHD_create_response_from_buffer()
open the file, then call MHD_create_response_from_callback() with suitable callbacks.
I just send the raw move data upon request.
None of them works.
So I assume the problem lies within the plugin.

The vlc player plays all files perfectly.

Any ideas/pointers?

Josef

---

