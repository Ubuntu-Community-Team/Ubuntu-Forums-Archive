---
title: "Looking for a basic webcam streaming solution."
date: 2011-10-13
forum: Multimedia Software
---

### Post by bpneiman on 2011-10-13
If this is not posted in the correct section, please forgive me.

What I want to accomplish:
- No Audio Required -
Stream live video from home and view in web browser
[or]
Log into home server to view current image/video webcam.

What I have:
Ubuntu 11.04 LAMP server (all functioning well) - No GUI.
Logitech Webcam Pro 9000 (working)
A domain name.

I am trying to come up with a fairly "painless" solution to this.  I have tried webcam-server, but it seems to no longer be supported.  I could bring up a still image from the cam, but could not refresh unless I restarted the webcam-server service.

I have looked into ffserver, but every solution I seem to have found is geared towards something more complicated than what I am trying to accomplish.

Can this be accomplished with a VLC "server"?  I don't want to record.  I don't want to be able to rewind.  I just want the current view, streaming if possible.

Any other suggestions are appreciated.

---

### Post by CindyP on 2011-11-25
bpneiman,  Did you get this figured out?  I have very similar requirements except I do want sound.  I am just getting started so I found this unanswered thread.  I hope someone chimes in with a suggestion.

---

### Post by josvanr on 2012-01-08
bump I also need this?.....

josvanr

---

### Post by Derek Karpinski on 2012-01-09
I think ffmpeg, and ffserver are your best bet.  VLC is capable, but if you're running a server, why install a huge VLC package, and stream with it.  It's not very lightweight.

---

### Post by samsunix on 2012-01-19
Try throw these in console:

```
 cvlc v4l2:///dev/video0 --sout '#transcode{vcodec=x264{keyint=60,idrint=2},vcodec=h264,vb=200,ab=32,fps=25,width=400,height=226,acodec=mp3,samplerate=44100}:duplicate{dst=std{access=http{mime=video/x-flv},mux=ffmpeg{mux=flv},dst=:8082/stream.flv}'
```

If you have error messages throw these first:

```
sudo chmod 777 /dev/video0
```


1. Make own folder for streaming inside www folder

```
sudo mkdir /var/www/stream
```


2. Fix user rights

```
sudo chmod 777 /var/www/stream
```


3. Move to streams folder and download flowplayer

```
cd /var/www/stream
wget http://samuliweb.dyndns.org/~samsunix/player/flowplayer-3.2.7.swf
wget http://samuliweb.dyndns.org/~samsunix/player/flowplayer-3.2.6.min.js
wget http://samuliweb.dyndns.org/~samsunix/player/style.css (optional)

``` 


4. Next we make html file for webcam
```
 sudo nano /var/www/stream/webcam.html 
```

copy paste these:

> <html><head>
<meta http-equiv="content-type" content="text/html; charset=UTF-8">
<!-- A minimal Flowplayer setup to get you started -->


        <!--
                include flowplayer JavaScript file that does
                Flash embedding and provides the Flowplayer API.
        -->
        <script type="text/javascript" src="flowplayer-3.2.6.min.js"></script>

        <!-- some minimal styling, can be removed -->
        <link rel="stylesheet" type="text/css" href="style.css">

        <!-- page title -->
        <title>My Webcam Stream</title>

</head><body>

        <div id="page">

                <h1>-=WEBCAM=-</h1>

                <p>lol</p>

                <!-- Change line href="?" more suitable -->
                <a
                         href="http://your.server.ip.address:8082/stream.flv"
                         style="display:block;width:400px;height:225px"
                         id="player">
                </a>

                <!-- Location of flowplayer -->
                <script>
                        flowplayer("player", "http://your.server.ip.address/stream/flowplayer-3.2.7.swf");
                </script>

        </div>


</body></html>


now open browser and give it a try
[http://your.server.ip.address/stream/webcam.html](http://your.server.ip.address/stream/webcam.html)

Here's my demo page: [http://samuliweb.dyndns.org/stream](http://samuliweb.dyndns.org/stream)

Opening stream with browser may take a while so give it a time. I am working to solve these. Meanwhile you can just refresh page with F5 until it gives a go.

---

### Post by mudguts on 2012-07-05
I realize that this thread is a few months old but I'd really like to do this stil
I get a 404 on some of the http files.
any ideas where I can get them from?

---

### Post by pgp_protector on 2012-07-06
> **mudguts said:**
> I realize that this thread is a few months old but I'd really like to do this stil
I get a 404 on some of the http files.
any ideas where I can get them from?

Found this thread looking for a streaming server also.

Found the source files at
[http://flow-player.googlecode.com/files/flowplayer-3.2.6.min.js](http://flow-player.googlecode.com/files/flowplayer-3.2.6.min.js)
[http://flow-player.googlecode.com/files/flowplayer-3.2.7.swf](http://flow-player.googlecode.com/files/flowplayer-3.2.7.swf)

But it didn't work for me, but that may be due to my hardware (Dazzle DVC100)  still working on that :)

but the links are good.

---

### Post by pgp_protector on 2012-07-06
FYI I found that Motion works quite well.
[http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome)

---

