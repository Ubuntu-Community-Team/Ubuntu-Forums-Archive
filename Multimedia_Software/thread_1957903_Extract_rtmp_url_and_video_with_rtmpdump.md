---
title: "Extract rtmp url and video with rtmpdump"
date: 2012-04-13
forum: Multimedia Software
---

### Post by gallina94 on 2012-04-13
Hi all, 
i'm trying to extract video from this url
[http://www.web-tv.135.it/](http://www.web-tv.135.it/)
the channel is italia2. I'm able to get all the parameters to pass to RTMPDUMP using rtmpsuck. The final command is the following

rtmpdump -r "rtmp://edge3.786cast.tv/live/italia22" -a "live/italia22" -f "MAC 11,1,102,55" -W "http://www.786cast.tv/jplayr.swf" -p "http://www.786cast.tv?u=italia2&vw=500&vh=500" -y "13338442377083" -o prova.flv

but i get this error

RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
ERROR: RTMP_HashSWF: couldn't contact swfurl [http://www.786cast.tv/jplayr.swf](http://www.786cast.tv/jplayr.swf) (HTTP error 302)
Connecting ...
ERROR: RTMP_Connect0, failed to connect socket. 111 (Connection refused)

Anyone can help me?

Thanks

---

### Post by ron999 on 2012-04-13
> **gallina94 said:**
> 
Anyone can help me?

Hi
It's a "live" stream, so you need to add [COLOR="Red"]--live[/COLOR] or [COLOR="Red"]-v[/COLOR] to the command.

> @ubuntu:~$ rtmpdump -r "rtmp://edge3.786cast.tv/live/italia22" -a "live/italia22" -f "MAC 11,1,102,55" -W "http://www.786cast.tv/jplayr.swf" -p "http://www.786cast.tv?u=italia2&vw=500&vh=500" -y "13338442377083" -o prova.flv [COLOR="Red"]-v[/COLOR]
RTMPDump v2.4 7340f6d
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting Live Stream
ERROR: rtmp server sent error
INFO: Metadata:
INFO:   author                
INFO:   copyright             
INFO:   description           
INFO:   keywords              
INFO:   rating                
INFO:   title                 
INFO:   presetname            Custom
INFO:   creationdate          Fri Apr 13 11:36:44 2012
INFO:   videodevice           ManyCam Virtual Webcam
INFO:   framerate             25.00
INFO:   width                 320.00
INFO:   height                240.00
INFO:   videocodecid          avc1
INFO:   videodatarate         300.00
INFO:   avclevel              31.00
INFO:   avcprofile            66.00
INFO:   videokeyframe_frequency2.00
INFO:   audiodevice           Line in (e2eSoft VAudio)
INFO:   audiosamplerate       22050.00
INFO:   audiochannels         1.00
INFO:   audioinputvolume      90.00
INFO:   audiocodecid          .mp3
INFO:   audiodatarate         32.00
640.328 kB / 16.43 sec

---

### Post by gallina94 on 2012-04-13
many thanks...it works!!!!

---

### Post by pabloavegno on 2012-04-30
> **ron999 said:**
> Hi
It's a "live" stream, so you need to add [COLOR="Red"]--live[/COLOR] or [COLOR="Red"]-v[/COLOR] to the command.
Buen dia Ron !!! Veo que entendes del tema. Necesito tu ayuda para crear el comando necesario para poder grabar con el programa rtmpdump, el sitio web [http://www.786cast.tv/channel.php?u=telefetv.k25.net](http://www.786cast.tv/channel.php?u=telefetv.k25.net) Mil gracias por anticipado !! Pablo

---

### Post by ron999 on 2012-04-30
I need your help to create the necessary command to record the program rtmpdump, website [http://www.786cast.tv/channel.php?u=telefetv.k25.net](http://www.786cast.tv/channel.php?u=telefetv.k25.net)

Hi
I can't find it. ](*,)

Ask here ---> [http://stream-recorder.com/forum/]("http://stream-recorder.com/forum/")

---

