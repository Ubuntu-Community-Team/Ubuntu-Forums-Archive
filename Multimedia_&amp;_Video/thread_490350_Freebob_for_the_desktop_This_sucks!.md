---
title: "Freebob for the desktop? This sucks!"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by linkx on 2007-07-02
I'm using an external firewire audio card with my MacBook Pro. Using jackd with the FreeBob driver works great . . . for Jack'd applications. The problem--and it is HUGELY annoying :-x -- is that "normal" desktop applications (Totem, Rhythmbox, Flash, etc.) are blissfully ignorant of the firewire audio device.

So, when I'm entertaining friends with my shiny UbuntuStudio MacBook and I want to play a video from YouTube, the audio fails to play through my fancy firewire card and professional speakers, and instead gets piped through my crappy little laptop speakers. 

It is quite embarrassing to inform them that my "awesome" UbuntuStudio does not know how to play normal audio through my firewire device. "Sorry guys, I have to reboot into OS X, or . . . Vista in order to hear the audio from my expensive professional soundcard" 

So, my question is, Can Freebob devices be used by general, non-jack'd apps like Flash and Totem? 

Is is possible to tell Ubuntu to use the freebob driver system-wide, like ALSA or OSS?

---

### Post by christhemonkey on 2007-07-02
In Feisty, Apps using Gstreamer can output through jackd with gstreamer0.10-plugins-bad installed) so apps like totem should work fine as should youtube vids.

---

### Post by linkx on 2007-07-02
Awesome. I will try this when I get home.

---

### Post by Das Oracle on 2007-07-02
let us know how it works out for you.

---

### Post by linkx on 2007-07-02
OK got gstreamer-plugins-bad installed . . . now what? still no JACK presence.

---

### Post by Nighto on 2007-07-02
[http://ubuntuforums.org/archive/index.php/t-208488.html](http://ubuntuforums.org/archive/index.php/t-208488.html)
[http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=XgB&q=oss2jack+ubuntu+feisty&btnG=Search](http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=XgB&q=oss2jack+ubuntu+feisty&btnG=Search)

---

### Post by christhemonkey on 2007-07-03
Can you provide the output of these commands?:
```
gst-inspect jackaudiosink 
```


And then if you have jack launched you should be able to do this and here a test noise:
```
gst-launch audiotestsrc ! audioconvert ! audioresample ! jackaudiosink 
```

---

