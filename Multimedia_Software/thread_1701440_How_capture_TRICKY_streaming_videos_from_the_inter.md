---
title: "How capture TRICKY streaming videos from the internet"
date: 2011-03-06
forum: Multimedia Software
---

### Post by montango on 2011-03-06
Hello,

I searched a lot and found no answer. Maybe you can help:

There is an internet page that displays streaming videos (TV shows) that are not detected by most Windows and Linux downloading software: Orbit, Replay Media Catcher (Windows) or Video Downloader, Downloadhelper, etc in Linux (ubuntu)

In Windows the only program that I managed to do the job with is "Stream Transport", and got .mp4 files that I could watch later.:D

But I don't have windows anymore, it is corrupted.:( In ubuntu, however, the many firefox add-ons, stand alone programs that I tested, don't see the video file.:confused: In the source of the page I don't understand anything, everything is concealed under javascript text... The video is not saved in the firefox cache.

How can I capture it? Does anybody know how to deal with this kind of well-concealed video files?:confused:

In theory, it should be possible to record everything that comes into the machine, but how?

Thanks in advance.

P.S. By TRICKY I mean something non-standard (not youtube, dailymotion, etc).

---

### Post by ron999 on 2011-03-06
Well first you need to know the URL of the webpage.

---

### Post by rayj on 2011-03-06
Have you tried copying the file directly out of /tmp?

---

### Post by montango on 2011-03-06
@ron999:

[http://inregistrari.antena3.ro/view-In_gura_presei_cu_Mircea_Badea-5.html](http://inregistrari.antena3.ro/view-In_gura_presei_cu_Mircea_Badea-5.html)

(for example)

@rayj:

the flash file is not stored in /tmp, nor in firefox cache, or at least I haven't found it.

---

### Post by ron999 on 2011-03-06
@montango
That video can be downloaded using a program called RTMPDump.

```
sudo apt-get install rtmpdump
```

Then use this command:-
```
rtmpdump -r "rtmpe://fms30.mediadirect.ro:1935/recantena3?id=14458935" -a "recantena3?id=14458935" -f "LNX 10,1,102,64" -W "http://static.mediadirect.ro/streamrecord/new3/player.swf" -p "http://inregistrari.antena3.ro/view-In_gura_presei_cu_Mircea_Badea-5.html" -C O:1 -C O:0 -y "mp4:In_Gura_Presei_2011-03-03_23-10-00_low.mp4" -o mp4_In_Gura_Presei_2011-03-03_23-10-00_low.flv
```

---

### Post by montango on 2011-03-06
Thanks, ron999!:KS

Works great! A little tricky, however, if I choose to download a show from another day (I have to put the correct date between "...view" and "In_gura_presei...", but I just tried and it works, too!:D

I'll figure out for myself how to use rtmpdump for other pages. Thanks a lot for now!

---

### Post by montango on 2011-03-06
Actually, this doesn't seem to be  very easy, unless I do the same thing for the same show, but for other dates... How did you get all the parameters? I only found 

[http://static.mediadirect.ro/streamrecord/new3/player.swf](http://static.mediadirect.ro/streamrecord/new3/player.swf)

in the page source, but I still have no idea what mean

-r "rtmpe://fms30.mediadirect.ro:1935/recantena3?id=14458935" -a "recantena3?id=14458935" -f "LNX 10,1,102,64"

As for the names of the files, I remember that Stream Transport did name them similarly indeed, so there must be a rule...

This still looks tricky to me...

I suppose the fact I don't know what rtmp is doesn't bring me any further...

---

### Post by ron999 on 2011-03-06
Hi montango
Use [FONT="Courier New"]**rtmpdump -h**[/FONT] for help.

Look at your command:-

rtmpdump 
-r "rtmpe://fms30.mediadirect.ro:1935/recantena3?id=14458935" 
-a "recantena3?id=14458935" 
-f "LNX 10,1,102,64" 
-W "http://static.mediadirect.ro/streamrecord/new3/player.swf" 
-p "http://inregistrari.antena3.ro/view-In_gura_presei_cu_Mircea_Badea-5.html" 
-C O:1 
-C O:0 
-y "mp4:In_Gura_Presei_[COLOR="Red"]2011-03-03[/COLOR]_23-10-00_low.mp4" 
-o mp4_In_Gura_Presei_[COLOR="Red"]2011-03-03[/COLOR]_23-10-00_low.flv

Maybe keep everything the same except for those -y and -o dates.

---

### Post by ron999 on 2011-03-06
Hi montango

I use this method to find the links:-

1) Start the server.
```
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT && rtmpsrv
```
Message in terminal is:- "**Streaming on rtmp://0.0.0.0:1935**"

2) Refresh the page and start the video.

3) Watch for links to display in terminal... then

4) Use control-C to stop the process.

5) Stop the server.
```
sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -j REDIRECT
```

6) Copy and paste your links to download the video.
:cool:

---

### Post by montango on 2011-03-06
Hm... It doesn't work anymore:confused:

Now I found the links, but when I type tyem, it says

RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: RTMP_Connect0, failed to connect socket. 111 (Connection refused)

And it says so for the commands that already worked before..:confused:

I don't get it:confused:

---

### Post by ron999 on 2011-03-06
Re-boot montango.

---

### Post by montango on 2011-03-06
I made a mistake (-A instead of -D in the second command - to close the server), and afterwards there was nothing to do, even if I tried to rewrite the right command. Now I restarted the machine and it seems to work.
(You probably notice that I'm still not 100% confident, as I don't understand why it didn't work before, but I hope I will some day)

Sorry to bother you.

Thanks again!

P.S. Oh, I just saw you told me to re-boot. So I was right to do so. If I understand well, iptables deals with some kind of firewall, with which I probably shouldn't mess up... I'll be more careful

---

### Post by montango on 2011-03-09
I was too hasty to mark the thread as SOLVED; the files I managed to dowload are full of errors and cannot b watched:

regardless where I click on the timeline of the video, after a few seconds the video player crashes (Totem Movie player or VLC) with 4 error messages (4 small windows on top of each other):

Disconnected: Connection terminated

pa_stream_cork() failed: Connection terminated

Disconnected: Connection terminated

pa_stream_writable_size() failed: Connection terminated


So maybe there are a few things to set...

ron999, can you please help me with that?

---

### Post by ron999 on 2011-03-09
> **montango said:**
> ... after a few seconds the video player crashes ...

So maybe there are a few things to set...


Hi montango
Yes, I agree, there's something wrong with the downloaded files from In_Gura_Presei.
Try again with addition of **-v** to your command.
This seems to cure the problem,:D
though the download time is much longer.:( 'Real-time'.


> .......low.mp4" -o mp4_In_Gura_Presei_2011-03-08_23-10-00_low.flv [COLOR="Red"]-v[/COLOR]

```
rtmpdump -r "rtmpe://fms30.mediadirect.ro:1935/recantena3?id=14656841" -a "recantena3?id=14656841" -f "LNX 10,1,102,64" -W "http://static.mediadirect.ro/streamrecord/new3/player.swf" -p "http://inregistrari.antena3.ro/view-08_Mar-2011-In_gura_presei_cu_Mircea_Badea-5.html" -C O:1 -C O:0 -y "mp4:In_Gura_Presei_2011-03-08_23-10-00_low.mp4" -o mp4_In_Gura_Presei_2011-03-08_23-10-00_low.flv [COLOR="Red"]-v[/COLOR]

```

---

### Post by montango on 2011-03-09
Thanks, ron999, I will test this later, from the office; from my hotel room, the network is configured such that I cannot access rtmp streams, but what you say is somehow confirmed by my experience with StreamTransport under Windows: it only records in real time, while other programs (Replay Media Catcher, Orbit Downloader) record much faster (but can not access the streams that I want).

By the way, are you familiar with wireless issues? I can access only unsecure wl networks, it doesn't recognise the (correct) password on secure ones (I've posted a thread [here]("http://ubuntuforums.org/showthread.php?p=10540388#post10540388"))

---

### Post by Malcom89 on 2011-11-13
Hi!

I trying download clip from [http://video.homelessworldcup.org/?cpak=3412165343567627&pak=1513287754057413](http://video.homelessworldcup.org/?cpak=3412165343567627&pak=1513287754057413)

I just try everything... and still same problem: ERROR: RTMP_Connect0, failed to connect socket. 111 (Connection refused)

Any tips?

```

malcom@Malcom-Linux:~$ rtmpdump -V -r "rtmp://ll2.workcast.net/vod1/Game300-LanguageXXX-Rec1_0_20110828151412811_1.mp4" -o plik.flv -W "http://c466722.workcast.net/flowplayer.commercial-3.2.5.swf" -f "LNX 10,1,102,64" -C O:1 -C O:0 -y "mp4:Game300-LanguageXXX-Rec1_0_20110828151412811_1.mp4" -p "http://video.homelessworldcup.org/?cpak=3412165343567627&pak=1513287754057413"
RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
DEBUG: Parsing...
DEBUG: Parsed protocol: 0
DEBUG: Parsed host    : ll2.workcast.net
DEBUG: Parsed app     : vod1
DEBUG: Protocol : RTMP
DEBUG: Hostname : ll2.workcast.net
DEBUG: Port     : 1935
DEBUG: Playpath : mp4:Game300-LanguageXXX-Rec1_0_20110828151412811_1.mp4
DEBUG: tcUrl    : rtmp://ll2.workcast.net:1935/vod1
DEBUG: swfUrl   : http://c466722.workcast.net/flowplayer.commercial-3.2.5.swf
DEBUG: pageUrl  : http://video.homelessworldcup.org/?cpak=3412165343567627&pak=1513287754057413
DEBUG: app      : vod1
DEBUG: flashVer : LNX 10,1,102,64
DEBUG: live     : no
DEBUG: timeout  : 30 sec
DEBUG: SWFSHA256:
DEBUG: 57 27 9d 7f b1 fa 20 a2 8a 1d b1 7e 51 3a bf 78
DEBUG: 61 60 7d a7 4d 2c f5 4b aa e8 23 5a e3 e3 cf f6
DEBUG: SWFSize  : 239973
DEBUG: Setting buffer time to: 36000000ms
Connecting ...
ERROR: RTMP_Connect0, failed to connect socket. 111 (Connection refused)
DEBUG: Closing connection.

```

---

### Post by ron999 on 2011-11-13
> **Malcom89 said:**
> 
Any tips?

Ask here --> [http://stream-recorder.com/forum/rtmpdump-f54.html]("http://stream-recorder.com/forum/rtmpdump-f54.html")

---

### Post by aliaomt on 2012-12-28
> **ron999 said:**
> Hi montango

I use this method to find the links:-

1) Start the server.
```
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT && rtmpsrv
```Message in terminal is:- "**Streaming on rtmp://0.0.0.0:1935**"

2) Refresh the page and start the video.

3) Watch for links to display in terminal... then

4) Use control-C to stop the process.

5) Stop the server.
```
sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -j REDIRECT
```6) Copy and paste your links to download the video.
:cool:

Wow!!!
That was great.
It work for videolectures.net
I tried thousands of tricks but this one worked well!
Now i downloading an rtmp stream video from videolectures
thanx

---

