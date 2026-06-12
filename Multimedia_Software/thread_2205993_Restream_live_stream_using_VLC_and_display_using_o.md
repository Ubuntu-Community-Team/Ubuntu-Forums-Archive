---
title: "Restream live stream using VLC and display using on web browser"
date: 2014-02-16
forum: Multimedia Software
---

### Post by andrew9 on 2014-02-16
[COLOR=#000000][FONT=Arial]I currently have a server and client connected through a tunnel using OpenVPN. My goal is to use the server to grab and restream the camera feed from the client, on the server using a HTML5 video tag or image tag (using mjpeg). The server has a public IP, so the idea is to allow people to view the client's video stream, through this server.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm using VLC, and using the graphical method, I'm able to view the video stream on VLC itself. I grabbed the stream, and restreamed it as mp4 (the first default profile). The steps I used are as follows:[/FONT][/COLOR]

[LIST=1]
[*]Media -> Stream -> Network Tab -> for network URL field, [http://10.8.0.6:8181/path/to/source/stream/](http://10.8.0.6:8181/path/to/source/stream/) -> Stream
[*]Next -> for the destination, change from File to HTTP -> check Display Locally -> Add
[*]for the Path field, I put /stream/live/
[*]Stream.
[/LIST]
[COLOR=#000000][FONT=Arial]The video shows in VLC, meaning if I use VLC to open a network stream, it works[/FONT][FONT=Arial], but when I add the following lines to my index.html file on the server to try to view it in a web browser, it is unsuccessful:[/FONT][/COLOR]
```
[COLOR=#800000]<video[/COLOR] [COLOR=#FF0000]id[/COLOR]=[COLOR=#0000FF]"id"[/COLOR] [COLOR=#FF0000]width[/COLOR]=[COLOR=#0000FF]"640"[/COLOR] [COLOR=#FF0000]height[/COLOR]=[COLOR=#0000FF]"480"[/COLOR] [COLOR=#FF0000]src[/COLOR]=[COLOR=#0000FF]"http://203.xxx.yyy.zzz:8080/stream/live/"[/COLOR] [COLOR=#FF0000]autoplay[/COLOR]=[COLOR=#0000FF]"autoplay"[/COLOR][COLOR=#800000]>[/COLOR]
[COLOR=#800000]</video>[/COLOR]
```
[COLOR=#000000][FONT=Arial]where 203.xxx.yyy.zzz is the public ip address of my server.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The video doesn't show; there's only a black screen. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I don't mind if it's not a graphical solution; a command line solution is fine too, or better yet, both. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
I also tried to use MJPEG to mux instead, so that I can simply display it on a webpage using an <img> tag (This would be preferred over using <video>). I created a new profile called "Video - MJPEG". Under the "Encapsulation" tab, I chose MJPEG. Under the "Video codec" tab, I checked "Video", chose the M-JPEG codec from the drop-down list, left Bitrate at 800kb/s, upped the frame rate to 30 fps, and put 1 for the resolution scale. Despite using this profile, the stream didn't show when I added<img src="203.xxx.yyy.zzz:8080/stream/live /> in my index.html. Please help![/FONT][/COLOR]

---

