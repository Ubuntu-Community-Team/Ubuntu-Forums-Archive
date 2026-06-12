---
title: "HDMI Audio Through the Browser"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Joe on 2010-05-02
I'm having problems getting audio to work via HDMI on a web browser (Firefox and Chrome). Initially I was unable to get audio through my HDMI cable at all but after some tinkering I was able to fix it with the exception of browser audio.  I'm pretty sure this is not a Flash issue because I can't get it to work when viewing Youtube or Vimeo videos in HTML5 either.  Analog audio via the headphone jack works fine.  I've got a HDA Intel device.  Any clues as to how I can get this fixed?

---

### Post by Joe on 2010-05-04
Just wanted to post an update in case anyone else also had this problem.  Well I got it solved by following the directions posted here under the Sound section:

[http://blog.mybarachois.com/b1/play/xbmc/htpc-nvidia-ion-1080pxbmcubuntu-guide/](http://blog.mybarachois.com/b1/play/xbmc/htpc-nvidia-ion-1080pxbmcubuntu-guide/)

The gist of it is that you had to create a .asoundrc file to tell Ubuntu to use a different sound card for audio through the browser.

---

