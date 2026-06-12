---
title: "Streaming via own (internet) server and Webcam at second PC"
date: 2016-12-13
forum: Multimedia Software
---

### Post by phibuntu on 2016-12-13
Hi everybody

I have just started installing a webcam and the image is good enough (testet using GUVCView). 
Now I want to stream this via our own webserver into the internet.
I have seen many tutorials, but I am a bit lost, because of the various possibilities and also because many tutorials use twich.tv or others and most do not tell, which software has to be installed on which machine (I have two!).

Conditions:
* I have my webcam connected to a linux box (Machine A) (no Domain-Name and only local IP-Adress).
* I have a webserver (also linux) standing in the internet (Domain and IP in the internet). Call this Machine B.

I want to stream from the first machine (A) to the second Machine (B) and place the stream into a website which lies on Machine B.

Quality is not very important and there is no sound to be streamed.

What would you suggest?

For me important is the information about which software has to be installed on (A) and which on (B).

Many thanks to all you "streamers" for simple ideas.


What I have done so far:

First addition:

On machine B I installed nginx (1.10.2)using the following tutorial:
[https://obsproject.com/forum/resources/how-to-set-up-your-own-private-rtmp-server-using-nginx.50/](https://obsproject.com/forum/resources/how-to-set-up-your-own-private-rtmp-server-using-nginx.50/)
For that I had to change port 80 to another port number for http in /usr/local/nginx/conf/nginx.conf.
Unfortunately the tutorial ends when it comes to OBS (Open Broadcast Software), which can not be installed on my Machine A, where OpenGL is only available in version 2.0...


On Machine A I use ffmpeg (instead of the unsupported OBS) to stream using something like:
fmpeg -f alsa -f v4l2 -i /dev/video0 -s 320x240 -ar 11025 -f flv -r 10.0 "rtmp://myserver/live"

Now, I wonder, what would be a simple ffmpeg-config and what is this about the often mentioned <Stream Key>
Any Idea? Any tutorials?

---

### Post by phibuntu on 2016-12-14
Found a part of the solution myself!

I had to add a simple key at the end of the url.

**Finally put together, what I have until now:**

[COLOR="#0000CD"]**Streming-Server (Machine B)**[/COLOR]
Starting nginx-Server installation on Machine B like described in this tutorial:

[https://obsproject.com/forum/resourc...sing-nginx.50/](https://obsproject.com/forum/resourc...sing-nginx.50/)

I have changed port 80 (http) to port 8765, so I don't mess up with my apache webserver. But I added the rtmp-section to /usr/local/nginx/conf/nginx.conf as described using port 1935.

The server started right away on my lubuntu webserver (Machine B).

[COLOR="#0000CD"]**Webcam-Machine(A)**[/COLOR]
On Machine A (also lubuntu) I installed ffmpeg. To test I used GUVCView, which hangs at /dev/video0.
Starting

>ffmpeg -i /dev/video0 -f flv -r 12 "rtmp://MY-SERVER.COM:1935/live/MYKEY"

This starts to stream to nginx machine B (which is MY-SERVER.COM:1935).

[COLOR="#0000CD"]**CLIENTS**[/COLOR]
From Clients I can now see my webcam through 
rtmp://MY-SERVER.COM:1935/live/MYKEY

Single problem remaining:
How do I embed this URL into a web-page? I tried several <object> and <embed> Tags form the internet, but I have found nothing that works in firefox.

---

