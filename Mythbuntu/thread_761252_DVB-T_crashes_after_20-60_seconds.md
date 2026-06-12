---
title: "DVB-T crashes after 20-60 seconds"
date: 2008-04-21
forum: Mythbuntu
---

### Post by pearless on 2008-04-21
Hi,

I have just downloaded and installed mythbuntu RC 1, I have followed the instructions on mythtv.org to install my Hauppage Nova T 500 card and it works for anything from 10 to 60 seconds and then the mythtv front end dies. Note I selected New Zealand (where I live) and it detected all the TV channels, EPG etc.

I am using a Celeron 2.4, 512MB RAM, NVidia 5700
From "apt-cache policy mythtv-common"

I get:

mythtv-common:
  Installed: 0.21.0+fixes16838-0ubuntu3
  Candidate: 0.21.0+fixes16838-0ubuntu3
  Version table:
 *** 0.21.0+fixes16838-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
        100 /var/lib/dpkg/status

From "less /var/log/mythtv/mythfrontend.log"

I get (last 2 pages only shown here)::
2008-04-21 18:26:49.685 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/weather-ui.xml
2008-04-21 18:27:21.603 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/keyboard/en_us_ui.xml
2008-04-21 18:27:36.448 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/keyboard/en_us_ui.xml
2008-04-21 18:28:16.041 Container startup has NULL area, bad theme.
2008-04-21 18:28:36.861 TV: Attempting to change from None to WatchingLiveTV
2008-04-21 18:28:36.862 Using protocol version 40
2008-04-21 18:28:38.500 DPMS Deactivated 
2008-04-21 18:28:38.501 New DB connection, total: 3
2008-04-21 18:28:38.503 New DB connection, total: 4
2008-04-21 18:28:38.504 Connected to database 'mythconverg' at host: localhost
2008-04-21 18:28:38.507 Connected to database 'mythconverg' at host: localhost
2008-04-21 18:28:38.589 NVP: Disabling Audio, params(-1,2,44100)
2008-04-21 18:28:38.850 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-04-21 18:28:39.046 OSD Theme Dimensions W: 640 H: 480
2008-04-21 18:28:40.792 TV: Changing from None to WatchingLiveTV
2008-04-21 18:28:40.797 Realtime priority would require SUID as root.
2008-04-21 18:28:41.152 Video timing method: USleep with busy wait
2008-04-21 18:28:43.287 NVP: Prebuffer wait timed out 10 times.
2008-04-21 18:28:45.356 NVP: Prebuffer wait timed out 10 times.
2008-04-21 18:28:46.972 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-04-21 18:28:47.872 AFD: Opened codec 0x8947f00, id(H264) type(Video)
2008-04-21 18:28:47.941 AFD: Opened codec 0x8be59b0, id(DVB_SUBTITLE) type(Subtitle)
2008-04-21 18:28:48.020 NVP: Disabling Audio, params(0,-1,-1)
2008-04-21 18:28:48.077 NVP: Prebuffer wait timed out 10 times.
2008-04-21 18:28:48.293 [h264 @ 0xb73e3b88]B picture before any references, skipping
2008-04-21 18:28:48.293 [h264 @ 0xb73e3b88]decode_slice_header error
2008-04-21 18:28:48.293 [h264 @ 0xb73e3b88]no frame!
2008-04-21 18:28:48.293 AFD Error: Unknown decoding error
2008-04-21 18:28:48.293 [h264 @ 0xb73e3b88]B picture before any references, skipping
2008-04-21 18:28:48.294 [h264 @ 0xb73e3b88]decode_slice_header error
2008-04-21 18:28:48.294 [h264 @ 0xb73e3b88]no frame!
2008-04-21 18:28:48.294 AFD Error: Unknown decoding error
2008-04-21 18:28:48.294 [h264 @ 0xb73e3b88]B picture before any references, skipping
2008-04-21 18:28:48.294 [h264 @ 0xb73e3b88]decode_slice_header error
2008-04-21 18:28:48.295 [h264 @ 0xb73e3b88]no frame!
2008-04-21 18:28:48.295 AFD Error: Unknown decoding error
2008-04-21 18:28:48.295 [h264 @ 0xb73e3b88]B picture before any references, skipping
2008-04-21 18:28:48.295 [h264 @ 0xb73e3b88]decode_slice_header error
2008-04-21 18:28:48.295 [h264 @ 0xb73e3b88]no frame!
2008-04-21 18:28:48.295 AFD Error: Unknown decoding error
2008-04-21 18:28:48.295 [h264 @ 0xb73e3b88]B picture before any references, skipping
2008-04-21 18:28:48.296 [h264 @ 0xb73e3b88]decode_slice_header error
2008-04-21 18:28:48.296 [h264 @ 0xb73e3b88]no frame!
2008-04-21 18:28:48.296 AFD Error: Unknown decoding error
2008-04-21 18:28:48.296 [h264 @ 0xb73e3b88]B picture before any references, skipping
2008-04-21 18:28:48.296 [h264 @ 0xb73e3b88]decode_slice_header error
2008-04-21 18:28:48.296 [h264 @ 0xb73e3b88]no frame!
2008-04-21 18:28:48.296 AFD Error: Unknown decoding error
2008-04-21 18:28:48.297 [h264 @ 0xb73e3b88]B picture before any references, skipping
2008-04-21 18:28:48.297 [h264 @ 0xb73e3b88]decode_slice_header error
2008-04-21 18:28:48.297 [h264 @ 0xb73e3b88]no frame!
2008-04-21 18:28:48.297 AFD Error: Unknown decoding error
2008-04-21 18:28:48.878 NVP: Prebuffer wait timed out 10 times.
2008-04-21 18:28:49.104 NVP: prebuffering pause
2008-04-21 18:28:49.624 NVP: prebuffering pause
2008-04-21 18:28:49.962 [h264 @ 0xb73e3b88]cabac decode of qscale diff failed at 56 39
2008-04-21 18:28:49.962 [h264 @ 0xb73e3b88]error while decoding MB 56 39, bytestream (5170)
2008-04-21 18:28:50.275 NVP: prebuffering pause
2008-04-21 18:28:50.280 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:50.280 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:50.293 [h264 @ 0xb73e3b88]cabac decode of qscale diff failed at 33 11
2008-04-21 18:28:50.294 [h264 @ 0xb73e3b88]error while decoding MB 33 11, bytestream (51541)
2008-04-21 18:28:51.173 NVP: prebuffering pause
2008-04-21 18:28:51.790 NVP: prebuffering pause
2008-04-21 18:28:52.044 [h264 @ 0xb73e3b88]cabac decode of qscale diff failed at 54 30
2008-04-21 18:28:52.045 [h264 @ 0xb73e3b88]error while decoding MB 54 30, bytestream (8640)
2008-04-21 18:28:52.060 [h264 @ 0xb73e3b88]top block unavailable for requested intra4x4 mode -1 at 75 0
2008-04-21 18:28:52.061 [h264 @ 0xb73e3b88]error while decoding MB 75 0, bytestream (122261)
2008-04-21 18:28:52.341 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:52.481 NVP: prebuffering pause
2008-04-21 18:28:52.644 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:53.089 NVP: prebuffering pause
2008-04-21 18:28:53.797 NVP: prebuffering pause
2008-04-21 18:28:54.356 NVP: prebuffering pause
2008-04-21 18:28:54.556 [h264 @ 0xb73e3b88]cabac decode of qscale diff failed at 44 17
2008-04-21 18:28:54.557 [h264 @ 0xb73e3b88]error while decoding MB 44 17, bytestream (7791)
2008-04-21 18:28:54.610 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:54.611 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:54.888 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:55.155 NVP: prebuffering pause
2008-04-21 18:28:55.469 [h264 @ 0xb73e3b88]error while decoding MB 15 44, bytestream (-12)
2008-04-21 18:28:55.793 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:55.794 [h264 @ 0xb73e3b88]top block unavailable for requested intra mode at 52 0
2008-04-21 18:28:55.794 [h264 @ 0xb73e3b88]error while decoding MB 52 0, bytestream (12628)
2008-04-21 18:28:55.912 NVP: prebuffering pause
2008-04-21 18:28:56.029 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:56.305 [h264 @ 0xb73e3b88]reference picture missing during reorder
2008-04-21 18:28:56.592 NVP: prebuffering pause
2008-04-21 18:28:57.263 NVP: prebuffering pause
2008-04-21 18:28:57.469 [h264 @ 0xb73e3b88]cabac decode of qscale diff failed at 14 3
2008-04-21 18:28:57.469 [h264 @ 0xb73e3b88]error while decoding MB 14 3, bytestream (11873)
2008-04-21 18:28:57.546 [h264 @ 0xb73e3b88]Internal error, picture buffer overflow

and then mythtv front end disappears!

I have to start mythtvfrontend and it again works for a short period of "Watch TV" and dies again!

Any ideas?

Perhaps this is the same as Ticket #4798 ( [http://www.gossamer-threads.com/lists/mythtv/commits/319345](http://www.gossamer-threads.com/lists/mythtv/commits/319345) ) ?

Cheers Douglas.

---

### Post by laga on 2008-04-21
Can you try the weekly builds? [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
(Yes, it needs to say "0.21" instead of "0.20.2" ;)).

If the mirrors aren't synced yet, you can use the PPA directly: [https://launchpad.net/~mythbuntu/+archive](https://launchpad.net/~mythbuntu/+archive)

---

### Post by pearless on 2008-04-21
Thanks, that helped!

Now I get (last part before it crashed):
2008-04-22 13:54:25.414 NVP: prebuffering pause
2008-04-22 13:54:25.536 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:25.651 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:25.767 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:25.889 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:26.140 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:26.380 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:26.548 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:26.667 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:26.785 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:26.906 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:27.137 NVP: Prebuffer wait timed out 10 times.
2008-04-22 13:54:27.227 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:27.373 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:27.514 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:27.633 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:27.754 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:27.875 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:28.169 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:28.343 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:28.448 NVP: prebuffering pause
2008-04-22 13:54:28.560 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:28.677 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:28.795 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:28.917 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:29.157 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:29.304 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:29.446 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:29.572 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:29.698 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:29.819 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:30.065 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:30.137 NVP: Prebuffer wait timed out 10 times.
2008-04-22 13:54:30.276 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:30.416 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:30.536 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:30.676 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:30.808 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:31.087 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:31.274 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:31.379 NVP: prebuffering pause
2008-04-22 13:54:31.530 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:31.696 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:31.816 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:31.938 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:32.208 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:32.359 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:32.674 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:32.891 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:33.021 NVP: Prebuffer wait timed out 10 times.
2008-04-22 13:54:33.161 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
2008-04-22 13:54:33.313 [h264 @ 0xb73ebb88]Interlaced pictures + spatial direct mode is not implemented
Segmentation fault

Note sure what that means...

Any ideas?

Cheers Douglas.

---

