---
title: "VLC on Ubuntu ~ No luck sending a stream!"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by Xama on 2006-12-06
Hello,

I am using Ubuntu 6.06 LTS (Dapper Drake) and I am struggling to get a Philips Webcam streaming ...

Let us say I am sending the video to 192.168.0.200

I select my webcam (a v4l device) and click the play locally and plug in the destination UDP address - 192.168.0.200. VLC selects MPEG-TS and I click OK to send.

Video is showing up on my end but VLC is saying
VLC media player 0.8.4 Janus
[00000288] main private error: cannot add this stream
[00000288] main private error: cannot add this stream

On the receive side I am getting an error:
main private error: cannot pre fill buffer

The webcam is working fine ... it is not the network because I tried this on a switch to localize it and still nothing ... no luck with HTTP either ...

I need some help ...

Thx

---

### Post by Puru on 2007-02-22
Are you able to stream media files? What if you use mmsh protocol? Are you streaming to Windows? Windows gives troubles with UDP traffic.

---

