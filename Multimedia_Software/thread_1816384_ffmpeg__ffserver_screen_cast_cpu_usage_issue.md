---
title: "ffmpeg / ffserver screen cast cpu usage issue"
date: 2011-08-01
forum: Multimedia Software
---

### Post by mozart_ar on 2011-08-01
Hello, 
 I am trying to use the approach ffmpeg/ffserver to capture screen and publish it as a stream. 
 I got it works, but as soon I launch ffserver, it uses 100% of CPU. Some idea?

Below the file /etc/ffserver.conf 

```

Port 8090

BindAddress 0.0.0.0
MaxHTTPConnections 2000
MaxClients 1000
MaxBandwidth 1000
CustomLog -
NoDaemon

<Feed desktop.ffm>
	File /tmp/desktop.ffm
	FileMaxSize 10M
	Launch ffmpeg -f x11grab -r 25 -s 1024x768 -i :0.0
</Feed>


<Stream desktop.mjpg>
	Feed desktop.ffm
	Format mpjpeg

	VideoCodec mjpeg

	VideoFrameRate 1
	VideoSize 640x480
	VideoIntraOnly
	NoAudio
	Strict -1

	ACL allow localhost
	ACL allow 192.168.0.0 192.168.255.255
</Stream>

<Stream stat.html>
Format status
ACL allow localhost
ACL allow 192.168.0.0 192.168.255.255
</Stream>

<Redirect index.html>
   URL http://www.ffmpeg.org/
</Redirect>

```

---

