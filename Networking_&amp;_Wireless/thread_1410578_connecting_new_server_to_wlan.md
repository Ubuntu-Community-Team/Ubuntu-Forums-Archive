---
title: "connecting new server to wlan"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by zander1013 on 2010-02-18
hi,

i just setup a new ubuntu 9.10 lamp server (oznola) and installed the desktop.

i would like to incorporate it into my wlan at [http://alonzofretwell.com](http://alonzofretwell.com) such that i can use it to develop and test with wordpress.

how can incorporate the new machine into my existing wlan so that i can can access it with [http://oznola.alonzofretwell.com](http://oznola.alonzofretwell.com) (and it will open oznola/var/www/ not bubba/home/web as it does now) is this possible?

right now bubba is the main server that serves [http://alonzofretwell.com](http://alonzofretwell.com) obviously i do not want to interfere with bubbas' normal service on the wlan.

when i open Places->Network i only see bubba and valantino (my vista machine)

i am connected to the wlan using wifi wlan. i can connect to the web just fine ~from~ oznola but i cannot even ssh ~to~ oznola.

from another computer i can see see it by ip address in trace route. but when i run port scan only smtp port 25 is open (on oznola). should other ports be open for this to work?

it can be successfully pinged at its dot-quad ip address.

please advise.

---

