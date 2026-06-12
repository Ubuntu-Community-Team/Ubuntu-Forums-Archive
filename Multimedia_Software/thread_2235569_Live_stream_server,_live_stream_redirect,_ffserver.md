---
title: "Live stream server, live stream redirect, ffserver, ffmpeg, VLC, rtmp"
date: 2014-07-21
forum: Multimedia Software
---

### Post by axetone on 2014-07-21
Hi,
  I have a website that I would like to allow a weekly stream from. I am currently using two machines to perform this effort which is described below. There are several concerns that I would like to mitigate before continuing;

1. I am using Ubuntu server (non-GUI) as my primary webserver running Apache2. I am NOT interested in ANYTHING GUI (unless it's a webpage driven architecture) so please do NOT offer GUI related advice!

2. The current setup is as follows:
1080p-HD-Cam configured on Win7, running VidStudio streaming production software. This (AMAZING!) software has the ability to stream to any IP:port combination with massive codec and compression support...~so I have the "source" (as it were) completed. Note: I am not running this full-HD before anyone asks.

3. The server (Ubuntu 12.04 precise) is running Apache2 webserver, and my NEED (question 1) is to have software configured to "capture, and then re-stream the feed from the win7 source".

4. Although I am intending to stream to the internet via my website (NOT A LAN BROADCAST!),  I am _**not**_ seeking to use any external services such as Ustream, LiveStream, etc..etc...or even paid streaming servers such as icecast, adobe, etc..etc. My goal is to capture the feed and re-stream using only 100% open-source freeware. (i.e. ffserver, vlc, ffmpeg..._or anything that will get the job done_.)

5. Firewall issues AND bandwidth fine/good/resolved.

6. I have read everything I can about each of these softwares above noted and everything I've read forces you to either stream from the source system (i.e. a web-cam) using VLC GUI on the source/feed PC, or from a static file (mpeg, etc) from the local web-server...none of which is helpful.

--------------------
CAMERA - (usb) - LAPTOP -->UDP--> SERVER - (re-stream via my-website) - Client 0
                                                                      - Client 1
                                                                      - Client 2
                                                                      - Client N--------------------

~also, I am including several links which describe what I am trying to do, and those persons solutions, but fail completely in hopes that someone will have pity on me and provide more info on a free open-source way to "capture and re-stream a live feed on Ubuntu server -CLI-only".

Please and thank you (in advance!!!)
Signed -two weeks reading and none-the-better for it!

_**Example setups I tried but are incomplete**_:
1.  (This one does not show how to capture stream using UDP...so I'm not sure if this is something that needs to be captured and saved to a local file, buffered, then re-streamed..??, because the errors I get sunig VLC, and FFserver say "cannot open local-file" (as if it needs a place to store the stream, so I don't know what it's actually doing...?)
[https://trac.ffmpeg.org/wiki/Streaming%20media%20with%20ffserver](https://trac.ffmpeg.org/wiki/Streaming%20media%20with%20ffserver)

2. This on is similar to my physical setup, but requires an SSH connection between the laptop(source) and the server...-which, #1 I already have production software and will not be using VLC due to its limited-/-single video source-stream, and #2 the overhead of an SSH connection between to nodes on the same network seems preposterous and unnecessary.
[http://serverfault.com/questions/288137/how-to-stream-live-video-from-a-linux-server/288227#288227](http://serverfault.com/questions/288137/how-to-stream-live-video-from-a-linux-server/288227#288227)

3. Everything else I've read just streams direclty a single attached device (i.e. camera) using vlc, or ffmpeg on the lcoal server out to the internet...~which defeats the isolation of the production from the webserver-ing, and also limits the bandwidth (et al).

------------SOoooooo...anyone??? Little help...PLEASE! ->THANK YOU!!

---

### Post by axetone on 2014-07-22
UPDATE:
It appears that the raw-UDP sent from the vidStudio applicaiton on my win7 laptop is not well received by the ffserver component on my Ubunutu server. I ran some wireshark and wow...that software truly saturates the local network well!

So, as a workaorund I have found that using Adobe Flash Media Encoder does infact recognize the "complete output production stream" from vidStudio as a single "input source"...AWESOME!!! This means that I can simultaneously capture, record, and encode/stream FLV on the laptop directly over the ffserver (Ubuntu).

My next challenge in resolving this "solution" will be to get ffserver to capture the stream, and restream it out to my website.

-not resolved but making progress! :guitar:

---

### Post by axetone on 2014-07-22
NOTE: edit not working...wanted to repost with correction...

[COLOR=#000000]UPDATE:[/COLOR]
[COLOR=#000000]It appears that the raw-UDP sent from the vidStudio applicaiton on my win7 laptop is not well received by the ffserver component on my Ubunutu server. I ran some wireshark and wow...that software truly saturates the local network well![/COLOR]

[COLOR=#000000]So, as a workaorund I have found that using Adobe Flash Media Encoder does infact recognize the "complete output production stream" from vidStudio as a single "input source"...AWESOME!!! This means that I can simultaneously capture, record, and encode/stream FLV on the laptop *_**AND THEN SEND-STREAM**_* directly over the ffserver (Ubuntu).[/COLOR]

[COLOR=#000000]My next challenge in resolving this "solution" will be to get ffserver to capture the stream, and restream it out to my website.[/COLOR]

[COLOR=#000000]-not resolved but making progress![/COLOR]

---

