---
title: "Video Streaming Errors in Jaunty - Need help"
date: 2010-01-26
forum: Multimedia Software
---

### Post by TMVirginia on 2010-01-26
I have vlc installed on two Ubuntu 9.04 boxes. Locally, each of the boxes player working ok. However, when I try to stream video from one machine to the other over ethernet connection I get errors. Following are the command lines I executed for the video streaming.
 On machine A (IP: 123.123.90.10, where the video will be streamed from):
  vlc -vvv samplevideo.mov --sout '#standard{access=udp,mux=ts,dst=123.123.90.5:1234}'

On machine B (IP: 123.123.90.5, where the video will be streamed to)
 vlc -vvv udp://123.123.90.5:1234

 On machine A (where the video is streamed from) I get the errors:
  access_output_udp access out debug: late packet for UDP input
  access_output_udp access out debug: packet has been sent too late
  access_output_udp access out warning: send error: Connection refused

On machine B (where the video is streamed to) the errors are:
  Client: main stream error: cannot pre fill buffer
 Client: main stream warning: cannot create a stream_t from access

  Any idea? Help is appreciated.;)

---

