---
title: "&quot;/!\ Cannot open audio device.&quot; Pianobar error."
date: 2014-10-23
forum: Multimedia Software
---

### Post by CalebW on 2014-10-23
Hello, I'm running 14.04 and everything is up-to-date.
When using pianobar(latest git), after a few songs it starts playing scrambled audio and rushing through the songs at 8 secs/sec. Same issue as this: [https://github.com/PromyLOPh/pianobar/issues/432](https://github.com/PromyLOPh/pianobar/issues/432) 

The solution mentioned is to replace ```
default=alsa
dev=default
``` with ```
default=pulse
``` in the /etc/libao.conf file. When I do this, all of my other sound applications still work. VLC, Totem, Firefox(youtube, etc.), but when I try to start pianobar I get "/!\ Cannot open audio device."

Any help would be greatly appreciated, I've looked all over goolge, but I can't find anything that works for me. And I'm tired of haveing to restart pianobar every few songs.

Edit: 
Stupid me, I changed the /etc/libao.conf, but I forgot I had a  ~/.libao.conf also which was conflicting with the global config. Deleted  ~/.libao.conf and everything works now.

---

### Post by snakebones on 2015-05-01
for this to work i needed to use *default_driver=pulse*

---

