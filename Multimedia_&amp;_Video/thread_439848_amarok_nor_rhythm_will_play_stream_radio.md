---
title: "amarok nor rhythm will play stream radio"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by firedancer on 2007-05-11
after reinstalling ubuntu i have a problem thnx to winxp who crashed on my dual boot system


only totem will play dvd and stream installing gstreamer

but amarok and rhythm 'say' something like unble to get plug in : cook.so


what can i do totem sucks a little on stream (cracks) 

is there another plug in that i can install , there are many, so i've got to find the right one 

need help pls.

---

### Post by firedancer on 2007-05-11
any help here !!

pls.

---

### Post by firedancer on 2007-05-11
where do i get plug ins realplayer G2 , cause that is what  it asks 

it's not in synaptic


anyone pls?


getting frustrated :confused:

---

### Post by chestnut1969 on 2007-05-15
I  had the same issue with gxine in xubuntu (Feisty)

Install multimedia codecs (the good, the bad and the ugly!). You may not require all of these, I installed all as I required them, and the streaming issue was resolved.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Scroll down to section " How to install Multimedia Codecs"

sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

sudo aptitude install w32codecs

plus the meta package ubuntu-restricted-extras


Cheers

---

### Post by firedancer on 2007-05-15
thnx still


was busy in that department !

---

