---
title: "How do I get a RTSP stream from my camera?"
date: 2013-08-28
forum: Multimedia Software
---

### Post by Maheriano on 2013-08-28
I bought a cheap D-Link DCS-930L wireless IP camera and I'm trying to access the stream any way I can. Either by RTSP or MJPG, I don't really care. I've put more research time into trying to figure out RTSP so far but cannot get it working. All I have right now is the camera and my client machine, do I need anything else? I see tutorials talking about a server, is this required? Can it be the same machine as my client? Do I need to download RTSP and install it? Do I need a camera which supports RTSP or do they all support it? Thanks.

---

### Post by Maheriano on 2013-08-29
Here's the solution I came up with yesterday.
I tried everything to get RTSP to work with this camera but eventually figured it out that this camera doesn't support RTSP, it only supports MJPG. So in order to see the stream from it in VLC, I used this URL: [http://192.168.1.119/MJPEG.CGI?.mjpeg](http://192.168.1.119/MJPEG.CGI?.mjpeg). The IP provided is the IP of the camera on my network, you'll have to modify that to match your IP. I also figured out that VLC doesn't support .cgi streams so I had to append the "?.mjpeg" to the end of the URL to force it to open it as a MJPG stream.

---

