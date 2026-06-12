---
title: "VLC - Multiple RTSP streams in one window?"
date: 2014-07-03
forum: Multimedia Software
---

### Post by Roasted on 2014-07-03
Hi there. I'd like to set up VLC to launch two videos side by side in one window. In particular, this would be using RTSP streams from my surveillance cameras to watch a live stream. I will not be recording or doing anything like that. In fact, I won't even have audio. Just video streams in real time.

I saw some references indicating that the mosaic feature is what I want. Unfortunately, I'm either an idiot or VLC's documentation is just really poor (or both?). So far I've been unsuccessful in getting this to work. The streams work when I view them individually, but not together, which of course is the end goal.

I set up a mosaic config file here:

```
new channel1 broadcast enabled                                                       
setup channel1 input rtsp://@192.168.1.11:554/live3.sdp                                       
setup channel1 output #duplicate{dst=mosaic-bridge{id=1,height=144,width=180},select=video,dst=bridge-out{id=1},select=audio}                                                         
                                                                               
new channel2 broadcast enabled
setup channel2 input rtsp://@192.168.1.12:554/live3.sdp
setup channel2 output #duplicate{dst=mosaic-bridge{id=2,height=144,width=180},select=video,dst=bridge-out{id=2},select=audio}                                                         

new background broadcast enabled
setup background input /home/jason/Documents/black.png
setup background output #transcode{sfilter=mosaic,vcodec=mp2v,vb=10000,scale=1}:bridge-in{delay=400,id-offset=100}:standard{access=udp,mux=ts,url=239.255.12.42,sap,name="mosaic"}

control background play
control channel1 play
control channel2 play
```

Is there anything noticably wrong with this? Here is the error output in terminal:

```
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x2052828] [http] lua interface: Lua HTTP interface
[0x2026118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x2042d18] [Media: channel2] main input error: ES_OUT_RESET_PCR called
[0x2051e68] [Media: channel1] main input error: ES_OUT_RESET_PCR called
Non-reference picture received and no reference available
[h264 @ 0x7fca90017e80] decode_slice_header error
Non-reference picture received and no reference available
[h264 @ 0x7fca980246a0] decode_slice_header error

```

And lastly, here is the command I am running to kick this off:

```
vlc --color --vlm-conf mosaic.conf --mosaic-width 1920 --mosaic-height 1080 --mosaic-rows 2 --mosaic-cols 2 --mosaic-order 1,2,3,4

```

This is on Ubuntu 14.04 with VLC 2.1.4. Thanks for any and all help!

---

