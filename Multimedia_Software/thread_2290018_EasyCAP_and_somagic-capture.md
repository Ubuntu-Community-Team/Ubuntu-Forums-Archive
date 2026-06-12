---
title: "EasyCAP and somagic-capture"
date: 2015-08-08
forum: Multimedia Software
---

### Post by philchambers on 2015-08-08
I have looked at the existing postings on this and can't find a solution. I'm using ubuntu 14.04.

I have and EasyCAP device and get the following from lsusb when I plug it in:
'Bus 001 Device 006: ID 1c88:0007 Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) (no firmware) [SMI-2021CBE]'

If I try somagic-capture at this stage I get
'Has device initialization been performed?'

I extracted the firmware using somagic-extract-firmware from SmiUsbGrabber3F.sys into /lib/firmware/somagic_firmware.bin

After running sudo somagic-init lsusb now gives:
'Bus 001 Device 007: ID 1c88:003f Somagic, Inc.'

Note that I do not get any /dev/videox entries though.

When I try sudo somagic-capture --test-only I get an exit code of 0.

I have connected an old VCR playing an old tape to the EasyCAL device.
When I try sudo somagic-capture > /tmp/video.ts and let it run for several seconds I get masses of data into /tmp/video.ts but vlc does not display anything when I open it.

I have tried --cvbs-input with values from 1 to 4 but only 3 results in any data in /tmp/video.ts.

What vlc actually does is to display the GUI with the progress bar at the bottom.  When I selct /tmp/video.ts to play I get the 'pause' symbol at the bottom right for several seconds but it does not throw up the usual display window.

If I try to play the .ts file vith 'videos' it says:
'Could not determine type of stream.'

I had hoped to use vlc's capture facility but there is no /dev/videox device to put in the 'Video device name' box.

Any suggestions will be most welcome.

---

### Post by jordan59 on 2015-12-01
Try piping the uyvy video output of somagic-capture to vlc. This is an example from the documentation but for mplayer:
somagic-capture | mplayer -vf yadif,screenshot -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3 -
If that doesn't work, you might be able to pipe its output to gst-launch with fdsrc (I think?) and udpsink to stream to vlc. Actually you may as well skip the udpsink and vlc and just use a gstreamer plugin to encode it to mpeg2ts with filesink.

---

