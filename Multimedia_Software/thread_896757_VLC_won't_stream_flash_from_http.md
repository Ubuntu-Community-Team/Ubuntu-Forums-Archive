---
title: "VLC won't stream flash? from http"
date: 2008-08-21
forum: Multimedia Software
---

### Post by cdoss on 2008-08-21
Hi, I've got another VLC-won't-stream problem.  I'm running ubuntu 8.04.

I have installed vlc, as well as w32codecs.  I am trying to use VLC to open a stream on the internet, such as a youtube video.  For youtube, I cut and paste the web address contained in the little "embed" bar  (minus all the http stuff) into the HTTP/HTTPS/FTP/MMS box in VLC's open->network.  I get 
"Unrecognized format for 'Content-Type: application/x-shockwave-flash'" error.  Do i need to install a shockwave or flash plugin?  Am i using the wrong address?  Should VLC be able to play youtube videos (without using the vlc firefox plugin)?  i.e. if i'd like to save a youtube video to my harddrive, is that technically possible?

Also a related question: if streaming content is embedded in a webpage, how do i go about trying to discover what is the actual address I need for just the content, not the webpage?  

Thanks!











Some extra information:

--output of "dpkg -l *vlc*" :
ii  libvlc0        0.8.6.release. multimedia player and streamer library
ii  mozilla-plugin 0.8.6.release. multimedia plugin for web browsers based on 
ii  vlc            0.8.6.release. multimedia player and streamer
un  vlc-aa         <none>         (no description available)
un  vlc-arts       <none>         (no description available)
un  vlc-esd        <none>         (no description available)
un  vlc-ggi        <none>         (no description available)
un  vlc-glide      <none>         (no description available)
un  vlc-lirc       <none>         (no description available)
un  vlc-mad        <none>         (no description available)
ii  vlc-nox        0.8.6.release. multimedia player and streamer (without X su
un  vlc-plugin-a52 <none>         (no description available)
un  vlc-plugin-aa  <none>         (no description available)
ii  vlc-plugin-als 0.8.6.release. dummy transitional package
ii  vlc-plugin-art 0.8.6.release. aRts audio output plugin for VLC
un  vlc-plugin-dv  <none>         (no description available)
un  vlc-plugin-dvb <none>         (no description available)
ii  vlc-plugin-esd 0.8.6.release. Esound audio output plugin for VLC
ii  vlc-plugin-ggi 0.8.6.release. GGI video output plugin for VLC
ii  vlc-plugin-gli 0.8.6.release. Glide video output plugin for VLC
un  vlc-plugin-lir <none>         (no description available)
un  vlc-plugin-mad <none>         (no description available)
un  vlc-plugin-ogg <none>         (no description available)
ii  vlc-plugin-pul 0.8.6.release. Pulseaudio audio output plugin for VLC
ii  vlc-plugin-sdl 0.8.6.release. SDL video and audio output plugin for VLC
ii  vlc-plugin-svg 0.8.6.release. SVGAlib video output plugin for VLC
un  vlc-plugin-xos <none>         (no description available)
un  vlc-pulse      <none>         (no description available)
un  vlc-sdl        <none>         (no description available)
ii  wxvlc          0.8.6.release. dummy transitional package

---

### Post by wolfen69 on 2008-08-21
here's a quick tip. after you watch a youtube vid, open nautilus and go to /tmp

you will find the video there. it will be replaced as soon as you start another youtube vid though.

---

### Post by cdoss on 2008-08-21
Oh, thanks :).  Do you know if VLC should play flash, though?  or not?

---

