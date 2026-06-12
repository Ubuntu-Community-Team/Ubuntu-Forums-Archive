---
title: "Chromecast unable to find TV"
date: 2021-04-03
forum: Multimedia Software
---

### Post by asb3 on 2021-04-03
I want to use chromecast to display media (or desktop, if possible) on my TV.  I have a TV with built-in chromecast.  

I can share my android tablet screen using an app called "Screen mirroring stream".  The app sees my TV, which is on my local network.

I have chrome, VLC, and mkchromecast installed on my linux box (running Ubuntu 20.04).   
From Chromium, when I select "cast", I get the "Cast Tab" with the message "Searching for devices".  After a few seconds, I get the message "No devices found".

Running VLC, I have a similar problem
Playback->Renderer
only gives one option, "Local".

Running mkchromecast, same problem:
(base) asb@cavu> mkchromecast
Mkchromecast v0.3.8.1
Creating Pulseaudio Sink...
Open Pavucontrol and Select the Mkchromecast Sink.
Starting Local Streaming Server
[Done]
Selected backend: parec
Selected audio codec: mp3
Default bitrate used: 192k
Default sample rate used: 44100Hz.
 * Serving Flask app "mkchromecast.audio" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
PID of main process: 7096
   Use a production WSGI server instead.
PID of streaming process: 7102
 * Debug mode: off
 * Running on [http://0.0.0.0:5000/](http://0.0.0.0:5000/) (Press CTRL+C to quit)
No devices found!
Cleaning up /tmp/...
[Done]
Killed

What do I have to do to permit chromecast to see my TV?

---

### Post by crip720 on 2021-04-03
Would try with Chrome instead.  Google does something so that only their products work well together.  Only have chrome for videostream app that seems able to play/convert easy to chromecast.  Other casting apps seem to really work my laptop trying to cast to chromecast.

---

